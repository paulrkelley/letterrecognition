# letterrecognition

## Data Set
for this project I took a look at the letter recognition data set from the UCI datasets. This data set consists of a large number of black-and-white rectangular pixel displays as one of the 26 capital letters in the English alphabet. The character images were based on 20 different fonts and each letter within these 20 fonts was randomly distorted to produce a file of 20,000 unique letters. Measurements of these letters were then taken and then the letters were scaled so they would be integers and fall between 0 and 15.

## Initial Steps
First I downloaded the file data file, and opened it with excel in order to get a general idea as to the format of the data. I noticed that the data set did not contain any labels, and that I would need to figure out what each value meant. Luckily UCI had included a seperate file with the meaning of each data group.  It turned out that these were messurements.

I then imported the data file into Jupiter Notebook, and used pandas to convert the raw data file into a usable format.  This meant that I had a data frame object with 20,000 entries, and 17 variables for each entry the first being the letter and the rest of them were measurements.  I took a look at what the range of values for the 17 variables were and saw that each measurement consisted of integers between 1, and 15.  I took a look at the values for the letter and ensured that all the letters were accounted for.

## Data Transformation
I used the standard scaler from sklearns preprocessing library to scale the data to be more uniform. I decided to standardize the data, as it usually improves the accuracy of the algorithms, and allows for easier comparison between the different letters. I then took a look at the values of each variable, and tried to determine an appropriate number of features to work with, as I thout that 16 was going to be too many. I decided to start with 6 key features, and used the principal component analysis from sklearns decomposition library to create a new dataframe with the 6 features that had the most variance.

## Data Visualization
I used a combination of matplotlib, and seaborn to graph the key components against each other to check on how spread out the dataset was. From these graphs I was able to determine that the data set was still very clustered, but there were a few groupings that stood out. These groupings are a good sign, as they should increase the accuracy of the artificial intelegence algorithms.  Having a better understanding of the dataset, and having standardized it a fair amount I was ready to move into training the algorithms to see how they would perform on this task.

## Training of The Artificial Intelegence Algorithms
Having used sklearn for much of the project already, and wanting to get more familliar with how their machine learning algorithms work I decided to work with their k-nearest neighbors, tree, random forest, and vector machines algorithms. I decided to dedicate 25 percent of the data to testing the algorithms, and the other 75 percent went toward training the algorithms, and used sklearn to do this. I then used the same datasets to do an initial training of each algorithm.

## Testing The Initial Algorithms
I then tested each of the algorithms, and found that the k-nearest neighbors algorithm had performed the best with an accuracy of 94 percent. This is most likely due to how closely packed the data is.  I was less than pleased with this performance, however and decided to try and improve the accuracy. In order to achieve this I tried changing the percentage of data, and found that the higher the percentage of training data the better the algorithms work, which makes sense.

## Optimizing each Algorithm
### K-nearest Neighbor
For the k-nearest neighbor algorithm I decided to test the amount of neighbors that were considered.  I found that the lower the number of neighbors that were considered the better the accuracy became, with the max being with 1 nearest neighbor, however if I was using this in a real world scenario I would most likely use the next highest percentage of 94.4 percent, as I think that judging the letter off of only one other data point could be risky in the long run.  I also experimented with different numbers of components, and found that k-nearest neighbors had the max accuracy of 95 percent.

### Decision Trees


### Random Forest


### Vector Machine
