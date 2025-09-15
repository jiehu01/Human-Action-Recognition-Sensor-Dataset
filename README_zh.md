1. # 人体活动识别（HAR）数据集

   整理了多个人体活动行为识别传感器（加速计）数据集，对他们进行标准化，可以方便的读取npy文件进行使用。

   ## 1. PAMAP2 数据集（Physical Activity Monitoring Dataset, P）[1]

   该数据集从 9 位被试者收集了 18 种活动动作。这个数据集包含 3 个加速计传感器（分别位于手臂，胸部和脚踝）以及 1 个心率传感器。本文在实验中使用了手臂的加速计运动传感器数据，采样频率为 100Hz。

   ## 2. WISDM 数据集（Wireless Sensor Data Mining, W）[2]

   该数据集由福坦莫大学的无线运动传感器数据挖掘实验室采集，包含 29 名用户的数据。它使用一个放置于用户裤子口袋中的智能手机采集用户的行走、慢跑、上楼梯、下楼梯、站立和静坐的加速计运动传感器数据，数据的采样频率为 20Hz。

   ## 3. UCI HAR 数据集（Human Activity Recognition Using Smartphones Dataset, U）[3]

   该数据集由来自热那亚大学的研究团队采集，包含 30 名年龄位于 19 岁到 48 岁之间的用户。用户在采样期间执行行走、上楼梯、下楼梯、站立、静坐、平躺的动作，采样频率为 50Hz。实验共进行两次采集：第一次将智能手机固定于用户腰部，第二次测试时，智能手机由用户自行放置。在采集加速计和陀螺仪数据的同时，记录用户执行每个动作的视频，后期根据这些视频和运动传感器数据进行手动标注所属运动类别。

   ## 数据处理方式

   对于所有数据集，均使用记录的加速计数据。在人体活动识别（HAR）任务中，选择了四种类型的动作：行走、上楼梯、下楼梯和静坐。实验前，通过线性插值将所有数据集的采样频率统一为 50Hz（对于 WISDM 为上采样，对于其他数据集为下采样）。使用一个步长为 128（2.56 秒）的滑动窗口将不同长度的原始数据段划分为样本，样本之间没有重叠。处理后的数据统计如下：

   | 数据集 | 用户数量 | 原始数据段数量 | 样本数量 | 分类别样本数量（行走, 上楼梯, 下楼梯, 静坐） |
   | ------ | -------- | -------------- | -------- | -------------------------------------------- |
   | UCIHAR | 30       | 616            | 3374     | 893, 809, 746, 926                           |
   | WISDM  | 51       | 323            | 13658    | 8258, 2341, 1901, 1158                       |
   | PAMAP2 | 9        | 361            | 4727     | 1584, 905, 808, 1430                         |

   ---

   如果要使用该数据集，请引用（作者会很高兴）：

   - Wen S, Chen Y, Ma Y, et al. *Time Series Adaptation Network for Sensor-based Cross Domain Human Activity Recognition* [C]//2023 International Joint Conference on Neural Networks (IJCNN). IEEE, 2023: 1-8. [4]

   ## 参考文献

   1. Reiss A, Stricker D. *Introducing a new benchmarked dataset for activity monitoring* [C]//2012 16th International Symposium on Wearable Computers. IEEE, 2012: 108-109.  
   2. Kwapisz J R, Weiss G M, Moore S A. *Activity recognition using cell phone accelerometers* [J]. ACM SigKDD Explorations Newsletter, 2011, 12(2): 74-82.  
   3. Anguita D, Ghio A, Oneto L, et al. *A public domain dataset for human activity recognition using smartphones* [C]//Proceedings of the 21th International European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning. 2013: 437-442.  
   4. Wen S, Chen Y, Ma Y, et al. *Time Series Adaptation Network for Sensor-based Cross Domain Human Activity Recognition* [C]//2023 International Joint Conference on Neural Networks (IJCNN). IEEE, 2023: 1-8.