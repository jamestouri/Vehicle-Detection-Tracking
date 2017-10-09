
# Vehicle Detection
This repository contains the pipeline to identify other vehicles on highway. The main notebook would be found under Detection.ipynb as a Jupyter Notebook.


## The Project

The steps of this project are the following:

* Perform a Histogram of Oriented Gradients (HOG) feature extraction on a labeled training set of images and train a classifier Linear SVM classifier
* Applied a color transform and append binned color features. 
* Trained a classifer through the data provided Using an Linear SVM
* Ran the Pipeline on the video output 

I first read in all the images that were provided by Udacity, specifically vehicle and non-vehicles.
![](https://github.com/jamestouri/Vehicle-Detection-Tracking/blob/master/car_not_car.png)

### Hog Parameters 
I used the skimage.hog function and expiremented with the different parameters.  Minor tweaks in the Orientation, Pix per Cell and Cells per block went a long way in the accuracy score when training the classifier, however didn't always conclude a successful video output.  

The courses examples had us starting at orient = 11, Pix_per_cell = 16, and Cell_per_block = 2, and ultimately stayed there. 

### Training the HOG Features 

I trained a LinearSVM for the classifier

## Sliding Window Search 

![](https://github.com/jamestouri/Vehicle-Detection-Tracking/blob/master/Vehicleidentified.png)

In the end, I removed the Color_hist function and the spatial_bins function from the Find_cars Sliding Window Search and used the HOG Features by itself.  Although the accuracy score lowered, the video produced much lower False Positives.

### Dealing with False Positives

I dealt with false positives on the video ouput consistently, even after applying the heatmap function to identify the placement of the vehicles. Overall the main difference was through the changing of the colorspace.  Using the YUV colorspace, I found the most success with little to no False Positives


Link to the video: https://youtu.be/FvMVXN81fqA

### Discussion
One of the things I noticed was that some of the advice that was given from Udacity also determined a minor flaw.  As much as I tweaked the spaces of the shapes and squares that identified the Vehicles, if it moved between the location as to where a square is implemented, it didn't draw a box around it. 

This video would have a hard time in stormy weather, or snowy weather where snow would cover half of the car, making it difficult to identify the vehicles. 

I could tweak the squares for a smoother transition, and work on the false positive based on a sanity test, or if there was a box drawn previously, then it would show a square in the video. 






