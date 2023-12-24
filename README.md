# Feature-Engineering-99Acres-Data

Here's a brief description of the key steps:

Data Loading and Exploration:

The code starts by importing the necessary libraries, such as NumPy and Pandas.
It reads the raw data from the 'gurgaon_properties_cleaned_v1.csv' file into a Pandas DataFrame named 'df'.
The initial exploration of the dataset is done by displaying the first few rows using df.head().
Handling Total Area:

The 'total_area' column is inconsistent, containing various types of area measurements (e.g., carpet area, built-up area, super built-up area).
Three new columns ('carpet_area', 'built_up_area', 'super_built_up_area') are created based on the 'areaWithType' column using regular expressions to extract the respective areas.
Dealing with Missing Values:

Some rows have missing values in the newly created area columns.
A separate DataFrame 'all_nan_df' is created for rows with missing values in all three area columns.
The missing values are filled by extracting 'Plot area' from the 'areaWithType' column.
Age of Possession Categorization:

The 'agePossession' column is categorized into four groups: New Property, Relatively New, Moderately Old, and Old Property. This is done to simplify the age information.
Additional Room Feature Extraction:

The 'additionalRoom' column contains information about additional rooms (e.g., study room, servant room).
New binary columns ('study room', 'servant room', 'store room', 'pooja room', 'others') are created based on the presence of these rooms.
Furnish Details:

The 'furnishDetails' column is complex, containing various details about furnishing.
Using K-means clustering, it is categorized into three clusters representing unfurnished, semi-furnished, and furnished properties.
A new column 'furnishing_type' is added to the DataFrame.
Features Handling:

The 'features' column contains a list of amenities for each property.
Missing values are filled by merging information from an 'appartments.csv' file.
Binary columns are created for each amenity using MultiLabelBinarizer.
Luxury Score Calculation:

A 'luxury_score' column is created based on the weighted sum of luxury features present in each property.
Drop Unnecessary Columns:

Several columns, such as 'nearbyLocations', 'furnishDetails', 'features', 'features_list', and 'additionalRoom', are dropped as they are no longer needed.
Saving the Result:

The final DataFrame is saved to a new CSV file named 'flats_feature_engineered.csv'.
This feature engineering process enhances the dataset, making it more suitable for exploratory data analysis (EDA) and subsequent machine learning tasks.
