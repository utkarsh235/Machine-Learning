**High-Level Overview:** This work focuses on building a system which predicts natural disasters from Images/Videos. 
Given Images/Videos of Natural Disaster to the system, the system predicts which disaster has occured.

**Data Collection:** Various Sources were used to collect the data which was relevant for the Disaster Management System.
The sources used to collect the data were Web Scraping, Kaggle, Already Built Existing Datasets and Other Dataset Repositories.
In the proposed system the publicly available dataset from Kaggle is used. Apart from that some of the images from the 
“No-Disaster” class has been collected manually either through web scraping or mixing multiple different datasets which 
contained images of Streets, Cars, Trees etc. The name of the dataset which contained 4 categories is ‘Disaster Images Dataset 
(CNN Model)’. Dataset contains almost 4500 images with 4 types of natural disasters. These natural disasters are Earthquake, 
Cyclone, Flood and Wildfire. Earthquake class has 1350 images, Flood class has 1350 images, Wildfire class has 1350 images 
and Cyclone class has 1350 images. The number of images in the No-Disaster class varied from 2000-3000 images.

**Data Preprocessing:** The Proposed System is valid on Images and videos data. In the proposed system all the images in the
dataset are read through OpenCV module as numpy array and then are converted into 224*224*3 RGB color images. In the final 
step of the preprocessing, The Images are normalised by dividing by 255 so as to get the best possible accuracy prediction by
the transfer learning model. All this Preprocessing is done while training the model through a Batch-processing pipeline which
is built in order to prevent the system from running into RAM Overflow Error. The number of images to be processed in one batch
has been selected via a variable called batch_size whose optimal value is determined experimentally.  
 
**Model Building:** In the system CNN is used for training the model. The Xception-Net model architecture was used from training
the model. The model is trained using 30 epochs with the batch size of 100 and learning rate of 0.01 along with categorical_crossentropy
as loss function. The activation function in the final layer is Softmax and no pooling layers were used in the overall architecture
of the proposed model. Since the dataset was balanced, we took accuracy score as our evaluation metric. Hyperparameter Optimization
was also performed on the Model to improve It’s accuracy. Learning rate, Batch Size and Number of epochs were tuned for Hyperparameter
optimization and then the best possible model was proposed. 
