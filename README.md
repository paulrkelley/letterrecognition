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
For the decision trees I decided to test both the depth parameter, as well as the split of testing and training data, and found the higher the percentage of training data the more accuracy I could achieve with the decision tree algorithm.  The depth seemed to peak at around 7 layers of decisions.  From this we can see that both a higher percentage of training data, and a relatively low number of decision layers meant a better accuracy, again I think that this is probably due to the measurements, and how closely they were clustered together.  The max accuracy I achieved with the decision tree algorithm was 89 percent.

### Random Forest
With the random forest I decided to test different test training splits, as well as different numbers of principal components.  I once again found that as you increase the percentage of training data, you increase the accuracy of the algorithm.  In terms of the number of principal components I found that the higher the number of components generally the higher the accuracy, however the accuracy increase began to diminish once you get into the 8 principal components range, which demonstrates the law of diminishing returns.  The highest accuracy I was able to achieve with the random forest was 93.7 percent.

### Vector Machine
sklearn includes two versions of the vector machine natively which are the linear vector machine, and the poly vector machine.  I tested both with different rates of success.
#### Linear Vector
For the linear vector machine I tested both the split in training, and testing data, as well as the number of components that it was using.  Initially when I tried to experiment with the split in the training testing data something strange happened. I found that the maximum accuracy was around 50% split.  This did not track logically, and I decided to run the experiment several times with different static states for the training and testing data.  In general I found that the higher the percentage of training data the higher the accuracy, however there were many instances where a lower percentage of training data out performed the higher percentage.  This is something I may explore more in the future, as I am not exactly sure why this occurs.  In terms of the number of components I found that the higher the number of components the better the linear vector machine did which tracks with the other algorithms. The highest accuracy I was able to get with this algorithm was 85 percent.

#### Poly Vector
For the poly vector machine I tested both the split in training, and testing data, as well as the number of components that it was using.  Like many of the other machine learning models I found that as you increase the percentage of data that was used in the training the accuracy went up.  I also found the same with the number of components where as you increase the number of components, the accuracy of the algorithm would increase.  The maximum accuracy I was able to achieve with the poly vector machine was 88.3 percent.

## Conclusion
In conclusion, it seems that the k-nearest neighbors algorithm did the best with this dataset with an accuracy of 95 percent.  I am still not pleased with this accuracy, and if I were to use this in the real world I might write a custom algorithm, or experiment with nueral networks in order to increase this accuracy.  I did however accomplish my goal with this project which was to better understand numpy, matplotlib, and sklearn and their limitations.  I learned a lot about how the machine learning models provided by sklearn work, as well as some of their limitations.  This knowledge will help me in the future if I choose to develop my own machine learning algorithms.

## Next Steps
In terms of next steps I would love to work on some custom machine learning algorithms that take many of the good aspects from sklearns library in that they are easy to use, and universal and try to write my own versions that could be more customizable, and might give better results.  I could also reapproach this dataset with neural networks to see if they might improve the accuracy of the classification.
