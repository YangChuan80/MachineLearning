# Karoytyping Pinnacle: Support Vector Machine
Chromosome Classification via Deep Learning Applied in Patients with Structural Abnormalities of Chromosomes

***Chuan Yang*** (<yangc@sj-hospital.org>)

## Introduction
Karyotyping is an important procedure in cytogenetic practice for an early diagnosis of genetic diseases. The etiologies of many diseases originate from the abnormalities of karyotypes, such as leukemia, Down syndrome, simultaneous abortion, etc. So, the karyotype analysis is the basis and important reference for further diagnosis of genetics-related disease and preimplantation genetic diagnosis and screening. It has the advantages of ease of specimen aggregation and low testing costs. However, the clinical work of karyotyping is tedious, time-consuming, and sometimes error-prone, which is a heavy-load job even for an experienced cytogeneticist.

**Objective**: The objective of our study was to propose a novel DCNN-based model for automatically classifying both normal and abnormal chromosomes with the extracted chromosome images from patients, and an assessment was made to evaluate the performance of the model on a further translation of clinical practice, so that automatic classification of chromosomes is achieved to reduce the workload of chromosome karyotype analysts.

**Methods**: We analyzed 2,968 chromosomes of 63 patients with normal chromosomes and 544 abnormal chromosomes of 25 patients from our hospital. These chromosomes in peripheral blood or amniotic fluid samples were harvested based on the protocols, which were digested by trypsin and stained by Giemsa at approximately 300~500 bands resolution. The chromosomes contained all the autosomes (classes 1-22) and two sex chromosomes (either X or Y). We segmented and isolated every chromosome from the original image into the corresponding labeled class, then every centromere of the chromosome was aligned manually with the middle point of the image canvas, and the pixel values of images were extracted with PIL (Python imaging library) package, and then 300 × 300 NumPy arrays as features (X values) were generated. We labelled the generated the NumPy arrays of chromosomes as 32 classes with labels including 24 classes of normal chromosomes (Chr 1, Chr 2, Chr 3, Chr 4, Chr 5, Chr 6, Chr 7, Chr 8, Chr 9, Chr 10, Chr 11, Chr 12, Chr 13, Chr 14, Chr 15, Chr 16, Chr 17, Chr 18, Chr 19, Chr 20, Chr 21, Chr 22, Chr X, Chr Y) and 8 classes of abnormal chromosomes: del(5)(p14), inv(9)(p12q13), del(18)(p11), i(18)(q10), i(X)(q10), del(X)(p22), del(X)(q21), del(X)(q22) as the y values. We proposed the DCNN-based model. The architecture of the model contains 11 layers: three 3 × 3 convolutional layers, three max-pooling layers, one flatten layer, and four fully connected layers. The channel numbers of the three convolutional layers are 32, 64, and 64 respectively. The features extracted from each convolutional layer were down-sampled by a max-pooling layer with a 2 × 2 window, and the softmax function (cross-entropy) was used as the training loss function. Each convolutional layer includes a convolution operation and a non-linear activation, while each fully connected layer multiplies its input by a weight matrix and then adds a bias vector, followed by a non-linear activation. ReLU (rectified linear unit) is used as the activation function. Every 5-fold cross-validation was performed to evaluate the performance of the proposed model under four commonly generated metrics, including accuracy, precision, recall, and F1 score. We especially analyzed the chromosomes in eight abnormal variants. Confusion matrices were calculated in the multi-class classifications. And we also used the receiver operating characteristic (ROC) curve and area under the curve (AUC) score to evaluate binary classifications in the abnormal chromosomes. We run our models with Python programming language, and TensorFlow and Keras package were implemented as the key framework to construct a neural network to train and validate the image data.  

**Results**: We applied the proposed DCNN-based model to classify both normal and abnormal chromosome images. The generated metrics of the model were averaged after five times of training and validating independently as cross-validation results. The average accuracy of the normal chromosomal classification was 91.75%; the precision, recall, and F1 were 91.81%, 91.75%, and 91.75%, respectively. The accuracy of the merged dataset of normal and abnormal karyotypes was 87.76%; the precision, recall, and F1 were 87.81%, 87.76%, and 87.70%, respectively. Our study is a first attempt to differentiate eight common structural abnormalities of chromosomes with the DCNN model from its corresponding normal chromosomes. We got the accuracies ranging from 90.84%-100%, and the values of the area under the curve ranged from 91.81%-100%. The classification of i(18)(q10) reached the highest accuracy rate, which was 100%, and the precision, recall, and F1 score were all 100%, while the AUC was 100%. The del(18)(p11) abnormality got the lowest accuracy rate (90.84%), and the precision, recall, F1, and AUC were 90.74%, 90.84%, 90.70%, and 97.68% respectively.

**Conclusions**: Our proposed DCNN-based model is able to classify normal and abnormal karyotypes effectively. It has the competence to be used as a predictive tool for abnormal karyotype detection and screening in genetic diagnosis without beforehand feature extraction. We believe our work is meaningful for genetic triage management at a low cost in clinical practice by significantly reducing the diagnostic workload, making up for the lack of clinical experience of doctors, and improving work efficiency and accuracy. 

(GUI_TouchScreen.png)](README.md)


## Prerequisites
### Install the Scikit-learn
This option is only adopted by Python specialist. There are several dependencies necessarily preinstalled in your Python interpreter:

- **Scikit-learn**
```
$ pip install sklearn
 ```

 - **TensorFlow**
```
$ pip install tensorflow
 ```

## License
The MIT License (MIT)

Copyright (c) 2021 Chuan Yang

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Contributor List
- **Qiulei Dong** Ph.D., Professor, School of Artificial Intelligence, University of Chinese Academy of Sciences
