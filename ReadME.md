---
title: "Analysis"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
library(dplyr)
```

```{r data_load,echo=TRUE}
features <- read.table("UCI HAR Dataset/features.txt", col.names = c("n", "functions")) 
activities <- read.table("UCI HAR Dataset/activity_labels.txt", col.names = c("code", "activity"))
subject_train <- read.table("UCI HAR Dataset/train/subject_train.txt", col.names = "subject")
x_train <- read.table("UCI HAR Dataset/train/X_train.txt", col.names = features$functions)
y_train <- read.table("UCI HAR Dataset/train/y_train.txt", col.names = "code")
subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt", col.names = "subject")
x_test <- read.table("UCI HAR Dataset/test/X_test.txt", col.names = features$functions)
y_test <- read.table("UCI HAR Dataset/test/y_test.txt", col.names = "code")
```

```{r data_merging ,echo=TRUE}
subject <- rbind(subject_train, subject_test)
x <- rbind(x_train, x_test) 
y <- rbind(y_train, y_test)
merged_data <- cbind(subject, y, x)
```

```{r tidy_data,echo=TRUE}
tidy_data <- merged_data %>%
  select(subject, code, contains("mean"), contains("std"))
tidy_data$code <- activities[tidy_data$code, 2]
```

```{r names,echo=TRUE}
names(tidy_data)[2] <- "activity"
names(tidy_data) <- gsub("^t", "Time", names(tidy_data))
names(tidy_data) <- gsub("^f", "Frequency", names(tidy_data))
names(tidy_data) <- gsub("Acc", "Accelerometer", names(tidy_data))
names(tidy_data) <- gsub("Gyro", "Gyroscope", names(tidy_data))
names(tidy_data) <- gsub("Mag", "Magnitude", names(tidy_data))
names(tidy_data) <- gsub("BodyBody", "Body", names(tidy_data))
```

```{r writing_data,echo=TRUE}
final_data <- summarise(group_by(tidy_data,subject, activity),across(everything(),mean))
write.table(final_data, "final_tidy_data.txt", row.name=FALSE)
```

