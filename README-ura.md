
#README file for **run_analysis.R** script

This script computes and produces a Tidy Dataset of Averages for means and standard deviations of measurements obtained in an Experiment for the Samusung Galaxy S II smartphone.
The measurements were collected from 30 volunteers within an age bracket of 19-48 years. 
Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist.

##Input Data
The script reads the following INPUT DATA files obtained from the Experiment.
 	features.txt: List of all features.
 	activity_labels.txt: Links the class labels with their activity name.
 	train/X_train.txt: Training set.
 	train/y_train.txt: Training labels.
 	test/X_test.txt: Test set.
 	test/y_test.txt: Test labels.

##What the Script Does

	Section0.Loads the required R packages using read.table function.
	Section1.Merges the training and the test sets using rbind to create one data set and combine subject and activity id data with measurement data using cbind.
	Section2.Extracts the mean and standard deviation for each measurement using select().
	Section3.Labels the data set with descriptive variable names using names(). *Control Characters were removed from descriptions for easy manipulation*
	Section4.Replaces activity column ids with activity names using factor().
	Section5.Creates a tidy dataset of Averages named result from the data set in step 4, for each activity and subject 
                 group_by() and summarise_each() functions have been used in achieving this result.


##How to read the result dataset

The tidy dataset result has been saved to a text file using the following command and submitted as part of the course project.
write.table(result, file = "result.txt", row.name = FALSE)
It can be read into R using the following: 
data <- read.table(file_path, header = TRUE)

##Code Book
Please find the Code-Book which describes the variables in the results dataset the  under the same Github Repo as this README file.

##Justification for format chosen for tidy dataset

Hadley Wickham's frame work for tidy data supports the idea  "each variable forms a column". 
Based on this principal it was decided to treat the Activity variable as a single column which puts the tidy dataset in a wide format.
According to comments made in the discussion forum for this project, the wide format has been mostly favored in previous groups as well. 
That further corroborates the idea.
Having said that, the final decision as to the most fitting dataset depends greatly on the type of analysis and the semantics of the dataset.
From a presentation perspective the narrow format seems better.  
The reader may easily convert it to the narrow format by simply applying a two step process in one line as follows:

tidy_data1 <- result %>% gather(measurement, average, -(activity:subject)) %>% spread(activity,average)






