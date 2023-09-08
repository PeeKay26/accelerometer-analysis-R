# Data Analysis Workflow

The `run_analysis.R` script performs the following data preparation steps as part of the course project:

1. **Download the Dataset**

   - The dataset is downloaded and extracted into a folder called "UCI HAR Dataset."

2. **Assign Data to Variables**

   - `features` is assigned from `features.txt`, containing 561 rows and 2 columns.
     - These features originate from accelerometer and gyroscope signals (tAcc-XYZ and tGyro-XYZ).

   - `activities` is assigned from `activity_labels.txt`, with 6 rows and 2 columns.
     - It lists activities performed during measurements, along with their corresponding codes.

   - `subject_test` is assigned from `test/subject_test.txt`, containing 2947 rows and 1 column.
     - This holds data for 9/30 volunteer test subjects being observed.

   - `x_test` is assigned from `test/X_test.txt`, with 2947 rows and 561 columns.
     - It contains recorded features as test data.

   - `y_test` is assigned from `test/y_test.txt`, with 2947 rows and 1 column.
     - It contains test data activity code labels.

   - `subject_train` is assigned from `test/subject_train.txt`, with 7352 rows and 1 column.
     - This contains training data for 21/30 volunteer subjects being observed.

   - `x_train` is assigned from `test/X_train.txt`, with 7352 rows and 561 columns.
     - It contains recorded features as training data.

   - `y_train` is assigned from `test/y_train.txt`, with 7352 rows and 1 column.
     - It contains training data activity code labels.

3. **Merging Training and Test Sets**

   - `X` (10299 rows, 561 columns) is created by merging `x_train` and `x_test` using the `rbind()` function.

   - `Y` (10299 rows, 1 column) is created by merging `y_train` and `y_test` using the `rbind()` function.

   - `Subject` (10299 rows, 1 column) is created by merging `subject_train` and `subject_test` using the `rbind()` function.

   - `Merged_Data` (10299 rows, 563 columns) is created by merging `Subject`, `Y`, and `X` using the `cbind()` function.

4. **Extracting Mean and Standard Deviation Measurements**

   - `TidyData` (10299 rows, 88 columns) is created by subsetting `Merged_Data`, selecting only columns: `subject`, `code`, and measurements on the mean and standard deviation (`std`) for each measurement.

5. **Descriptive Activity Names**

   - Entire numbers in the `code` column of `TidyData` are replaced with corresponding activity names from the second column of the `activities` variable.

6. **Labeling Variables Descriptively**

   - The `code` column in `TidyData` is renamed to `activities`.

   - All "Acc" in column names are replaced by "Accelerometer."

   - All "Gyro" in column names are replaced by "Gyroscope."

   - All "BodyBody" in column names are replaced by "Body."

   - All "Mag" in column names are replaced by "Magnitude."

   - All columns starting with "f" are renamed with "Frequency."

   - All columns starting with "t" are renamed with "Time."

7. **Creating a Second Tidy Data Set**

   - `FinalData` (180 rows, 88 columns) is created by summarizing `TidyData`, taking the means of each variable for each activity and each subject, after grouping by subject and activity.

8. **Exporting Data**

   - `FinalData` is exported to the `FinalData.txt` file.

This script accomplishes the necessary steps for the project's data analysis workflow.
