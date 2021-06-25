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

![Part2_DataPreparation](https://user-images.githubusercontent.com/55681983/123368708-ec884c00-d599-11eb-9830-3a63f600f692.PNG)


## Data
![Part2_Data](https://user-images.githubusercontent.com/55681983/123368586-b054eb80-d599-11eb-93d2-efbb5f550fbd.PNG)


## Model

![Part2_Model](https://user-images.githubusercontent.com/55681983/123368116-d1690c80-d598-11eb-94b1-7ed2d35c4edd.PNG)




