# Cleaning-Data-Project Steps

Please Note: make sure that the 'UCI HAR Dataset' dataset provided as part of the project is unzipped in your working directory folder.<br />
##**Please install dplyr package by using command install.packages("dplyr")**<br />
After this has been done, please run the Run_Analysis.R file in the R-Studio with command source("*path*\Run_Analysis.R"); where *path* denotes the path where Run_Analysis.R file has been placed by you.<br />

##How the code works.

*Step1: Get the current working directory and set this in 'directory' variable.<br />
*Step2: Create variables directory1,directory2,directory3,directory4,directory5,directory6,directory7,directory8 and assign the paths of the following files in the specified order (with the help of variable 'directory' created in Step1).<br />
		1)directory1= directory +"/UCI HAR Dataset/test_folder_/X_test_folder_.txt"<br />
		2)directory2= directory +"/UCI HAR Dataset/test_folder_/y_test_folder_.txt" <br />
		3)directory3= directory +"/UCI HAR Dataset/test_folder_/subject_test_folder_.txt" <br />
		4)directory4= directory +"/UCI HAR Dataset/train_folder_/X_train_folder_.txt" <br />
		5)directory5= directory +"/UCI HAR Dataset/train_folder_/y_train_folder_.txt" <br />
		6)directory6= directory +"/UCI HAR Dataset/train_folder_/subject_train_folder_.txt" <br />
		7)directory7= directory +"/UCI HAR Dataset/act_labels.txt" <br />
		8)directory8= directory +"/UCI HAR Dataset/features.txt" <br />
*Step3: Create data frames 'test_folder_x','test_folder_y','test_folder_sub','train_folder_x','train_folder_y','train_folder_sub','act_lab' and 'feature' and populate data into them using read.table command from file paths stored in variables described in Step2 respectively.<br />
*Step4: Create new data frame 'test_var' and assign data to it by column binding data frames 'test_folder_x','test_folder_y' and 'test_folder_sub'.<br />
*Step5: Create new data frame 'train_var' and assign data to it by column binding data frames 'train_folder_x','train_folder_y' and 'train_folder_sub'.<br />
*Step6: Create new data frame 'bind' and assign data to it by row binding data frames test_var and train_var created in Step 4 and Step5 respectively.<br />
*Step7: Assign column names "subject" and "actid" to first 2 columns of data frame 'bind' created in Step6.<br />
*Step8: Assign column names to columns 3-563 of data frame 'bind' using the data frame 'feature' created in Step3.<br />
*Step9: Using the grep command, extract the column indexes from data frame 'bind' where column names match words 'mean()' or 'std()'. Store this extracted data in new variable 'index'.<br />
*Step10: Create new data frame 'dataset' which contains only column indexes 1,2 and 'index'(created in Step9) from data frame 'bind'.<br />
*Step11: Assign column names "actid" and "activity" to data frame 'act_lab' created in Step3.<br />
*Step12: Load package 'dplyr' using the library command.<br />
*Step13: Inner join data frames 'act_lab' and 'dataset' (created in Step3 and Step10 respectively) on column "actid". Store the resultant dataset into variable 'data'.<br />
*Step14: Exclude the first column from data frame 'data'.<br />
*Step15: Finally, using the summarise_each() function, calculate and display the mean of all columns in data frame 'data'.<br />