# CodeBook

## Data Source
The data used in this project was obtained from the accelerometers of the Samsung Galaxy S smartphone. The original data set can be found at the [UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones).

## Data Description
### Original Data
- **subjects_train.txt / subjects_test.txt**: Subject identifiers for training and test sets.
- **X_train.txt / X_test.txt**: Feature data for training and test sets.
- **y_train.txt / y_test.txt**: Activity identifiers for training and test sets.

### Merged Data
- **subject**: An identifier for the subject who carried out the experiment.
- **activity**: The activity performed by the subject.
- **TimeBodyAccelerometerMeanX**: Time domain body accelerometer mean in the X direction.
- **TimeBodyAccelerometerMeanY**: Time domain body accelerometer mean in the Y direction.
- **TimeBodyAccelerometerMeanZ**: Time domain body accelerometer mean in the Z direction.
- **TimeBodyAccelerometerStdX**: Time domain body accelerometer standard deviation in the X direction.
- **TimeBodyAccelerometerStdY**: Time domain body accelerometer standard deviation in the Y direction.
- **TimeBodyAccelerometerStdZ**: Time domain body accelerometer standard deviation in the Z direction.
- *(And so on for all the mean and standard deviation variables)*

### Transformations
1. **Merging Data Sets**: Combined the training and test sets using `rbind()`.
2. **Extracting Measurements**: Extracted only the measurements on the mean and standard deviation for each measurement using `select()`.
3. **Descriptive Activity Names**: Replaced activity codes with descriptive activity names from `activity_labels.txt`.
4. **Labeling Data Set**: Renamed columns with descriptive variable names, making them more readable by expanding abbreviations and standardizing.
5. **Creating a Tidy Data Set**: Created a second, independent tidy data set with the average of each variable for each activity and each subject using `group_by()` and `summarize_all()`.

### Variables
Below are the variables included in the tidy data set:

- **subject**: Integer identifier for the subject.
- **activity**: String descriptor of the activity performed.
- **TimeBodyAccelerometerMeanX**: Numeric value, mean of time domain body accelerometer signal in the X direction.
- **TimeBodyAccelerometerMeanY**: Numeric value, mean of time domain body accelerometer signal in the Y direction.
- **TimeBodyAccelerometerMeanZ**: Numeric value, mean of time domain body accelerometer signal in the Z direction.
- **TimeBodyAccelerometerStdX**: Numeric value, standard deviation of time domain body accelerometer signal in the X direction.
- **TimeBodyAccelerometerStdY**: Numeric value, standard deviation of time domain body accelerometer signal in the Y direction.
- **TimeBodyAccelerometerStdZ**: Numeric value, standard deviation of time domain body accelerometer signal in the Z direction.
- *(And so on for all the mean and standard deviation variables)*

### Data Processing Steps
1. **Loading Data**: Loaded the datasets from their respective files.
2. **Merging Data**: Merged the training and test sets to create one complete data set.
3. **Filtering Measurements**: Selected only the columns related to mean and standard deviation.
4. **Replacing Activity Codes**: Used descriptive activity names for the activity codes.
5. **Labeling Variables**: Renamed columns with more descriptive names.
6. **Creating Tidy Data Set**: Created a new data set with the average of each variable for each activity and each subject.

### Example Code for Data Transformation
```r
# Load necessary libraries
library(dplyr)

# Read data
features <- read.table("UCI HAR Dataset/features.txt", col.names = c("n", "functions"))
activities <- read.table("UCI HAR Dataset/activity_labels.txt", col.names = c("code", "activity"))
subject_train <- read.table("UCI HAR Dataset/train/subject_train.txt", col.names = "subject")
x_train <- read.table("UCI HAR Dataset/train/X_train.txt", col.names = features$functions)
y_train <- read.table("UCI HAR Dataset/train/y_train.txt", col.names = "code")
subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt", col.names = "subject")
x_test <- read.table("UCI HAR Dataset/test/X_test.txt", col.names = features$functions)
y_test <- read.table("UCI HAR Dataset/test/y_test.txt", col.names = "code")

# Merge the datasets
subject <- rbind(subject_train, subject_test)
x <- rbind(x_train, x_test)
y <- rbind(y_train, y_test)
merged_data <- cbind(subject, y, x)

# Extract measurements on the mean and standard deviation
tidy_data <- merged_data %>%
  select(subject, code, contains("mean"), contains("std"))

# Use descriptive activity names
tidy_data$code <- activities[tidy_data$code, 2]

# Label the data set with descriptive variable names
names(tidy_data)[2] <- "activity"
names(tidy_data) <- gsub("^t", "Time", names(tidy_data))
names(tidy_data) <- gsub("^f", "Frequency", names(tidy_data))
names(tidy_data) <- gsub("Acc", "Accelerometer", names(tidy_data))
names(tidy_data) <- gsub("Gyro", "Gyroscope", names(tidy_data))
names(tidy_data) <- gsub("Mag", "Magnitude", names(tidy_data))
names(tidy_data) <- gsub("BodyBody", "Body", names(tidy_data))

# Create a second, independent tidy data set
final_data <- tidy_data %>%
  group_by(subject, activity) %>%
  summarize_all(funs(mean))

# Write the final tidy data set to a text file
write.table(final_data, "final_tidy_data.txt", row.name=FALSE)
