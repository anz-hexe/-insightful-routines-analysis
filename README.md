# insightful-routines-analysis

This repository contains Jupyter notebooks and scripts designed for processing photos and customizing data for acne detection analysis. 
This project is interconnected with the "[insightful-routines](https://github.com/anz-hexe/insightful-routines)". Its main goal is to process the data obtained from the project, identify the relationship between the data and provide a general analysis.
Below is a brief overview of the key notebooks included in the repository.
At the moment there is not enough data for analysis and forecasting. Workbooks `4_analyz_data.ipynb` and `5_prediction.ipynb` are experimental and the approach to analysis and forecasting will change.
The YOLO model will be added later.

## Notebooks

`1_photo_processing.ipynb`

This notebook performs the following tasks:

- Loads images from a specified folder.
- Detects faces in the images using the MTCNN model.
- Crops and saves detected faces in a new folder.
- Uses the YOLO model to detect acne in the cropped face images.
- Saves the detection results in a JSON file.
- Displays images with detected faces and highlights images where no faces were detected.

`2_customizing_data.ipynb`

This notebook focuses on:

- Loading and cleaning a CSV file with user data.
- Removing unnecessary columns from the dataset.
- Integrating acne detection results from the JSON file generated in `1_photo_processing.ipynb`.
- Summarizing acne detection results and saving the summary in CSV format.
- Merging the summarized results with the original user data and exporting the final dataset.

 `3_preprocessing_data.ipynb`

This notebook is responsible for:

- Preprocessing the merged dataset for further analysis.
- Counting occurrences of various food items mentioned in the user data.
- Categorizing skincare routines and other user habits (e.g., drinks, milk consumption) into binary columns.
- Encoding categorical variables using ordinal encoding.
- Converting boolean columns to numerical values.
- Saving the preprocessed data to a CSV file for model training and further analysis.

 `4_analyz_data.ipynb`

This notebook focuses on:

- Imports necessary libraries, including Pandas for data manipulation and scipy.stats for statistical analysis.
- Loads a dataset from a CSV file named 'data_full.csv' into a Pandas DataFrame.
- Conducts correlation analysis between numerical columns and the 'total_pimples' column in the dataset using the Pearson correlation coefficient and p-values.
- Prints the correlation coefficient and p-value for each numerical column, sorted by p-values.
- Computes the overall correlation of all columns in the dataset with the 'total_pimples' column and prints the correlation values in descending order.

`5_prediction.ipynb`

This notebook performs the following tasks:

-  Imports necessary libraries including Pandas, Optuna, and scikit-learn modules for model training and evaluation.
-  Loads a dataset from a CSV file named 'data_full.csv' into a Pandas DataFrame.
-  Splits the dataset into features (X) and target variable (y).
-  Defines hyperparameters for the Random Forest Regressor model using Optuna's hyperparameter optimization functionality. However, this section is currently commented out.
-  Trains a Random Forest Regressor model on the training data with the best hyperparameters found from the optimization process or predefined hyperparameters.
- Generates predictions on the test data using the trained model.
- Evaluates the model performance using Mean Squared Error (MSE).
- Analyzes feature importances of the trained model and prints them out.

## Files and Directories

- **`PATH_TO_CSV`**: Path to the CSV file containing the original data collected in the "[insightful-routines](https://github.com/anz-hexe/insightful-routines)" project.
- **`PHOTO_FOLDER_PATH`**: Path to the folder containing the original images.
- **`MODEL_PATH`**: Path to the YOLO model for acne detection.
- **`PROJECT_PATH`**: Path to the project directory where results will be saved.
- **`mini_photo`**: Folder where cropped face images are saved.
- **`acne_detection_results.json`**: JSON file containing acne detection results.
- **`summary_file.csv`**: CSV file summarizing acne detection results.
- **`data_with_pimples.csv`**: Preprocessed dataset with acne detection results integrated.

## Dependencies

- Python libraries: `mtcnn`, `ultralytics`, `cv2`, `matplotlib`, `pandas`, `json`, `csv`
- Configuration file `config.py` with paths defined for `PATH_TO_CSV`, `PHOTO_FOLDER_PATH`, `MODEL_PATH`, and `PROJECT_PATH`.

## Usage

1. Ensure all dependencies are installed.
2. Set the correct paths in the `config.py` file.
3. Run the notebooks in the specified order:
    1. `1_photo_processing.ipynb`
    2. `2_customizing_data.ipynb`
    3. `3_preprocessing_data.ipynb`
    4. `4_analyz_data.ipynb`
    5. `5_prediction.ipynb`
4. Use the processed and customized data for further analysis or model training.

## Contributions

Feel free to contribute to this project by submitting issues or pull requests.