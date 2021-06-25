# PART 1
Make a model using datasetSentences.txt without any augmentation.
The dataset must have around 12k examples.

MAX_VOCAB_SIZE = 12_000

Text.build_vocab(train, max_size = MAX_VOCAB_SIZE)
Label.build_vocab(train)

The dataset is split into 70/30 Train and Test (no need of validation)

(train, test) = stanfordDataset.split(split_ratio=[70, 30], random_state = random.seed(SEED))

Convert floating-point labels into 5 classes 

![Screenshot](![image](https://user-images.githubusercontent.com/55681983/123360714-67963600-d58b-11eb-8a2c-33e21ba45a35.png))

Share the prediction on 10 samples picked from the test dataset. (100 pts)


# PART 2

Train model we wrote in the class on the following two datasets taken from this link (Links to an external site.): 
http://www.cs.cmu.edu/~ark/QA-data/ (Links to an external site.)
https://quoradata.quora.com/First-Quora-Dataset-Release-Question-Pairs (Links to an external site.)
Once done, please upload the file to GitHub and proceed to answer these questions in the S7 - Assignment Solutions, where these questions are asked:
Share the link to your GitHub repo (100 pts for code quality/file structure/model accuracy) (100 pts)
Share the link to your readme file (100 points for proper readme file), this file can be the second part of your Part 1 Readme (basically you can have only 1 Readme, describing both assignments if you want) (100 pts)
Copy-paste the code related to your dataset preparation for both datasets.  (100 pts)
