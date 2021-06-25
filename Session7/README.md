# PART 1
Make a model using datasetSentences.txt without any augmentation.
The dataset must have around 12k examples.

MAX_VOCAB_SIZE = 12_000

Text.build_vocab(train, max_size = MAX_VOCAB_SIZE)
Label.build_vocab(train)

The dataset is split into 70/30 Train and Test (no need of validation)

(train, test) = stanfordDataset.split(split_ratio=[70, 30]

Convert floating-point labels into 5 classes 

![Screenshot](![image](https://user-images.githubusercontent.com/55681983/123360714-67963600-d58b-11eb-8a2c-33e21ba45a35.png))


Share the prediction on samples picked from the test dataset.

![Screenshot](![image](https://user-images.githubusercontent.com/55681983/123361990-99100100-d58d-11eb-96c3-2ffa0c6b977e.png))


# PART 2

To take a Question-Answer dataset and apply Encoder-Decoder-Seq2Seq architecture

## Preparation of Data

![Screenshot](![image](https://user-images.githubusercontent.com/55681983/123367713-0fb1fc00-d598-11eb-885f-6216db556baa.png))

![Screenshot](![image](https://user-images.githubusercontent.com/55681983/123367842-5273d400-d598-11eb-898c-7d53d3c47b0d.png))

## Model

![Screenshot](![image](https://user-images.githubusercontent.com/55681983/123367934-79caa100-d598-11eb-98f7-53d6f32ec1a2.png))




