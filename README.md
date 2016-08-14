Instructions

Clone this repository and run the run_analysis.R script from within the cloned repository root directory.

This script will download and process the data set generating a tidy data set at TidyDataSet.txt

Data Source

This project uses the "Human Activity Recognition Using Smartphones Dataset" downloaded to ./data/Dataset.zip by run_analysis.R from: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

Script Walkthrough

The run_analysis.R script will perform the following steps:  
  
Require dplyr library (for group_by and summarize functions)  
Reads in subject, activity, and data datasets, for both train and test  
Renames columns of each dataset  
Sets activity names on the class labels  
Combines the 3 train datasets together and the 3 test datasets together  
Combines the full train and full test datasets together  
Extracts measurements on mean & standard deviation, for each measurement  
Creates a second, independent, tidy data set which contains the average of each variable for each activity and subject  
Saves the resulting tidy data set to file TidyDataSet.txt  
