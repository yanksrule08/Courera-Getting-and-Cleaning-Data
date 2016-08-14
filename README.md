# Coursera-Getting-and-Cleaning-Data

train_sub <- read.table("./UCI HAR Dataset/train/subject_train.txt", header=FALSE)
colnames(train_sub) <- "subject"
train_act <- read.table("./UCI HAR Dataset/train/y_train.txt", header=FALSE)
colnames(train_act) <- "activity"
train_act[train_act == 1] <- "walking"
train_act[train_act == 2] <- "walking_up"
train_act[train_act == 3] <- "walking_down"
train_act[train_act == 4] <- "sitting"
train_act[train_act == 5] <- "standing"
train_act[train_act == 6] <- "laying"
train_data <- read.table("./UCI HAR Dataset/train/X_train.txt", header=FALSE)
data_colnames <- read.table("./UCI HAR Dataset/features.txt", header=FALSE)
colnames(train_data) <- (data_colnames[,2])
train <- cbind(train_sub, train_act, train_data)

test_sub <- read.table("./UCI HAR Dataset/test/subject_test.txt", header=FALSE)
colnames(test_sub) <- "subject"
test_act <- read.table("./UCI HAR Dataset/test/y_test.txt", header=FALSE)
colnames(test_act) <- "activity"
test_act[test_act == 1] <- "walking"
test_act[test_act == 2] <- "walking_up"
test_act[test_act == 3] <- "walking_down"
test_act[test_act == 4] <- "sitting"
test_act[test_act == 5] <- "standing"
test_act[test_act == 6] <- "laying"
test_data <- read.table("./UCI HAR Dataset/test/X_test.txt", header=FALSE)
colnames(test_data) <- (data_colnames[,2])
test <- cbind(test_sub, test_act, test_data)

data <- rbind(train, test)
data$sub_act <- paste(data$subject,data$activity)
data <- data[ , !duplicated(colnames(data))]
data_m_sd <- select(data, sub_act, contains("mean()"), contains("std()"))

data_grp <- group_by(data_m_sd, sub_act)

data_mean <- summarise_each(data_grp, funs(mean))
