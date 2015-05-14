===========================================================================
#README file for **run_analysis.R** script

The script prduces a Tidy Dataset named "result" of measurement Averages obtained from Samsung Galaxy S II Experiment Data from the link below.
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

===========================================================================

===========================================================================

##The script reads the following INPUT DATA files 
 	features.txt: List of all features.
 	activity_labels.txt: Links the class labels with their activity name.
 	train/X_train.txt: Training set.
 	train/y_train.txt: Training labels.
 	test/X_test.txt: Test set.
 	test/y_test.txt: Test labels.
=========================================================================

=========================================================================
##The script does the following:

	Section0.Loads the required R packages using read.table function.
	Section1.Merges the training and the test sets using rbind to create one data set and combine subject and activity id data with measurement data using cbind.
	Section2.Extracts the measurements on the mean and standard deviation for each measurement using select().
	Section3.Labels the data set with descriptive variable names using names(). *Control Characters were removed from names for easy manipulation*
	Section4.Replaces activity column ids with activity names using factor().
	Section5.From the data set in step 4, creates a second, independent tidy data set with the average of each measurement for each activity and each subject 
                 group_by() and summarise_each() functions have been used in achieving this result.
============================================================================

============================================================================
##How to read the result file

The tidy dataset has been saved to a text file using the following command and submitted as part of the course project.
write.table(result, file = "result.txt", row.name = FALSE)
It can be read into R using the following 
data <- read.table(file_path, header = TRUE)

==========================================================================

========================================================================== 
##Code Book
Please find the Code-Book which describes the variables in the results dataset the  under the same Github Repo as this README file.

==========================================================================

==========================================================================
##Justification for format chosen for tidy dataset

Based on the principle of "each variable forms a column" in Hadley Wickham's frame work for tidy data, it was decided to treat activity variable  as single column which results in the wide format as the tidy dataset. The fact that according to discussion forum comments forthis course, the wide format has been favored in previous groups further corroborates this idea.

Having said that, I do agree that the final decision as to the most fitting dataset depends greatly on the type of analysis intended and the semantics (meaning) of the dataset and from a presentation perspective the narrow format seems better.  In that context, if it is needed, we can easily convert it to the narrow format by simply applying a two step process in one line as follows:

**tidy_data1 <- current_result %>% gather(measurement, average, -(activity:subject)) %>% spread(activity,average)**
=============================================================================

=============================================================================



