
<h1 style="text-align: center;">Real-time health monitoring using wearables and Apache Spark Streaming</h1>  
<h3 style="text-align: center;">Girish Nair</h3>  

<h6 style="text-align: center;">Sem-IV, MSDS, CU</h6>
<h6 style="text-align: center;">August 2023</h6>

---
### ABSTRACT  
Today data is growing at an exponential rate. 'Big Data Technology' allows us to harness that data for solving problems which were not possible earlier. It can be applied to all domains. This report concerns with 'Big Data' application in the Healthcare domain. 

Diabetes is a chronic disease which means it is not easily curable, especially because its detected late. However if diabetes detection can be done early its onset can be averted with proper medical intervention. Now with 'Big Data Technology' we can do early detection and take prompt action. Also 'Big Data Technology' can be used to monitor health status and manage diabetes effectively for those who already have it.

This study attempts to design and create a system using wearables and 'Big Data Technology' for real-time health status monitoring.

---
## 1. BACKGROUND (Introduction)  
Today there is a huge amount of data produced by organizations and people. This is made possible by the growing affordability of computing and storage devices along with the rise of AI and ML advancements. They make possible the creation of powerful applications which can be used ubiquitously (i.e. all the time and from anywhere). They in turn produce lots of data in various forms. This data is valuable as it contain rich information which can be harnessed to understand the status of the system and fix any ongoing or future problems.

This concept applies to the healthcare sector as well. People often visit the doctor when they are very sick, but if they can monitor their health on a regular basis, they may be able to take proper action before something goes gravely wrong.

So with the help of '**Big Data**' technology we can today design such an 'Online Health Monitoring System' or '**OHMS**'. It will collect health data from the **wearables**, and send it to the 'Big Data' processing platform on the cloud, eventually providing a glimpse of the users health through the various parameters.

This project proposes to create such a system with practical outcomes for early detection of the chronic disease of Diabetes.

## 2. PROBLEM STATEMENT (Related Research)  
According to Wikipedia a [chronic disease](https://en.wikipedia.org/wiki/Chronic_condition) is persistent or long-lasting in its effects or a disease that comes with time (lasting for more than three months) 

According to WHO, four groups of diseases account for over 80% of all premature [Non-Communicable-Diseases](https://www.who.int/news-room/fact-sheets/detail/noncommunicable-diseases) (NCD) deaths as on 16 Sep 2022.  
1. Cardiovascular diseases account for most NCD deaths, or 17.9 million people annually, 
2. Cancers (9.3 million), 
3. Chronic respiratory diseases (4.1 million), 
4. Diabetes (2.0 million including kidney disease deaths caused by diabetes).

An effective response means : Detection, screening and treatment.

According to IDF.org, the number of adult diabetics (20-79 yrs) worldwide is (in millions):  

 
Year |  2000 | 2021 | 2030 | 2045 | 
:---:|---|---|---|---|  
Diabetics | 151 | 537 | 643 | 783 | 

There are 3 types of diabetes :  
- Type 1 = caused by insulin deficiency.
- Type 2 = caused by lack of bodies ability to use insulin.
- Type 3 = caused by increase in Blood Glucose in pregnant females.

Of these **Type 2 diabetes** accounts for **90-95%** of all cases. [6]  
Diabetes is said to occur due to genetic reasons, poor diet and lack of physical activity. Critical cases can lead to other complications like blindness, kidney failure, heart attacks and lower limb amputation. [25, 26]

We must use the now available huge amount of health data, generated form patient interaction, patient health records, hospital database, medical research, institutional and Government database etc, for early diabetes detection and prompt medical intervention before its too late.

However using 'Big Data' has its own challenges [2] :  
- Collecting large amounts of data from various sources
- Storing that large and hetrogenous data
- Analysing big data in real-time
- Provide real-time access of actionable insights to end-users [8]

Study related to 'Online prediction of diseases' are rare [2] and most of those are recent. So templates or boilerplates are not readily available. On will have to experiment a lot to get a fine-tuned working system.

There are many architectures adopted for diabetese monitoring. Data is collected from smart sensors attached to the body (Body Sensor Network). It is transmitted using BLE (Bluetooth Low Energy) [6] or WiFi to a nearby smartphone gateway or arduino device or raspberry pi etc [33]. This data is then routed to the cloud. Data ingestion is done by Kafka, Flume, RabbitMQ etc. and processed by Spark, Samza, Flink and other stream processing frameworks. Big data storage is achieved using Hdfs, HBase, Cassandra, MongoDB etc. Also the results obtained is displayed to the end-users using Web apps, Mobile apps, Dashboards, Reports, Alert servers and Hospital social networks [31].
</br></br>

## 3. RESEARCH QUESTIONS  
The availability of large healthcare datasets and the exponential advancement of AI and ML along with IoT has made computer predictions highly accurate [1].  
> So is it possible to design and create a real-time system using wearables along with big data technology for online health status monitoring (OHMS).

## 4. AIM AND OBJECTIVES  
The main aim of this study is to create a system to give users (patients and doctors) a peek into the health status and trends for early detection, diagnosis and prevention of the chronic disease : **Diabetes**.   
These patients can include both those undergoing treatment and out-patients.  This system can be used by healthy people wanting to monitor their health regularly.  

The research objectives planned to be met are :  
- To choose the most appropriate data source or data collection device (wearable)
- To experiment with multiple ML and DL models to get the best and most efficient model
- To create a dashboard that takes care of users/stakeholder needs and project goals


## 5. SIGNIFICANCE OF THE STUDY  
The OHMS can be extremely helpful to people concerned about keeping in good health. Having said that, it is assumed that they already follow good eating habits and are doing regular physical exercises.  
If their health goes off-course for any reason whatsoever, they will get notified and **can take prompt action** to remedy the situation (adjust meds, seek expert medical help etc.). This way chronic diseases will always be in check and good health will be more prevalent.  
Also hospitals will be less burdened as they will be able to attend to more cases at early stages of the disease. Cases in terminal stages will drop considerably when more people use the sytem on a regular basis.

## 6. SCOPE OF THE STUDY  
It is proposed that the study be conducted for 5 users over a period of 7 days. Data can be ideally collected every minute or five minutes as deemed fit for the particular usecase and sent to the cloud for further action. After the data gets processed, a health status report is published to the Dashboard.   
The system can be fine-tuned over many iterations and accuracy can be increased till acceptable thresholds are achieved. 


## 7. RESEARCH METHODOLOGY (Design)  

The objective is to have a real-time glimpse of the users health status. So we need to gather health data using a wearables like 'Fitbit wristband' or such devices. The '**vital signs**' data through a mobile app is sent to Kafka messaging system, which can be used as a buffer for the messages. It is then sent to Apache Spark Streaming pipeline where after preprocessing an algorithm will do a prediction for disease. The prediction or diagnosis is the sent back to the user. The users can check it in 'Real Time'. Alerts will be sent if there is a health scare.

Various IoT devices and wearables like [Fitbit](https://www.fitbit.com/global/in/technology/health-metrics) and [Corsano](https://corsano.com/solutions/remote-patient-monitoring/) bracelets are available in the market. They come with open API for real time data access. They collect vital sign data like : **Temperature, Weight, Blood Pressure, Blood Glucose, Heart Rate, Oxygen Saturation (SPO2), Respiration Rate, Level of consciousness** etc. [6]. Other options are : **EEG, ECG, EMG, Pulse, Motion, Accelerometer** etc. [14]. Mostly these devices transfer their data to the smart phone app from where it is sent to the cloud server.


![Diabetes Detection Workflow](/assets/OHMS_arch_2.jpg)  
Figure 1 : Diabetes Detection Workflow  


The data from various smart phones gets transferred into a messaging system like Kafka. It is a distributed platform to hold messages temporarily in 'Topics' correlated with different categories of patients and service plans. This transfer uses the secured internet connection in most cases with https protocol (128-bit encryption), or a VPN (virtual private network) kind of network for added security. 

From Kafka data is sent to Apache Spark Streaming for processing and modeling. Apache Spark framework is a distributed in-memory parallel processor which is extremely fast and most popular. You could directly transfer smart phone data to Spark without using Kafka, but during high load times (many users accessing spark simultaneously, says in thousands or tens of thousands) Spark may fail to collect the data and hence Kafka is employed. Kafka acts like a buffer before the raw unlabeled data is sent to Spark in an orderly fashion [2].

Spark receives this streaming patient data and does preprocessing on it like, removing redundant and invalid data, clustering into related groups, making data balanced, selecting relevant subset for analysis, normalizing features with large variations etc. This is essential to develop good classification models. **Right feature selection** can provide models of greater accuracy with reduced run time. Techniques like PCA (principle component analysis), RFE (recursive feature elimination), MI (mutual information) and correlation analysis can be used to get best set of features [7].

After preprocessing the model is then developed with Apache Spark using the collected historical data. This is a batch operation done at some regular interval like midnight each day. This model is then copied into the Spark Streaming environment replacing its current model. Thus online model update is accomplished and the model never drifts out of the input distributions [2].

The study involves using Spark MLlib for testing and modeling with different algorithms like **Random Forest, Support Vector Machine, Logistic Regression, Naïve Bayes, Gradient Boosting, Artificial Neural Networks, Ensemble models** etc. to arrive at the best possible algorithm for the streaming health data events. Parameters such as window size, tree depth in case of decision tree etc. can be fine tuned to get better results. The model predicts if a diabetes risk is present or not. When BG (Blood Glucose) prediction is combined with diet and exercise data, personalized health routines can be prescribed for the user [6].

The model can then be evaluated using metrics like **Accuracy, Precision, Recall, F1 score and execution time** [7]. The frequency of data collection and model update is planned to be strict initially and can be relaxed in time depending on the outcome conditions. Also accuracy and confidence in the model is greatly boosted by employing Cross-validation in the modeling stage.

Both the processed data and the predictions are stored in Cassandra which is a distributed columnar NoSQL database. The predictions data gets served to a visualization software like Tableau or Power BI which can be used to create a 'Dashboard'. It will display the overall health status for all end-users individually and collectively. Alerts will show up onscreen which the doctors or service personnel can attend to for quick remedial action. 


## 8. REQUIREMENTS RESOURCES (Design)  
The proposed design involves: data collection from wearables like 'Fitbit' or such devices, Kafka for messaging, Spark Streaming to process streaming data, Apache Spark to process batch data, Apache Cassandra to store data and serve predictions, Tableau or Power-BI Dashboard to show the health parameters and prediction/diagnosis.

The total records can be around 50,000 to 60,000 spanning a week of data collection. 
A Spark cluster of 1 master 2 worker setup should suffice. However with more users or increasing parameters more workers may be required.

Initial testing can be done on a local Cloudera Quick-Start VM and then the application ported to Amazon AWS EMR big data platform and then tested for large scale deployment.

A master node must have:  
- Core i7 processor, with 4 cores, 8 GB RAM, 20 GB memory and Ubuntu OS. 

A worker node must have:  
- Core i3 processor, with 4 cores, 4 GB RAM, 20 GB memory and Ubuntu OS. 

## 9. RESEARCH PLAN  
1. Background research and literature review (Dur: 4 weeks)
	- Meet with stakeholders and concerned people
	- Collect and analyze relevant literature
	- Develop a theoretical framework

2. Research design planning (Dur: 3 weeks)
	- Design questionnaires
	- Identify participants
	- Recruit team members/volunteers

3. Data collection and preparation (Dur: 6 weeks)
	- Collect responses from sent questionnaires
	- Conduct interviews with select participants
	- Choose a data collection device (wearable)
	- Create data repository
	- Collect additional data from various data sources
	- Clean and prepare data for analysis

4. Data analysis and modeling (Dur: 5 weeks)
	- Conduct EDA
	- Experiment with different ML and DL algorithms
	- Develop a model and evaluate it.
	- Analyze the results with respect to research objective
	- Develop a dashboard
	- Deploy the solution

5. Writing (Dur: 5 weeks)
	- Complete writing 1st draft 
	- Get stakeholder feedback for revision
	- Write 2nd draft based on feedback
	- Get supervisor approval
	- Write final Report 


---
### REFERENCES  
  
[1] Nair, L.R., Shetty, S.D. and Shetty, S.D., 2018. Applying spark based machine learning model on streaming big data for health status prediction. Computers & Electrical Engineering, 65, pp.393-399.  
[2] Hassan, F., Shaheen, M.E. and Sahal, R., 2020. Real-time healthcare monitoring system using online machine learning and spark streaming. International Journal of Advanced Computer Science and Applications, 11(9).  
[3] Tsui, F.C., Espino, J.U., Dato, V.M., Gesteland, P.H., Hutman, J. and Wagner, M.M., 2003. Technical description of RODS: a real-time public health surveillance system. Journal of the American Medical Informatics Association, 10(5), pp.399-408.  
[4] Shameer, K., Badgeley, M.A., Miotto, R., Glicksberg, B.S., Morgan, J.W. and Dudley, J.T., 2017. Translational bioinformatics in the era of real-time biomedical, health care and wellness data streams. Briefings in bioinformatics, 18(1), pp.105-124.  
[5] Benhlima, L., 2018. Big data management for healthcare systems: architecture, requirements, and implementation. Advances in bioinformatics, 2018.  
[6] Alfian, G., Syafrudin, M., Ijaz, M.F., Syaekhoni, M.A., Fitriyani, N.L. and Rhee, J., 2018. A personalized healthcare monitoring system for diabetic patients by utilizing BLE-based sensors and real-time data processing. Sensors, 18(7), p.2183.  
[7] Tiwari, S. and Agarwal, S., 2023. Empirical analysis of chronic disease dataset for multiclass classification using optimal feature selection based hybrid model with spark streaming. Future Generation Computer Systems, 139, pp.87-99.  
[8] McPadden, J., Durant, T.J., Bunch, D.R., Coppi, A., Price, N., Rodgerson, K., Torre Jr, C.J., Byron, W., Young, H.P., Hsiao, A.L. and Krumholz, H.M., 2018. A scalable data science platform for healthcare and precision medicine research. arXiv preprint arXiv:1808.04849.  
[9] Yildirim, E., Cicioğlu, M. and Çalhan, A., 2022. Real-time internet of medical things framework for early detection of Covid-19. Neural Computing and Applications, 34(22), pp.20365-20378.  
[10] Ebada, A.I., Elhenawy, I., Jeong, C.W., Nam, Y., Elbakry, H. and Abdelrazek, S., 2022. Applying apache spark on streaming big data for health status prediction. Comput., Mater. Continua, 70(2), pp.3511-3527.  
[11] Ed-daoudy, A., Maalmi, K. and El Ouaazizi, A., 2023. A scalable and real-time system for disease prediction using big data processing. Multimedia Tools and Applications, pp.1-30.  
[12] Awadalla, M., Kausar, F. and Ahshan, R., 2021. Developing an IoT platform for the elderly health care. International Journal of Advanced Computer Science and Applications, 12(4).  
[13] Harb, H., Mroue, H., Mansour, A., Nasser, A. and Motta Cruz, E., 2020. A hadoop-based platform for patient classification and disease diagnosis in healthcare applications. Sensors, 20(7), p.1931.  
[14] Satyanarayana, T.V.V., Roopa, Y.M., Maheswari, M., Patil, M.B., Tamrakar, A.K. and Shankar, B.P., 2022. A secured IoT-based model for human health through sensor data. Measurement: Sensors, 24, p.100516.  
[15] Arpna Joshi, Chirag Singla, Mr. Pankaj, "Analysing and Predicting on Diseases using Data Pipeline in Hadoop ", International Journal of Scientific Research in Computer Science, Engineering and Information Technology (IJSRCSEIT), ISSN : 2456-3307, Volume 5 Issue 2, pp. 1288-1292, March-April 2019.  
[16] Asri, H. and Jarir, Z., 2023. Toward a smart health: big data analytics and IoT for real-time miscarriage prediction. Journal of Big Data, 10(1), pp.1-23.  
[17] Fakhfakh, O., Megdiche, I., Dalce, R. and Val, T., 2021, May. A Lambda Architecture for Imbalance Prediction with Smart Cane. In 8ème Colloque en Télésanté et dispositifs biomédicaux (JETSAN 2021) (pp. 1-4).  
[18] Shrotriya, L., Sharma, K., Parashar, D., Mishra, K., Rawat, S.S. and Pagare, H., 2023. Apache Spark in Healthcare: Advancing Data-Driven Innovations and Better Patient Care. International Journal of Advanced Computer Science and Applications, 14(6).  
[19] Dubale, Y. and Wagh, M.K., Prediction Of Chronic Diseases From X-Rays Using Distributed Machine Learning.  
[20] Kaur, J. and Mann, K.S., 2017, December. AI based healthcare platform for real time, predictive and prescriptive analytics using reactive programming. In Journal of Physics: Conference Series (Vol. 933, No. 1, p. 012010). IOP Publishing.  
[21] Ed-daoudy, A. and Maalmi, K., 2019. A new Internet of Things architecture for real-time prediction of various diseases using machine learning on big data environment. Journal of Big Data, 6, pp.1-25.  
[22] Naghib, A., Jafari Navimipour, N., Hosseinzadeh, M. and Sharifi, A., 2023. A comprehensive and systematic literature review on the big data management techniques in the internet of things. Wireless Networks, 29(3), pp.1085-1144.  
[23] Paganelli, A.I., Mondéjar, A.G., da Silva, A.C., Silva-Calpa, G., Teixeira, M.F., Carvalho, F., Raposo, A. and Endler, M., 2022. Real-time data analysis in health monitoring systems: A comprehensive systematic literature review. Journal of Biomedical Informatics, 127, p.104009.  
[24] Imran, S., Mahmood, T., Morshed, A. and Sellis, T., 2020. Big data analytics in healthcare− A systematic literature review and roadmap for practical implementation. IEEE/CAA Journal of Automatica Sinica, 8(1), pp.1-22.  
[25] Rajendra, P. and Latifi, S., 2021. Prediction of diabetes using logistic regression and ensemble techniques. Computer Methods and Programs in Biomedicine Update, 1, p.100032.  
[26] Saravi, F.B., Moghanian, S., Javidi, G. and Sheybani, E.O., 2021. Machine Learning in Apache Spark Environment for Diagnosis of Diabetes.  

---

