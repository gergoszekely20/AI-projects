## Project 1
I loaded the test and train datasets to explore their structure. Upon observation, I found that the test dataset contained 82 non-null columns, consisting of 3 integer columns, 11 object columns, and 68 float columns. The training dataset was similar to the test dataset, except it had an additional column called "DiagPeriodL90D," which indicated whether a patient was diagnosed with breast cancer or not. I displayed detailed statistics for both datasets, including the count, minimum, and maximum values for each column.

In terms of data description, I examined the test dataset's descriptive statistics, covering both numerical and object type columns. Additionally, I identified the number of rows and columns in both datasets and confirmed that there were no duplicate entries in either the test or train datasets. Upon analyzing missing values in the test dataset, I noted a significant number of nulls in columns like 'metastatic_first_novel_treatment,' 'metastatic_first_novel_treatment_type,' 'bmi,' and 'patient_race.'

For data visualization, I plotted the value counts of the 'Region' column in the test dataset as a pie chart. Furthermore, I visualized the distribution of 'payer_type' and 'patient_age' in the test dataset using histograms. It was apparent from the visualizations that most participants in the study were above 45 years old, indicating a higher likelihood of breast cancer diagnosis in older women.

In terms of cancer diagnosis analysis, I examined the frequency of breast cancer diagnosis codes in the training dataset. I also visualized the distribution of breast cancer diagnoses within the last 90 days, noting a higher number of recent diagnoses. Additionally, I compared the ease of diagnosing different breast cancer types within 90 days, highlighting that some types were diagnosed quicker than others. Moreover, I analyzed the correlation between patient age and breast cancer diagnosis within 90 days, observing a higher diagnosis rate in older age groups.

During data observations, I identified columns that might not be useful for analysis, such as 'Ozone,' 'PM25,' 'NO2,' and 'men,' which were not directly related to breast cancer. I also displayed histograms for each numerical column to gain detailed insights into their distributions.

For data cleaning and preparation, I dropped unnecessary columns from the test dataset, including 'patient_id,' 'metastatic_first_novel_treatment_type,' 'metastatic_first_novel_treatment,' 'patient_race,' 'bmi,' 'Ozone,' 'PM25,' and 'NO2.' I filled missing values in categorical columns with 'Unknown' and imputed missing values in numerical columns using IterativeImputer to handle any remaining nulls.

In conclusion, this detailed exploration and cleaning of the test and train datasets provided a solid foundation for further analysis and model training. By focusing on filling missing values and dropping irrelevant columns, I ensured that the data was in a suitable format for machine learning applications.

## Project 2
In my analysis of the training table, I identified several columns with numerous missing values or strings, such as 'metastatic_first_novel_treatment_type', 'metastatic_first_novel_treatment', 'bmi', and 'patient_race'. These columns seemed unlikely to be helpful, so I decided to remove them. Additionally, I noted that 'patient_id' is unique for each patient, making it unnecessary for analysis, and 'patient_gender' also had unique entries. Consequently, I removed these columns as well.

From the metastatic diagnosis period graphs, it became apparent that the disease was typically diagnosed within the first 100 days. To further understand the data, I visualized 'patient_race' and discovered that more than half of the diagnosed individuals were 'white'.

I also examined patient ages to understand the age distribution at diagnosis. Most individuals were between 40 and 70 years old. Interestingly, the data showed that more 'white' and 'black' individuals were diagnosed at age 60, whereas 'hispanic', 'asian', and 'others' were more frequently diagnosed at age 55.

When exploring the relationship between 'payer_type' and the speed of diagnosis, I observed that patients with insurance tended to receive quicker diagnoses.

For model selection, I considered Linear Regression with Ridge regularization due to its interpretability and computational efficiency. However, I initially built two Random Forest Regression models: one using certain columns and another using the same columns plus a newly created age category column.

To categorize patients by age group, I developed a function that segmented the ages accordingly. The addition of the age category column slightly improved the performance of the Random Forest Regression model.

Finally, I experimented with combining two models to enhance the final prediction accuracy. This combination resulted in a modest improvement in the machine learning model's performance.



## Project 3
I chose image classification as my project, specifically to differentiate between 5 breeds of dogs.

My dataset contains a folder named "data," which contains two other directories: "train" and "validation." Each of these directories has five subdirectories, each named after a dog breed. The "train" directory contains 308 images from which the model can learn, while the "validation" directory contains 84 images.

The dataset has already been split into training and validation directories, so there was no need for manual splitting.

I performed preprocessing on the dataset using ImageDataGenerator from Keras to augment and normalize the images.

I used a CNN architecture with a pre-trained VGG16 backbone, to which I added additional layers for training. I chose VGG16 because it is a well-known and high-performing model for image classification, and using a pre-trained model helps achieve higher accuracy with limited data.

The model was trained for 30 epochs with the following hyperparameters:
Learning rate: 1e-4
Batch size: 32
I used the Adam optimizer and the binary_crossentropy loss function. Additionally, I attempted fine-tuning by unfreezing the last 4 layers of the base model and continuing training with a lower learning rate (1e-5) for another 10 epochs.

The evaluation metrics used were accuracy and loss. These are important for understanding how well the model correctly classifies images and how well it minimizes error on the validation set.

From the experiments, I observed that the model performs well on the validation dataset. However, in cases where images are ambiguous or contain similar artifacts between classes, the model can have difficulty in correct classification. This can be improved by augmenting the dataset with more diverse examples or by using more complex architectures pre-trained on similar data.