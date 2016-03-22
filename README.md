
# CourseraDataCleansingProject

     This repo is for the Coursera Data Cleansing course project. The project is to create two tidy data sets from the  UCI HAR Human Activity Recognition Using Smartphones Dataset. The description of the original data set is as follows:
     The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 
     
     The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. The URL for the data downloaded is 
     https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
     The data used in this project was downloaded on March 15,2016
     
     1) Files included in this repo are:
       A) README.md
       B) CodeBook.md
       C) run_analysis.R
       D) meanandstd.txt
       E) meanandstdbysubjactivity.txt
       
     2) Summary of run_analysis.R script
       A) Read in the following 8 files from the downloaded UCI HAR data set unzipped on 3/15/2016:
          activity_labels.txt,features.txt,X_test.txt,X_train.txt,Y_test.txt,Y_train.txt,subject_test.txt
          subject_train.txt
       B) Create test table by cbinding x_test(with col names from features.txt),subject_test and 
          y_test(with col name of "activityid") . Do the same for the train table using the train files.
       C) Then create combined table by rbinding the test and train tables. Merge the combined table with the 
          table created form the activity_labels.txt file(col names activityid and activity) by activity id. 
          Subset table by dropping out the activityid variable resulting in table with subjectid,activity and 561           measurement variables
       D) Extract the desired mean and std measurement variables from the combined table from c) using the grep            function separately for mean(note:lower case) and std where they both exist for a given measurement              based on variables identified in the features_info.txt file
          Subset the combined table keeping columns 1 and 2(subjectid and activity) and using the column numbers           resulting from the two grep statements
       E) Tidy up the variable names by removing imbedded punctuation marks such as "." and "()" and then convert           all variable names and values of activity variable to lower case so that someone doesn't have to     
          remember when abd where upper case is used
       F) Sort and group by subjectid and activity(meanandstd data table)
       G) Create a second tidy table, per assignment, by using the dplyr summarize_each function to calculate the
          average of the varibales from the meanandstd table by subjectid activity pairs to create the 
          meanandstdbysubjactivity table 
       I) Use write.table to create two tidy txt files from the data tables from F) and G) 
       
     
     
