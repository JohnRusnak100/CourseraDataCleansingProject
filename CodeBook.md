

# This CodeBook is for the Coursera Data Cleansing Course final project

   The CodeBook will document the structure of the original data UCI HAR data set( URL in README.md),transformations performed on the data, creation,subsetting and grouping of the data to generate the two(2) required tidt data sets for the course project.
   
## Section:Code Book   
   
        1) Original UCI HAR data set contained the following files and file information:
   
   'README.txt'   

   'features_info.txt': Shows information about the variables used on the feature vector.

   'features.txt': List of all features.

   'activity_labels.txt': Links the class labels with their activity name.

   'train/X_train.txt': Training set.

   'train/y_train.txt': Training labels.

   'test/X_test.txt': Test set.

   'test/y_test.txt': Test labels.

The following files are available for the train and test data. Their descriptions are equivalent. 

   'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30. 

   'train/Inertial Signals/total_acc_x_train.txt': The acceleration signal from the smartphone accelerometer X axis in standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis. 

   'train/Inertial Signals/body_acc_x_train.txt': The body acceleration signal obtained by subtracting the gravity from the total acceleration. 

   'train/Inertial Signals/body_gyro_x_train.txt': The angular velocity vector measured by the gyroscope for each window sample. The units are radians/second. 

 Notes: 
- Features are normalized and bounded within [-1,1].
- Each feature vector is a row on the text file.

For more information about this dataset contact: activityrecognition@smartlab.ws

       2) The project used the folowing eight(8) files:
         A) 'features.txt' = file with the 561 variable names. This file was used to set the colnames names 
            for the test and train data tables. 
            For example measurement variable # 1 has name="tBodyAcc-mean()-X" not very tidy
         B) 'activity_labels.txt' used to link activityid number with activity
             for example activtyid=1 equals "walking"
         C) 'subject_train.txt' identifies the subject who performed the activity for each 7352 row sample
         D) 'X_train.txt' the training data set file with 7352 obs of the 561 measuremnents identified in A)
         E) 'y_train.txt' the file with the activity id's for the 7352 obs in D)
         F) Corresponding 'subject_test.txt','X_test.txt' and 'Y_test.txt' to create the test table with 2947 obs
       
      3)  The following recaps the varaible name and value transformations
        A) transformed the activity variable values to make potential subsetting on this variable easier:
        
           Original values:         tidy data set :
           -------------------     -------------------
            WALKING                  walking
            WALKING_UPSTAIRS         walkingupstairs
            WALKING_DOWNSTAIRS       walkingdownstairs
            SITTING                  sitting
            STANDING                 standing
            LAYING                   laying
            
         B) Changes to mean and std variable names as follows
            a) 	“-“ and “( )” were removed using gsub("[[:punct:]]","",colnames(dffinal))
            b) All characters were changed to lower case using       tolower(varf[1:68])
            c) Following complete descriptive changes were made using gsub:
            
                 acc changed to accelerator      Not familar with abbreviation usage I changed to complete
                 gyro changed to gyroscope       descriptive names so anyone would be able to understand
                 mag changed to magnitude
                 bodybody changed to body        looks like misnamed based on features_info.txt

             d) In the original UCI HAR data set – the original measurement variables were the values 
                for a single subject and activity observation from the X_test.txt and X_train.txt files. 
                There were 10299 such observations.
             e) For the meanandstdbysubjactivity data set the values for all of these variables 
                is the average of the values from meanandstd data set calculated for 
                each subjectid(30) and activity(6) pair resulting in 180 rows of data.
                 
                          Recap of measurement variable name and value transformations
                               meanandstd data set                 meanandstdbysubjactivity data set
                            ---------------------------           ------------------------------------
      measurement names       transformed as shown below             transformed as shown below

      measurement values      same as original                       average(of original values)

      unit of measurements    same as original                       same as original             

      comments                same as original but now               tidy and values are the average 
                              tidy and sorted by subjectid           of the original values for each
                              and activity                           subjectid/activity pair

              
                              Recap of variable name changes:
         
                 Original UCI HAR names       	Revised tidy data sets names
                -----------------------         ------- -------------------
                tBodyAcc-mean()-X        	        tbodyacceleratormeanx
                tBodyAcc-mean()-Y	                tbodyacceleratormeany
                tBodyAcc-mean()-Z                   tbodyacceleratormeanz
                tGravityAcc-mean()-X    	        tgravityacceleratormeanx
                tGravityAcc-mean()-Y    	        tgravityacceleratormeany
                tGravityAcc-mean()-Z    	        tgravityacceleratormeanz
                tBodyAccJerk-mean()-X   	        tbodyacceleratorjerkmeanx
                tBodyAccJerk-mean()-Y   	        tbodyacceleratorjerkmeany
                tBodyAccJerk-mean()-Z   	        tbodyacceleratorjerkmeanz
                tBodyGyro-mean()-X      	        tbodygyroscopemeanx
                tBodyGyro-mean()-Y      	        tbodygyroscopemeany
                tBodyGyro-mean()-Z      	        tbodygyroscopemeanz
                tBodyGyroJerk-mean ()-X   	        tbodygyroscopejerkmeanx
                tBodyGyroJerk-mean()-Y   	        tbodygyroscopejerkmeany
                tBodyGyroJerk-mean()-Z  	        tbodygyroscopejerkmeanz
                tBodyAccMag-mean()      	        tbodyacceleratormagnitudemean
                tGravityAccMag-mean()    	        tgravityacceleratormagnitudemean
                tBodyAccJerkMag-mean()  	        tbodyacceleratorjerkmagnitudemean
                tBodyGyroMag-mean()     	        tbodygyroscopemagnitudemean
                tBodyGyroJerkMag-mean() 	        tbodygyroscopejerkmagnitudemean
                fBodyAcc-mean()-X       	        tbodyacceleratormeanx
                fBodyAcc-mean()-Y       	        tbodyacceleratormeany
                fBodyAcc-mean()-Z       	        tbodyacceleratormeanz
                fBodyAccJerk-mean()-X   	        fbodyacceleratorjerkmeanx
                fBodyAccJerk-mean()-Y   	        fbodyacceleratorjerkmeany
                fBodyAccJerk-mean()-Z   	        fbodyacceleratorjerkmeanz
                fBodyGyro-mean()-X      	        fbodygyroscopemeanx
                fBodyGyro-mean()-Y      	        fbodygyroscopemeany
                fBodyGyro-mean()-Z      	        fbodygyroscopemeanz
                fBodyAccMag-mean()      	        fbodyacceleratormagnitudemean
                fBodyBodyAccJerkMag-mean()	        fbodyacceleratorjerkmagnitudemean
                fBodyBodyGyroMag-mean() 	        fbodygyroscopemagnitudemean
                fBodyBodyGyroJerkMag-mean()	        fbodygyroscopejerkmagnitudemean
                tBodyAcc-std()-X	                tbodyacceleratorstdx
                tBodyAcc-std()-Y	                tbodyacceleratorstdy	
                tBodyAcc-std()-Z	                tbodyacceleratorstdz	
                tGravityAcc-std()-X	                tgravityacceleratorstdx	
                tGravityAcc-std()-Y	                tgravityacceleratorstdy	
                tGravityAcc-std()-Z	                tgravityacceleratorstdz	
                tBodyAccJerk-std()-X	            tbodyacceleratorjerkstdx	
                tBodyAccJerk-std()-Y	            tbodyacceleratorjerkstdy	
                tBodyAccJerk-std()-Z	            tbodyacceleratorjerkstdz	
                tBodyGyro-std()-X	                tbodygyroscopestdx	
                tBodyGyro-std()-Y	                tbodygyroscopestdy	
                tBodyGyro-std()-Z	                tbodygyroscopestdz	
                tBodyGyroJerk-std()-X	            tbodygyroscopejerkstdx	
                tBodyGyroJerk-std()-Y	            tbodygyroscopejerkstdy	
                tBodyGyroJerk-std()-Z	            tbodygyroscopejerkstdz	
                tBodyAccMag-std()	                tbodyacceleratormagnitudestd	
                tGravityAccMag-std()	            tgravityacceleratormagnitudestd	
                tBodyAccJerkMag-std()	            tbodyacceleratorjerkmagnitudestd	
                tBodyGyroMag-std()	                tbodygyroscopemagnitudestd	
                tBodyGyroJerkMag-std()	            tbodygyroscopejerkmagnitudestd	
                fBodyAcc-std()-X	                fbodyacceleratorstdx	
                fBodyAcc-std()-Y	                fbodyacceleratorstdy	
                fBodyAcc-std()-Z	                fbodyacceleratorstdz	
                fBodyAccJerk-std()-X	            fbodyacceleratorjerkstdx	
                fBodyAccJerk-std()-Y	            fbodyacceleratorjerkstdy	
                fBodyAccJerk-std()-Z	            fbodyacceleratorjerkstdz	
                fBodyGyro-std()-X	                fbodygyroscopestdx	
                fBodyGyro-std()-Y	                fbodygyroscopestdy	
                fBodyGyro-std()-Z	                fbodygyroscopestdz	
                fBodyAccMag-std()	                fbodyacceleratormagnitudestd	
                fBodyBodyAccJerkMag-std()	        fbodyacceleratorjerkmagnitudestd	
                fBodyBodyGyroMag-std()	            fbodygyroscopemagnitudestd	
                fBodyBodyGyroJerkMag-std()	        fbodygyroscopejerkmagnitudestd	
            
## Section:Instuction List      
      
     An R script called run_analysis.R is included in repo that does the following per project requirements:

      1) Merges the training and the test sets to create one data set.
      2) Extracts only the measurements on the mean and standard deviation for each measurement.
      3) Uses descriptive activity names to name the activities in the data set
      4) Appropriately labels the data set with descriptive variable names.
      5) From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject. 
         Note the 2 tidy data set are named meanandstd and meanandstdbysubjactivity
      
                         run_analysis script details with sample output as follows:
     
       A) Read in the following 8 files from the downloaded UCI HAR data set unzipped on 3/15/2016:
          activity_labels.txt,features.txt,X_test.txt,X_train.txt,Y_test.txt,Y_train.txt,subject_test.txt
          subject_train.txt
          
       B) Create test table by cbinding x_test(with col names from features.txt),subject_test and 
          y_test(with col name of "activityid") . Do the same for the train table using the train files.
          
          Resulting test table as follows(Note activity values based on activityid  will be added in step C) :
          
                                             head(test)
            subjectid activityid tBodyAcc-mean()-X tBodyAcc-mean()-Y tBodyAcc-mean()-Z tBodyAcc-std()-X 
          1         2          5         0.2571778       -0.02328523       -0.01465376       -0.9384040      
          2         2          5         0.2860267       -0.01316336       -0.11908252       -0.9754147     
          3         2          5         0.2754848       -0.02605042       -0.11815167       -0.9938190     
          4         2          5         0.2702982       -0.03261387       -0.11752018       -0.9947428    
          5         2          5         0.2748330       -0.02784779       -0.12952716       -0.9938525     
          6         2          5         0.2792199       -0.01862040       -0.11390197       -0.9944552     
          
          
       C) Then create combined table by rbinding the test and train tables. Merge the combined table with the 
          table created form the activity_labels.txt file(col names activityid and activity) by activity id. 
          Subset table by dropping out the activityid variable resulting in table with subjectid,activity and 561
          measurement variables
          Resulting table from rbinding test and traing tables,adding activityid and transforming variables  
          names(since I'm not familar with data in this field, I added more descriptive names so that I could
          better understand variables) 
       D) Extract the desired mean and std measurement variables from the combined table from c) using the grep  
          function separately for mean(note:lower case) and std where they both exist for a given measurement based
          on variables identified in the features_info.txt file 
          Subset the combined table keeping columns 1 and 2(subjectid and activity) and using the column 
          number resulting from the two grep statements.
       E) Tidy up the variable names by removing imbedded punctuation marks such as "." and "()" and then convert 
          all variable names and values of activity variable to lower case so that someone doesn't have to     
          remember when abd where upper case is used
          After steps C), D), and E) table is as follows and is tidy
          
                                                     head(dffinal)
            subjectid activity tbodyacceleratormeanx tbodyacceleratormeany tbodyacceleratormeanz 
          1         7  walking             0.2693013           0.007891765           -0.05068156            
          2        21  walking             0.2623422          -0.016215306           -0.11446522            
          3         7  walking             0.2383207           0.002102952           -0.04988110        
          4         7  walking             0.2447143          -0.031546655           -0.18135387              
          5        18  walking             0.2490386          -0.021118537           -0.12493361            
          6         7  walking             0.2046162          -0.067271336           -0.14010421              
          
       F) Sort and group by subjectid and activity(meanandstd data table)
       G) Create a second tidy table, per assignment, by using the dplyr summarize_each function to calculate the
          average of the varibales from the meanandstd table by subjectid activity pairs to create the 
          meanandstdbysubjactivity table   Resulting tidy table as follows:
          
                                           head(meanandstdbysubjactivity)
           subjectid          activity tbodyacceleratormeanx tbodyacceleratormeany tbodyacceleratormeanz
         1         1            laying             0.2215982          -0.040513953            -0.1132036
         2         1           sitting             0.2612376          -0.001308288            -0.1045442
         3         1          standing             0.2789176          -0.016137590            -0.1106018
         4         1           walking             0.2773308          -0.017383819            -0.1111481
         5         1 walkingdownstairs             0.2891883          -0.009918505            -0.1075662
         6         1   walkingupstairs             0.2554617          -0.023953149            -0.0973020

                                          tail(meanandstdbysubjactivity)
             subjectid          activity tbodyacceleratormeanx tbodyacceleratormeany tbodyacceleratormeanz
         175        30            laying             0.2810339          -0.019449410           -0.10365815
         176        30           sitting             0.2683361          -0.008047313           -0.09951545
         177        30          standing             0.2771127          -0.017016389           -0.10875621
         178        30           walking             0.2764068          -0.017588039           -0.09862471
         179        30 walkingdownstairs             0.2831906          -0.017438390           -0.09997814
         180        30   walkingupstairs             0.2714156          -0.025331170           -0.12469749
          
          
       I) Use write.table to create  tidy txt files from the data tables from F) and G) 

