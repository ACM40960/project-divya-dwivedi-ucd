## Detection of Covid-19 using Chest X-Ray

### Background: 

The first documented instance of a highly transmissible illness caused by the Severe Acute Respiratory Syndrome Coronavirus 2 (SARS-CoV-2) was detected in Wuhan, China, in December 2019. This project aims to leverage chest X-ray images to develop a predictive model for COVID-19 diagnosis. The need for auxiliary diagnostic tools increased as there are no accurate automated toolkits available. Recent findings obtained using radiology imaging techniques suggest that such images contain salient information about the COVID-19 virus. Application of advanced artificial intelligence (AI) techniques coupled with radiological imaging offers the potential for a faster and more accessible diagnostic method, especially in areas where RT-PCR testing resources may be limited.

### Project Workflow

![image](https://github.com/ACM40960/project-divya-dwivedi-ucd/assets/133960362/07d0f198-46fc-457c-9afd-937995acad39)


The proposed system works in following steps:

1. Identifying and splitting the data by labels which can be used to train our model.

2. Designing a supervised learning model(CNN) which will learn from the different features of the image and provide predictions with the highest accuracy possible.

3. Finally, our model will be evaluated using the test dataset and the results will be noted down which will indicate if the proposed model can be used to detect Covid-19 cases. The focus here will be on the false-negatives as the goal is to predict the positive cases of Covid-19 correctly.

### Dataset

For the purpose of the model we use the following dataset which was taken from kaggle.

Link: https://www.kaggle.com/datasets/prashant268/chest-xray-covid19-pneumonia

The Dataset consists of 6536 x-ray images and contains three sub-folders (COVID19, PNEUMONIA, NORMAL). The data is then divided into train, validation and test sets where the test set is 20% of the total data.

![image](https://github.com/ACM40960/project-divya-dwivedi-ucd/assets/133960362/b06fe987-d44b-40b4-8d72-3e858b0294b0)
![image](https://github.com/ACM40960/project-divya-dwivedi-ucd/assets/133960362/50b2ef8c-d10c-4701-ba03-e165e843643d)

The images above show the X-ray images of a normal person and of a person diagnosed with Covid-19.

Before evaluating a model, it is crucial to report the demographic statistics of their datasets, including age and sex distributions. Diagnostic studies commonly compare their models’ performance to that of RT–PCR. 

The data set used for this study is clinical data for individuals aged between 10-90 years with 65% Male and 35% Female ratio. [1]

![image](https://github.com/ACM40960/project-divya-dwivedi-ucd/assets/133960362/bfcc1293-faa2-4642-b6f5-36ed76de24e4)
![image](https://github.com/ACM40960/project-divya-dwivedi-ucd/assets/133960362/825cc9d4-4750-4fac-9e77-ace152ca91e4)


### Model

The model designed here uses three convolutional layers with an input shape of (100, 100, 3) and Rectified Linear Unit (ReLU) activation function to introduce non-linearity in the model. The first layer has 32 filters to convolve over the input image. It also employs dropout and L2 regularization techniques to improve generalization and prevent overfitting. In the final dense layer, the softmax activation function is used to obtain the class probabilities for multi-class classification

![image](https://github.com/ACM40960/project-divya-dwivedi-ucd/assets/133960362/e5cd5125-c7a2-4be9-8458-7f7cf324ede6)

### Results

We are interested in the F1 score of the model. This score provides the balance between precision and recall or in other words it is the accuracy for individual class. From the output below, we can see the overall accuracy is 95.9% for validation and 95.4% for test data. The support count for each class represents the number of images on which the model training and testing was performed. 

<img width="571" alt="image" src="https://github.com/ACM40960/project-divya-dwivedi-ucd/assets/133960362/45547724-692c-4265-8199-695862aa039b">

To analyze the model classification we look into the Confusion matrix of our proposed
model. We can see that the sensitivity (Recall) of Covid-19 (96.2%) is at par with
sensitivity of Pneumonia (96.7%). Due to the fatality of the problem in hand, we aim
to focus on the False Negatives of the model which is only 1 case out of the total
dataset. This is likely due to the overlapping imaging characteristics.

![image](https://github.com/ACM40960/project-divya-dwivedi-ucd/assets/133960362/de89d4ca-5173-4785-83e2-ed5366cb5ae4)

Given the severity of the issue at hand, it is imperative that we create a visualization
of the scare tissue presence. Gradient-wighted Class Activation Mapping uses the
gradients from any target convolutional layer to create a local map which highlights
important feature that the model has learned.The images on the left column are the
actual input images of chest X-ray. heatmap of class activation is then generated
from the image based on the detected features from the image. Finally, the heatmap
is superimposed on the actual image to clearly show the presence of the COVID-19
scare tissue on the X-ray image.

![image](https://github.com/ACM40960/project-divya-dwivedi-ucd/assets/133960362/e30d7887-785e-434c-846c-333bf3f1d7d3)

The high-intensity visuals (blue and green) reflects the area of interest to our model
at the time of prediction

### Application: 

In light of our study to detect Covid-19 using X-ray images, the application of new models has shown promising potential in several areas:

**1. Early Detection and Diagnosis:** Advanced machine learning models can analyze raw chest X-ray images to detect COVID-19 at an early stage, allowing for quicker diagnosis and appropriate treatment, which is crucial for controlling the spread of the virus and providing timely care to patients.

**2. Screening and Triage:** Automated systems can be integrated into healthcare facilities to screen and triage patients, identifying those with potential COVID-19 symptoms, which can help reduce the burden on healthcare resources and minimize the risk of transmission in hospital settings.

**3. Remote and Point-of-Care Diagnosis:** These models could be deployed in remote or point-of-care settings, enabling healthcare professionals in underserved areas or mobile clinics to identify COVID-19 cases rapidly and accurately without the need for immediate access to specialized medical facilities.

**4. Support for Radiologists:** AI-based models can assist radiologists in interpreting chest X-rays, offering a second opinion, enhancing efficiency, and reducing diagnostic errors. Radiologists can focus more on critical cases, leading to better patient outcomes.

**5. Surveillance and Monitoring:** Automated COVID-19 detection systems can be used for real-time monitoring of large populations, helping public health authorities track the spread of the virus and implement targeted interventions to contain outbreaks.

**6. Research and Data Analysis:** The vast amount of data generated from chest X-ray images can be utilized for research purposes, gaining insights into the disease progression, risk factors, and treatment outcomes. AI models can aid researchers in identifying patterns and correlations that might otherwise be challenging to detect manually.

It's important to note that the field of AI in medical imaging and COVID-19 detection is continuously evolving. 

### Challenges and opportunities

Models developed for diagnosis and prognostication from radiological imaging data are limited by the quality of their training data. While many public datasets exist for researchers to train deep learning models for these purposes, we have determined that these datasets are not large enough, or of suitable quality, to train reliable models, and all studies using publicly available datasets exhibit a high or unclear risk of bias. However, the size and quality of these datasets can be continuously improved if researchers worldwide submit their data for public review. Because of the uncertain quality of many COVID-19 datasets, it is likely more beneficial to the research community to establish a database that has a systematic review of submitted data than it is to immediately release data of questionable quality as a public database.

The intricate link of any AI algorithm for detection, diagnosis or prognosis of COVID-19 infections to a clear clinical need is essential for successful translation. As such, complementary computational and clinical expertise, in conjunction with high-quality healthcare data, are required for the development of AI algorithms. Meaningful evaluation of an algorithm’s performance is most likely to occur in a prospective clinical setting. Like the need for collaborative development of AI algorithms, the complementary perspectives of experts in machine learning and academic medicine were critical in conducting this systematic review.

### Conclusion: 

AI computational models used to assess chest X-rays in the process of diagnosing COVID-19 should achieve sufficiently high sensitivity and specificity. Their results and performance should be repeatable to make them dependable for clinicians. Moreover, these additional diagnostic tools should be more affordable and faster than the currently available procedures. The performance and calculations of AI-based systems should take clinical data into account

In our experiments, we have also applied a color visualization approach by using the Grad-CAM technique to make the proposed deep learning model more interpretable and explainable. The obtained results reveal that the patient diagnosed with Pneumonia has more chances to get tested as a False Positive by the proposed algorithm. Therefore, to detect the COVID-19 cases accurately with higher recall, it is suggested to train the model on radiology images of patients with Pneumonia symptoms as well. This will help us to detect pneumonia patients as True Negative (just for clarification-here, COVID-19 cases are True Positive) which were previously detected as false positive. This results in an unbiased detection of COVID-19 cases in a real-time scenario.


### References

[1]  Joseph Paul Cohen, IEEE. (n.d.). GitHub - ieee8023/covid-chestxray-dataset: We are building an open database of COVID-19 cases with chest X-ray or CT images. GitHub. https://github.com/ieee8023/covid-chestxray-dataset

