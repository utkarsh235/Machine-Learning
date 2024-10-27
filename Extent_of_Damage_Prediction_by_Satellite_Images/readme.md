**High-Level Overview:** This work is about detecting the extent due to Natural Disaster to trees, buildings etc.
Given, Pre and Post Disaster images, our system predicts the percentage of extent of disaster caused.


**Data Collection:** The Data for the Extent of Damage Prediction has been collected from a Already In-built Dataset
known as xbd Dataset. The Dataset can be downloaded from (Kaggle: https://www.kaggle.com/bloodaxe/xview2-damage-assessment) or from (xview2: https://xview2.org/)
The xBD dataset contains 850,736 annotated buildings and spans 45,362 square km of satellite imagery.
There are 9,168 pre-disaster/post-disaster 1024x1024 high-resolution color images. The images capture 19 natural disasters 
from all over the world. The dataset, in general, is highly biased towards the "no damage" class with “no damage” class 
consisting of approximately 60% of the Dataset. The five classes which the dataset contains are ‘no damage’, ‘minor damage’,
‘major damage’, ‘destroyed’ and ‘unclassified’. 

**Data Preprocessing:** Initially a mathematical function had to be built to obtain the regression labels from the classification labels
i.e. to obtain the numerical value of the extent of damage from the 5 classes which were provided in the dataset.
Parallely, The pre disaster images and the post disaster images were read by the OpenCV module as numpy array and
then are converted into 224*224*3 RGB color images. Then the Images are normalised by dividing by 255 and then the 
pre disaster image and the post disaster image are concatenated via the third axis so as to get the best possible 
accuracy prediction by the transfer learning model. All this Preprocessing is done while training the model through 
a Batch-processing pipeline which is built in order to prevent the system from running into RAM Overflow Error. 
The number of images to be processed in one batch has been selected via a variable called batch_size whose optimal
value is determined experimentally.  

**Model Building:** In the system CNN is used for training the model. The DenseNet121 model architecture was used from training
the model. The model is trained using 10 epochs with the batch size of 40 and learning rate of 0.01 along with sigmoid as loss
function. The activation function in the final layer is Sigmoid and a Combination of Max, Average and Global Average Pooling layers
were used as proposed in the original DenseNet121 Architecture. Since the dataset was Unbalanced, we took F1-Score as our evaluation 
metric. Hyperparameter Optimization was also performed on the Model to improve It’s accuracy. Learning rate, Batch Size and Number 
of epochs were tuned for Hyperparameter optimization and then the best possible model was proposed. 

**Model Deployment:** This Disaster management system has been deployed for the end user to classify any image or video into the above mentioned categories on a Localhost Streamlit web application. Under the hood, As soon as a user uploades a file to the Web UI, the code underneath parses the image/video to it's corresponding constituents and the trained Machine learning model makes it's predictions on these smaller subsets and then accumulates the final results by a majority voting algorithm to putput final predictions.
