# Human Activity Recognition (HAR) Datasets

We compiled multiple human activity recognition (HAR) datasets, each collected using IMU sensors. These datasets cover four activity states: walking, ascending stairs, descending stairs, and sitting. Further details can be found in the paper [Time Series Adaptation Network for Sensor-based Human Activity Recognition](#ref4).

## 1. PAMAP2 Dataset (Physical Activity Monitoring Dataset, P) [1]

This dataset contains 18 types of physical activities collected from 9 subjects. It includes data from three accelerometer sensors (located on the arm, chest, and ankle) as well as a heart rate monitor. In our experiments, we use the accelerometer data from the arm sensor, sampled at 100 Hz.

## 2. WISDM Dataset (Wireless Sensor Data Mining, W) [2]

Collected by the Wireless Sensor Data Mining (WISDM) Lab at Fordham University, this dataset consists of data from 51 users. A smartphone placed in the user’s pants pocket was used to record accelerometer data while performing activities such as walking, jogging, ascending stairs, descending stairs, standing, and sitting. The sampling rate is 20 Hz. In our study, we utilize only the accelerometer data.

## 3. UCI HAR Dataset (Human Activity Recognition Using Smartphones Dataset, U) [3]

Developed by a research team at the University of Genoa, this dataset includes 30 subjects aged between 19 and 48 years. During data collection, participants performed six activities: walking, ascending stairs, descending stairs, standing, sitting, and lying down. The sampling rate is 50 Hz. Two recording sessions were conducted: in the first, the smartphone was fixed at the user’s waist, while in the second, the smartphone was positioned freely by the user. In addition to accelerometer and gyroscope measurements, video recordings of each activity were captured, and the activity labels were manually annotated based on both the video and sensor data. For our experiments, we use only the accelerometer data.

## Data Organization

For all datasets, only the recorded accelerometer data are used. Each user’s data consists of multiple **Raw Segments**, and each Raw Segment contains multiple samples. Data are organized as a list of `<X.npy, Y.npy>` pairs per Raw Segment. Each Raw Segment includes three-axis accelerometer data:

- `X.npy` stores the sensor measurements, with shape `[num_samples, 128, 3]`  
- `Y.npy` stores the corresponding labels, with shape `[num_samples]`  

For example, `X.npy` with shape `[5,128,3]` and `Y.npy` with shape `[5]` indicates that this Raw Segment contains 5 samples after segmentation.

## Data Preprocessing

In the HAR task, we selected four activity types: walking, ascending stairs, descending stairs, and sitting. Before experiments, the sampling frequency of all datasets was unified to 50 Hz using linear interpolation (up-sampling for WISDM and down-sampling for the other datasets).  

A sliding window of length 128 (2.56 seconds) was applied to divide variable-length raw data segments into samples, without overlap between samples. The processed data statistics are summarized below:

| Dataset | Number of Users | Number of Raw Segments | Number of Samples | Samples per Activity (Walking, Upstairs, Downstairs, Sitting) |
| ------- | --------------- | ---------------------- | ----------------- | ------------------------------------------------------------ |
| UCIHAR  | 30              | 616                    | 3374              | 893, 809, 746, 926                                           |
| WISDM   | 51              | 323                    | 13658             | 8258, 2341, 1901, 1158                                       |
| PAMAP2  | 9               | 361                    | 4727              | 1584, 905, 808, 1430                                         |

```
Hint: The labels are represented by numbers and are in the same order as the following table
```

---

If you use these datasets, please cite the following work (the authors would be glad that their results contribute to other research):

- Wen S, Chen Y, Ma Y, et al. *Time series adaptation network for sensor-based cross domain human activity recognition* [C]//2023 International Joint Conference on Neural Networks (IJCNN). IEEE, 2023: 1-8. [4]

## References

1. Reiss A, Stricker D. *Introducing a new benchmarked dataset for activity monitoring* [C]//2012 16th International Symposium on Wearable Computers. IEEE, 2012: 108-109.  
2. Kwapisz J R, Weiss G M, Moore S A. *Activity recognition using cell phone accelerometers* [J]. ACM SigKDD Explorations Newsletter, 2011, 12(2): 74-82.  
3. Anguita D, Ghio A, Oneto L, et al. *A public domain dataset for human activity recognition using smartphones* [C]//Proceedings of the 21th International European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning. 2013: 437-442.  
4. Wen S, Chen Y, Ma Y, et al. *Time series adaptation network for sensor-based cross domain human activity recognition* [C]//2023 International Joint Conference on Neural Networks (IJCNN). IEEE, 2023: 1-8.