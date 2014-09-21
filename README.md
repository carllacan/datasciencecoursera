Getting and cleaning data Course Project
===================

This is my submission for the course project of Coursera's Getting and Cleaning Data course. It starts reading the data from the appropiate files, assuming that the script its located in the "UCI HAR Dataset" directory. It stores the names of the activities and of the features in two lists, and the information of the test and training datasets in two data frames, which are later joined vertically. The columns get the name of their corresponding feature and the rows get their labels according to their activity identifier. 

Afterwards a vector with the indices of the columns of interest is created using a regular expressions applied over the column names, and we get the new data "reduced" according to it. This new data is splitted twice; first we create from it the list sbjdata, which contains an element for the data of each one of the subjects. Then each one of these elements is further splitted into 6 lists, one for each activity, and we get sbjacts. 

At this moment we have 
  30 lists (one for each subject) containing each one
    6 lists (one for each activity) with 
      the values measured for the features at different points in time. 
        
What we need to do now is take the average over time for each one of these features, so we use lapply thrice, in order to do compute
  for every subject of the list
    for every activity of the subject
      for every feature value of that activity
        the average measure of that feature in all timepoints
        
And so we get the list tidy, which contains, for every subject, a list that contains, for every activity, a list with the average of every feature of interest.
  
