# PROJECT
----------
tab1 <- read.table("/UCI_HAR_Dataset/test/X_test.txt')
print(tab1)

#Activites are different exercises conducted#


```r
activities <- read.table("/UCI_HAR_Dataset/activity_labels.txt",sep="",header=FALSE)
```

```
## Warning in file(file, "rt"): cannot open file '/UCI_HAR_Dataset/
## activity_labels.txt': No such file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```r
colnames(activities) = c("code","name")
```

```
## Error in colnames(activities) = c("code", "name"): object 'activities' not found
```

```r
print(activities)
```

```
## Error in print(activities): object 'activities' not found
```
#features are column names of various measurements

```r
features <- read.table("/UCI_HAR_Dataset/features.txt.",sep=" ",header=FALSE)
```

```
## Warning in file(file, "rt"): cannot open file '/UCI_HAR_Dataset/
## features.txt.': No such file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```r
colnames(features) =c("code","name")
```

```
## Error in colnames(features) = c("code", "name"): object 'features' not found
```

```r
print(features)
```

```
## Error in print(features): object 'features' not found
```

##PREPARING TEST DATA
###subject_test file contains activity ids performed on each person
###x_test contains several columns data of various features
###y_test contains activity ids performed on each person
### Above three files contains same no.of records. First 2 files contains same data

*subjects*

```r
subjects <- read.table("/UCI_HAR_Dataset/test/subject_test.txt",sep=" ",header=FALSE)
```

```
## Warning in file(file, "rt"): cannot open file '/UCI_HAR_Dataset/test/
## subject_test.txt': No such file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```r
colnames(subjects)=c(sub_id)
```

```
## Error in eval(expr, envir, enclos): object 'sub_id' not found
```

```r
head(subjects)
```

```
## Error in head(subjects): object 'subjects' not found
```

```r
tail(subjects)
```

```
## Error in tail(subjects): object 'subjects' not found
```

*act_columns*

```r
activity_columns <- read.table("/UCI_HAR_Dataset/test/y_test.txt",sep=" ",header=FALSE)
```

```
## Warning in file(file, "rt"): cannot open file '/UCI_HAR_Dataset/test/
## y_test.txt': No such file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```r
colnames(activity_columns)=c("act_id")
```

```
## Error in colnames(activity_columns) = c("act_id"): object 'activity_columns' not found
```

```r
head(activity_columns)
```

```
## Error in head(activity_columns): object 'activity_columns' not found
```

```r
tail(activity_columns)
```

```
## Error in tail(activity_columns): object 'activity_columns' not found
```

*features_col*

```r
features_columns <- read.table("/UCI_HAR_Dataset/test/x_test.txt",sep="",header=FALSE)
```

```
## Warning in file(file, "rt"): cannot open file '/UCI_HAR_Dataset/test/
## x_test.txt': No such file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```r
colnames(features_columns)=features$name
```

```
## Error in eval(expr, envir, enclos): object 'features' not found
```

```r
head(features_columns)
```

```
## Error in head(features_columns): object 'features_columns' not found
```

```r
tail(features_columns)
```

```
## Error in tail(features_columns): object 'features_columns' not found
```

*Original test data*

```r
library(dplyr)
tab1=inner_join(activity_columns,activities,by=c("act_id"="code"))
```

```
## Error in inner_join(activity_columns, activities, by = c(act_id = "code")): object 'activity_columns' not found
```

```r
test.data.original=cbind(subjects,activity_columns,features_columns)
```

```
## Error in cbind(subjects, activity_columns, features_columns): object 'subjects' not found
```
----------------------------------------------------------------------------------------------
##PREPARING TRAIN DATA

*subjects*

```r
subjects <- read.table("/UCI_HAR_Dataset/train/subject_train.txt",sep="",header=F)
```

```
## Warning in file(file, "rt"): cannot open file '/UCI_HAR_Dataset/train/
## subject_train.txt': No such file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```r
print(subjects)
```

```
## Error in print(subjects): object 'subjects' not found
```

```r
colnames(subjects)<- c("sub_id")
```

```
## Error in colnames(subjects) <- c("sub_id"): object 'subjects' not found
```

```r
head(subjects)
```

```
## Error in head(subjects): object 'subjects' not found
```

*act_columns*

```r
activity_col <- read.table("/UCI_HAR_Dataset/"train/y_train.txt",sep=" ",header=FALSE)
print(activity_col)
colnames(activity_col) <- c("act_id")
head(activity_col)
```

```
## Error: <text>:1:47: unexpected symbol
## 1: activity_col <- read.table("/UCI_HAR_Dataset/"train
##                                                   ^
```

*features_col*

```r
features_col<- read.table("/UCI_HAR_Dataset/train/X_train.txt",sep="",header=FALSE)
```

```
## Warning in file(file, "rt"): cannot open file '/UCI_HAR_Dataset/train/
## X_train.txt': No such file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```r
print(features_col)
```

```
## Error in print(features_col): object 'features_col' not found
```

```r
colnames(features_col) <- features$name
```

```
## Error in eval(expr, envir, enclos): object 'features' not found
```

```r
head(features_col)
```

```
## Error in head(features_col): object 'features_col' not found
```

*Original train data*

```r
tab2=inner_join(activity_col,activities,by=c("act_id"="code"))
```

```
## Error in inner_join(activity_col, activities, by = c(act_id = "code")): object 'activity_col' not found
```

```r
train.data.original=cbind(subjects,activity_col,features_col)
```

```
## Error in cbind(subjects, activity_col, features_col): object 'subjects' not found
```

```r
print(train.data.original)
```

```
## Error in print(train.data.original): object 'train.data.original' not found
```

```r
head(train.data.original)
```

```
## Error in head(train.data.original): object 'train.data.original' not found
```
