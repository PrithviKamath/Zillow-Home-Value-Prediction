
<img src="https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Extras/Zillow%20Home%20Value%20Prediction%20logo.PNG"></img><br />
<b>Zillow Home Value Prediction Dataset</b> (https://www.kaggle.com/c/zillow-prize-1/overview)<br />

<b>Summary:</b> <br />
Ever since Zillow released its Home Value Prediction 11 years ago, it was a great hit amongst the first time home buyers. Home being the largest and most expensive purchase a person makes in his lifetime, it ensured homeowners had access to reliable information, free of cost, at the click of a button.<br />

<b>Data Description</b><br />
Below is the description about the files used in this analysis:<br />
• <b>properties_2016.csv</b> - all the properties with their home features for 2016<br />
• <b>train_2016.csv</b> - the training set with transactions from 1/1/2016 to 12/31/2016<br />
• <b>sample_submission.csv</b> - a sample submission file in the correct format<br />
These files have been manually downloaded and placed in a 'Data' folder. <br />

Output files shall be placed in an 'Output' folder. Hence I have started with writing a code to traverse through the file system and create new a folder.<br />
Bokeh library is used to create graphs and plots in a new tab in the browser. These plots are also saved in html formt in the Output folder.<br />

<b>Exploratory Data Analysis</b><br />
Understanding the dataset:
• properties_2016.csv has 2985217 observations with 53 variables for each observation. <br />
• train_2016.csv has 90275 observations with 3 variables for each observation. <br />

We start with plotting a scatter plot to understand the distribution of logerror in the train_2016 dataset.<br />
<img src='https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Extras/Logerror_ScatterPlot.PNG'></img><br />

On plotting this graph I truncated the outliers ie obeservations with logerror >= 2.5 or logerror <= 3 were dropped.
Then I moved onto plotting the month-wise frequency of these observations. This reveiled that there was a significant drop in the number transactions during Novermber and December 2016. Also the data description mentioned that data for November and December 2016 were not complete.Hence we move on to dropping observations that have transactions dates greater than 10/15/2016. <br />
Now we move on to understanding the properties_2016 dataset. Manual overview reviels that there are null values for most of the variables. Hence we start with finding the frequency of null for each variables. The first 10 variables with their null count is as follows: <br/>
<img src='https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Extras/Top10NullValues.PNG'></img><br />
Since the count seems to be quite large we move on to counting the percentage of null values for each variable. The first 10 variables with their respective null percentage is as follows: <br />
<img src='https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Extras/Top10NullPercentage.PNG'></img><br />
Since there are 53 variables, it difficult to get a overall view. Hence we move on to plotting a bar graph.
<img src='https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Extras/Variable_Vs_NullPercentage.PNG'></img><br />
We move on to dropping variables with null percentage greater than 60%.
Next we merge the cleaned properties_2016 and train_2016 datasets to get a total of 85652 observations with 31 variables for each. <br />
Out of these 31 variables, data description mentions that 'structuretaxvaluedollarcnt' reviels 'The assessed value of the built structure on the parcel.' A simple describe functions gives the below details regarding the variable.
<img src='https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Extras/structuretaxvaluedollarcnt_merged_data.PNG'></img><br />
Seeing the difference in the minimum, mean and maximum values for this variable we plot a skewness graph to get a get the distribution.
<img src='https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Output/Skewness.png'></img><br />
We also observe that the obserevations have latitude and longitudes. The data description mentions that the observations are for Los Angeles, Orange and Ventura, California counties. We plot a map to verify the same.
<img src='https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Output/ObservationsMap.png'></img><br />
Finally we save this dataset in the Data folder to further use it as an input to implement machine learning algorithms.

<b>Data Pre-processing</b>
We start with importing the above created merged_data, properties_2016 dataset and the sample_submission dataset.
Next we move to clear a bad record in the merged_data by dropping the first column. Then we take variables with numerical values and ignore the variables with strings as string values cannot be used in this machine learning model. Finally we replace the empty values with '-1'.

<b>Implementing Machine Learning Alsorithms</b>
• The firt step in implementing machine learning algorithms is to <b>Create a training dataset</b>
I have done that by including all variables except parcelid and logerror from the merged_data dataset. Sample output ie logerror in the form of a series of values form the train_y dataset.

• Next step is to <b>Create a testing dataset</b>
I am using the sample_submission dataset to create a test dataset. test_x dataset contains variables similar to train_x.

We then implement Random Forest Regressor for 5,10 and 15 variables and check the prediction of log error. Top 1000 rows of the output is saved in .csv file named LogErrorPrediction with a time stamp. Only top 1000 rows is considered duw to space contraints. Top 15 parcelid with their predicted logerror is as follows:
<img src='https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Extras/Output.PNG'></img>

<b>References</b> <br />
https://www.kaggle.com/c/zillow-prize-1 <br />
https://www.kaggle.com/arjanso/simple-starter-randomforest-regressor
