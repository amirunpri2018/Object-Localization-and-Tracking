# Object-Localization-and-Tracking
Compare different methods of tracking

# Disclaimer
This software is published for academic and non-commerical use only.

# Dependencies
Opencv 3.0+,
Tensorflow 1.0+
Python 3.5

# Setup
This code has been tested on Windows 8.1, Windows 10, macOS Sierra

# Methods used
1) Meanshift and Camshift Algorithms
2) Histograms
3) Grabcut Algorithm
4) Convolutional Neural network to predict four corners for the rectangle (CNN based Bounding Box regressor model)
5) Linear regression loss function to train the network.

# Program
## box_find.py 
1) It is used to create a dataset on your own in a small scale to test your model. 
2) The training images must be present in same directory where all the training images are kept. 
3) Then in that directory run
  * `python box_find.py.`
4) Then you will get images one by one, where you should use your mouse to draw boxes on the image. 
5) Then press 'm' to go to next image.
6) The image name , along with the coordinates of the box is written in the text file *dataset.txt*

## bounding_box_regression.py
1) The dataset created in the above process is used in training the model.

### Model Details
 * Input image is resized to 256x256x3 

Type | Dimensions | Comments
--- | --- | ---
Convolutional Layer 1 | 3 filters, each 5x5x3 | Layer output dimension is 128x128x3
Convolutional Layer 2 | 3 filters, each 5x5x3 | Layer output dimension is 64x64x3
Feed Forward layer 1  | 12288 Neurons | 
Feed Forward layer 2  | 4 Neurons | Output layer
 * Then run `python bounding_box_regression.py`

## bboxreg.py
1) The dataset created is trained along with a pre-trained vgg16 model.
2) Weights for the model can be found [here](https://www.cs.toronto.edu/~frossard/vgg16/vgg16_weights.npz)

## grabcut.py
 * This algorithm is used in a hope to classify each pixel to each object.
 * To run this code firstly you must change the image you want to read, by changing this line of code.
 ```python
 cv2.imread("abc.jpg")
 ```
  * The run `python grabcut.py`
  * Then draw a box around the object and wait for the program to highlight the object separately, drawing a contour around it.  

