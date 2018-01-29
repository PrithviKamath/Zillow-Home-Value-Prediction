
<img src="https://github.com/PrithviKamath/Zillow-Home-Value-Prediction/blob/master/Extras/Zillow%20Home%20Value%20Prediction%20logo.PNG"></img>
<b>Zillow Home Value Prediction Dataset</b><br />
https://www.kaggle.com/c/zillow-prize-1/overview
</br>
<b>Summary:</b> <br />
Ever since Zillow released its Home Value Prediction 11 years ago, it was a great hit amongst the first time home buyers. Home being the largest and most expensive purchase a person makes in his lifetime, it ensured homeowners had access to reliable information, free of cost, at the click of a button.<br />

<b>Data Description</b><br />
Below is the description about the files used in this analysis:<br />
• <b>properties_2016.csv</b> - all the properties with their home features for 2016<br />
• <b>train_2016.csv</b> - the training set with transactions from 1/1/2016 to 12/31/2016<br />
• <b>sample_submission.csv</b> - a sample submission file in the correct format<br />
These files have been manually downloaded and placed in a 'Data' folder. <br />

Output files shall be placed in an 'Output' folder. Hence I have started with writing a code to traverse through the file system and create new a folder.<br />

<b>Exploratory Data Analysis</b><br />
I have started with plotting a scatter plot to understand the distribution of the data points in the train_2016 dataset.<br />
Bokeh library is used to create graphs and plots and they are saved in html format in the Output folder.
On plotting this graph I truncated the outliers ie obeservations with logerror >= 2.5 or logerror <= 3 were dropped.
Then I moved onto plotting the month-wise frequency of these observations. This reveiled that there was a significant drop in the number transactions during Novermber and December 2016. Also the data description mentioned that data for November and December 2016 were not complete.


<b>References</b> <br />
https://www.kaggle.com/c/zillow-prize-1
https://www.kaggle.com/arjanso/simple-starter-randomforest-regressor
