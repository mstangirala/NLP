Using twitter dataset make a model in such a way that:

encoder: an RNN/LSTM layer takes the words in a sentence one by one and finally converts them into a single vector. VERY IMPORTANT TO MAKE THIS SINGLE VECTOR
this single vector is then sent to another RNN/LSTM that also takes the last prediction as its second input. Then we take the final vector from this Cell
and send this final vector to a Linear Layer and make the final prediction. 
This is how it will look:
embedding
word from a sentence +last hidden vector -> encoder -> single vector
single vector + last hidden vector -> decoder -> single vector
single vector -> FC layer -> Prediction


Once the model is trained, take one sentence, "print the outputs" of the encoder for each step and "print the outputs" for each step of the decoder. 

classify_tweet("In his teen years, Obama has been known to use marijuana and cocaine.")

tensor([[ 0.0254, -0.0193,  0.0237,  ..., -0.0255,  0.0302, -0.0085],
        [ 0.0641, -0.0277,  0.0369,  ..., -0.0404,  0.0435, -0.0356],
        [ 0.0846, -0.0577,  0.0532,  ..., -0.0443,  0.0568, -0.0767],
        ...,
        [ 0.7117, -0.2543,  0.2367,  ..., -0.2563, -0.5162, -0.5741],
        [ 0.7325, -0.2912,  0.2825,  ..., -0.2620, -0.4735, -0.6101],
        [ 0.7568, -0.2465,  0.2184,  ..., -0.2062, -0.6078, -0.5346]],
       grad_fn=<CatBackward>)
tensor([[[ 7.5683e-01, -2.4652e-01,  2.1839e-01, -4.5864e-03,  4.2375e-01,
          -7.0269e-01, -5.2529e-01, -5.4349e-01, -7.9138e-01, -2.8312e-01,
          -4.8821e-01,  2.0136e-01,  1.6348e-01, -5.5715e-01,  3.3043e-01,
           1.8674e-01, -3.5247e-01,  6.4125e-01, -3.9552e-01, -4.5429e-01,
           5.9270e-01, -4.9525e-01, -1.8933e-01,  3.2923e-02, -3.9937e-01,
           2.8264e-01,  5.2573e-01,  1.2298e-01, -3.4291e-01,  2.1482e-01,
           2.3002e-02, -4.6391e-02, -2.8750e-01,  6.0622e-01, -1.5868e-01,
          -7.8684e-02, -4.3261e-01, -7.1311e-01,  1.8294e-01, -2.4872e-01,
           2.5715e-01,  5.7747e-01, -6.8293e-01,  6.3656e-01,  2.0560e-01,
          -4.7644e-01,  7.6413e-01, -3.4048e-01,  7.3545e-01,  5.7548e-01,
           3.2608e-01,  7.6504e-01, -1.6841e-01, -3.6340e-02, -1.5213e-01,
          -1.4144e-01,  8.6755e-01,  6.0907e-01,  1.3384e-01,  3.8838e-03,
           1.7646e-01,  7.5700e-01,  6.9512e-02,  2.1048e-02,  5.4589e-01,
           3.8504e-01, -6.1855e-01,  2.6822e-01, -2.4877e-01, -1.7781e-01,
           5.1973e-01, -4.9805e-01,  1.7957e-02,  4.6951e-01, -5.1748e-01,
           3.7728e-01, -5.4854e-01, -6.0237e-01,  4.3407e-01, -6.4828e-02,
           1.8965e-01, -5.4864e-01, -2.7633e-01, -2.7057e-01, -5.7071e-01,
           5.2363e-01, -6.6355e-01, -5.6422e-01,  5.9450e-01, -5.6800e-01,
          -6.4769e-01, -3.8024e-01, -3.3315e-01, -3.1677e-01, -8.5817e-01,
          -5.1952e-01, -6.8866e-01, -2.3359e-01, -3.3087e-01,  5.9904e-01,
           2.9488e-01,  4.4646e-01, -5.6673e-01,  3.1685e-01, -3.8813e-01,
           6.8674e-01,  1.2841e-01, -3.5910e-01, -2.1532e-01, -2.2279e-02,
           7.4006e-01, -2.9216e-01,  5.8266e-01, -4.3955e-01, -6.4610e-01,
          -7.5952e-01,  3.9197e-01, -1.6648e-01,  5.0394e-01, -7.1547e-01,
           5.0632e-01, -5.2438e-01, -2.7962e-01, -2.5757e-01,  6.0547e-02,
           4.2100e-01,  5.1754e-01, -6.7251e-01, -3.7307e-01,  8.0316e-01,
          -2.4985e-01, -4.3861e-01,  2.1083e-01, -4.7771e-01,  3.4741e-01,
          -4.6844e-01, -2.1712e-01, -2.9851e-01, -7.3527e-01, -5.9290e-01,
           2.8797e-01, -7.3011e-01,  3.4214e-01, -2.6876e-01,  6.7295e-01,
           4.5463e-01, -4.2313e-01, -1.8173e-01, -1.0440e-01, -6.2463e-01,
          -3.0468e-01,  4.3385e-01, -8.4833e-02,  2.6146e-01,  8.2672e-01,
          -4.9512e-01,  2.1044e-01, -4.6498e-01, -3.2756e-01, -6.9567e-01,
          -3.2837e-01, -2.9679e-01, -7.9920e-01, -8.2892e-01, -6.2518e-01,
           7.6288e-01,  2.7303e-01,  3.9516e-02,  4.8361e-01,  5.6706e-01,
           6.4303e-01,  5.6129e-01, -6.4483e-01,  5.0754e-01, -9.9998e-02,
          -2.7634e-01, -5.8511e-01,  6.9135e-01,  2.4319e-01,  6.9782e-01,
          -2.0190e-01,  5.4104e-01,  3.7583e-01, -4.5922e-01, -1.8792e-01,
           5.2470e-01, -2.2043e-01, -2.2028e-01, -3.1168e-01,  7.6767e-02,
          -6.4789e-02,  8.3835e-01,  2.8809e-01, -4.3914e-01, -1.4679e-01,
           1.0064e-01,  2.1384e-01,  4.5196e-01, -3.3169e-01, -6.5209e-01,
           1.1366e-01, -3.9464e-01,  5.4823e-01,  1.7415e-01,  7.9345e-01,
          -1.3886e-01,  6.3661e-02, -4.5201e-01,  6.7339e-01,  5.3730e-01,
          -1.5028e-01,  4.1601e-01,  2.6038e-01,  2.3233e-01, -5.3961e-01,
           8.7467e-01, -2.7439e-01, -3.8193e-01, -3.2518e-01,  1.5417e-01,
           1.7819e-01,  2.2394e-01,  3.3051e-01, -5.1130e-01,  1.2519e-01,
          -5.4656e-01,  2.8393e-01,  2.4968e-01, -6.6084e-01,  4.8767e-01,
           3.6033e-01,  3.7748e-01, -4.2247e-01, -2.4927e-01, -3.1719e-01,
           1.6617e-01, -7.0511e-01,  5.5693e-01, -8.4331e-02,  6.9773e-01,
          -4.4018e-01,  2.0049e-01,  3.3734e-01,  5.3198e-01,  2.5725e-01,
          -5.1703e-01,  8.1541e-03, -3.7894e-01,  4.3435e-01, -8.4218e-01,
          -6.0648e-01,  5.4380e-01, -7.7245e-01, -8.5015e-02, -5.7265e-01,
          -7.1604e-01, -2.6400e-01, -2.8485e-01, -3.1867e-01,  4.3277e-01,
          -3.4522e-01,  1.5725e-01,  6.7917e-01, -4.8707e-01,  2.0539e-01,
           8.2808e-01, -3.3877e-01, -4.9297e-01, -3.8983e-01, -6.4931e-01,
           8.3175e-01,  2.4464e-01, -4.8662e-01,  7.9704e-01, -6.4012e-01,
          -6.7995e-01, -5.8416e-02, -2.9442e-01,  2.7825e-01,  2.8592e-01,
          -3.6666e-01,  3.1482e-02,  9.8253e-02, -1.3849e-01,  3.5936e-01,
          -4.5719e-01,  7.9583e-01,  7.6902e-01, -6.5600e-01, -5.5056e-01,
          -3.0565e-01, -6.3589e-01, -7.3184e-01, -4.0673e-02,  1.4543e-01,
           7.3381e-01, -7.3708e-01,  5.7394e-01,  7.2316e-01,  5.2749e-01,
          -8.2931e-02,  4.4301e-01,  2.2232e-01, -2.3419e-02, -4.5096e-01,
           2.3537e-01, -2.9275e-01,  4.9104e-01, -5.2245e-01,  5.6895e-01,
          -1.7203e-01, -7.4774e-01, -5.3570e-01, -1.1805e-01, -6.1097e-01,
          -6.0420e-01,  3.7891e-01,  9.1105e-02,  5.1401e-01,  2.9352e-01,
          -5.1236e-02,  4.5601e-01, -5.1044e-02, -4.8988e-01, -3.5908e-01,
          -1.6405e-01, -4.1916e-01, -5.7661e-02,  1.5071e-01, -3.0527e-01,
           1.9827e-01, -1.9742e-01, -2.5501e-01, -3.3756e-01,  3.0634e-01,
           4.3657e-01, -5.0885e-02,  3.4999e-01,  2.8914e-01,  1.5040e-01,
           5.4362e-01,  3.1520e-01, -6.1672e-01, -3.9333e-01, -7.1070e-01,
           8.4325e-01, -2.6434e-03, -7.8397e-01, -2.6997e-02,  4.6974e-01,
           2.6668e-01,  1.7580e-01, -6.2417e-01,  2.3493e-01,  5.1350e-01,
           9.6537e-03,  1.4267e-02, -3.1734e-01,  7.5541e-01,  7.8800e-02,
           6.7500e-01, -8.1170e-01,  4.3690e-01, -3.3304e-01, -2.1799e-01,
          -7.8328e-01,  1.1055e-01, -8.0528e-01,  5.6694e-01,  2.7410e-01,
          -3.9841e-01,  7.9560e-02, -1.5728e-01,  5.9620e-01, -5.5755e-01,
          -6.2983e-01, -4.3885e-01,  8.0134e-01,  2.3423e-02,  2.1852e-01,
           5.9407e-01,  2.2327e-01, -3.3660e-01,  5.4329e-01, -2.2905e-01,
          -4.8972e-01, -1.4474e-01, -7.3959e-01, -1.1219e-01,  1.8883e-01,
           4.4161e-01, -6.1064e-01,  5.6781e-01,  4.5160e-01,  6.3141e-01,
          -3.0679e-02,  6.2379e-01, -3.8218e-01, -3.9639e-01,  3.2878e-02,
           3.8277e-02, -4.5754e-01,  6.8670e-01, -5.1379e-01,  2.6939e-01,
          -3.8812e-01,  4.9132e-01,  4.8399e-01, -1.9208e-01,  4.4911e-01,
           2.2681e-01,  6.1317e-01,  2.2529e-01,  3.4047e-01,  4.9277e-01,
          -4.5541e-01,  2.8729e-01,  2.7725e-01,  3.1999e-01,  3.1287e-01,
           8.0970e-01, -4.5475e-01, -6.4105e-01, -5.3254e-01, -5.3173e-01,
           1.9724e-01,  5.2390e-03, -8.0599e-01,  6.1740e-01,  3.4596e-01,
          -5.6226e-01,  2.3818e-01,  3.7857e-01, -5.2005e-01, -5.0339e-01,
          -3.0361e-01, -7.0118e-01, -1.0992e-01, -7.0530e-01, -5.9050e-01,
          -3.8119e-01,  2.8172e-01,  1.1636e-01, -3.7424e-01,  1.9860e-02,
           3.6469e-02,  4.2340e-01, -4.9704e-01,  3.9667e-01, -2.6676e-01,
          -4.1735e-01, -2.6107e-01,  1.2073e-01,  2.9727e-01, -4.0095e-01,
           4.8480e-01, -6.2490e-01,  6.1200e-01,  4.7096e-01, -2.9532e-01,
          -4.6294e-01,  3.1495e-01, -3.4347e-01,  3.9190e-01,  4.9582e-01,
           5.1186e-01,  9.3737e-01,  6.6376e-01, -2.1439e-04, -2.3088e-01,
          -6.7817e-01,  1.7252e-01,  4.4619e-01, -7.0667e-01, -4.1589e-01,
          -5.2532e-01,  4.4134e-01, -3.2918e-01,  2.1946e-01,  2.9460e-01,
           3.4120e-01,  7.3833e-01,  6.5658e-01, -1.2858e-01,  6.2160e-01,
          -5.0767e-01,  7.4531e-01,  2.7222e-01,  1.5641e-01,  3.3685e-01,
          -3.7229e-01,  1.0930e-01,  6.8611e-02,  4.6633e-01,  4.0528e-02,
          -4.6502e-01,  3.8595e-01, -4.2191e-01, -6.4652e-01, -4.4694e-02,
           1.1227e-01, -6.2898e-01, -1.3011e-01, -1.3043e-01,  7.1292e-01,
           3.0044e-01,  6.5745e-01,  5.4204e-01,  4.3219e-03, -2.0622e-01,
          -6.0778e-01, -5.3462e-01]]], grad_fn=<StackBackward>)
"Negative"
