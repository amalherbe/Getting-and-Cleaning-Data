Code Book
========

This is a code book that describes the variables, data, and any transformations or work that you performed to clean up the data.

Raw data collection
-------------------

### Collection

Raw data are obtained from UCI Machine Learning repository: [http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones).

#### Data Set Information

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. 

##### Attribute Information:

For each record in the dataset it is provided:
* Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
* Triaxial Angular velocity from the gyroscope.
* A 561-feature vector with time and frequency domain variables.
* Its activity label.
* An identifier of the subject who carried out the experiment. 

See Readme file into 'UCI HAR Dataset' for more information.


Raw Data transformation
-------------------

The raw data sets are processed with the script run_analysis.R script to create a tidy data set.

__Merge training and test sets__
Test and training data, subject ids and activity ids are merged to obtain a single data set. 
Variables are labelled with the names assigned by original collectors.

__Extract mean and standard deviation variables__
Keep only the values of estimated mean and standard deviation .

__Get descriptive activity names__
A new column is added to intermediate data set with the activity description.

__Get abel variables appropriately__
Labels given from the original collectors were changed to get valid/more descriptive R names 

__Create a tidy data set__
From the intermediate data set is created a final tidy data set where numeric
variables are averaged for each activity and each subject.

Tidy data set
-------------------

### Variables

The tidy data set contains :

* an identifier of the subject who carried out the experiment (__Subject__). Its range is from 1 to 30. 
* an activity label (__Activity__): WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING
* mean of all other variables are measurement collected from the accelerometer and gyroscope 3-axial raw signal (numeric value)

The variable name convention is like the following: 

* __measurement__: the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk).  Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable: gravityMean, tBodyAccMean, tBodyAccJerkMean, tBodyGyroMean,tBodyGyroJerkMean.

* __.mean/std__: mean or standard deviation of the measurement
* __.X/Y/Z__: one direction of a 3-axial signal
* __.mean__: global mean value  

The data set is written to the file 'sensordata_avg_by_subject.txt'.
