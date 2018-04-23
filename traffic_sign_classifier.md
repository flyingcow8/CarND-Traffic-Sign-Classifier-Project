# **Traffic Sign Recognition** 

## 1. Data Set Summary & Exploration

### Provide a basic summary of the data set

I used pickle module to load traffic
signs data set:

* The size of training set is 34799
* The size of the validation set is 4410
* The size of test set is 12630
* The shape of a traffic sign image is 32*32*3, 32*32 is resolution and 3 means RGB dimensions
* The number of unique classes/labels in the data set is 43

### Visualization of the data set.

Here is an exploratory visualization of the data set. It is a bar chart showing how the data is distributed.

![alt text][image1]

The x-axis represent 43 types of traffic signs. The y-axis represent how many images of each type in the data set.

## 2. Design and Test a Model Architecture

As a first step, I decided to convert the images to grayscale because it can reduce the size of the data set and speed the training time.

Here is an example of a traffic sign image before and after grayscaling.

![alt text][image2]

As a last step, I normalized the image data because it makes the data has mean zero and equal variance. 

My final model consisted of the following layers:

| Layer         		|     Description	        					|
|:---------------------:|:---------------------------------------------:|
| Input         		| 32x32x1 grayscaling image   				    |
| Convolution 5x5     	| 1x1 stride, valid padding, outputs 28x28x6 	|
| RELU					| activation									|
| Max pooling	      	| 2x2 stride,  outputs 14x14x6 				    |
| Convolution 5x5	    | 1x1 stride, valid padding, outputs 10x10x16   |
| RELU					| activation     								|
| Max pooling	      	| 2x2 stride,  outputs 5x5x16 				    |
| Flatten	      	    | 5x5x16 -> 400 	       			            |
| Fully Connected		| 400 -> 120									|
| RELU					| activation									|
| Fully Connected		| 120 -> 84									    |
| RELU					| activation									|
| Fully Connected		| 84 -> 43									    |

To train the model, I used an AWS EC2 GPU instance. I choose LeNet model as my neural network model. My parameters are:
* EPOCHS: 50
* BATCH SIZE: 98
* MU: 0
* SIGMA: 0.1
* LEARNING RATE: 0.001

My final model results were:
* Validation Accuracy = **0.951** 
* Test Accuracy = **0.928**

To get the above results, I adjusted three parameters: EPOCHS, BATCH_SIZE and LEARNING_RATE. This group of parameters maybe not the best one, but it has better results than other groups which I had tried.

## 3. Test a Model on New Images

Here are five German traffic signs that I found on the web:

![alt text][image3] ![alt text][image4] ![alt text][image5] 
![alt text][image6] ![alt text][image7]

The original pictures have different resolutions. I used image editor to process these pictures. All the new pictures are 32*32 resolution and JPEG format.

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| No entry      		| No entry    									| 
| 70km/h limit     		| 70km/h limit 									|
| Road work				| Turn right ahead								|
| Go straight or right 	| Roundabout mandatory					 		|
| Keep right			| Keep right      							    |


The model was able to correctly guess 3 of the 5 traffic signs, which gives an accuracy of 60%. 

To see the detail results, please **visit my** [project code](https://github.com/flyingcow8/CarND-Traffic-Sign-Classifier-Project/blob/master/Traffic_Sign_Classifier.ipynb)


[image1]: ./examples/data_stat.png "Visualization"
[image2]: ./examples/grayscale.jpg "Grayscaling"
[image3]: ./traffic-signs-download/1.jpg "Traffic Sign 1"
[image4]: ./traffic-signs-download/2.jpg "Traffic Sign 2"
[image5]: ./traffic-signs-download/3.jpg "Traffic Sign 3"
[image6]: ./traffic-signs-download/4.jpg "Traffic Sign 4"
[image7]: ./traffic-signs-download/5.jpg "Traffic Sign 5"