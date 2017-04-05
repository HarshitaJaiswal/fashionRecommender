# **High Level Approach**

## Process Images
1. Use urllib to retrieve images from URLs
2. Each image will have the following naming convention <category-name>_<integer>.jpg (e.g. tribal_00.jpg)
3. We will crop each image to only include pixels within the red border (i.e. just the dress, ignore everything else)
4. Use image augmentation (flips, rotations, ZCA etc.) as feature engineering to ensure a more robust network
5. Create feature matrices and label arrays for the images. Steps to create label array:
    * Split image title string by underscore and set the first item in the resulting list as the label (e.g. tribal_00.jpg > tribal)
    * From Scikit-learn preprocessing use Label Ecoder followed by OHE to transform the labels
6. Split the images into train and test folders

## Train a CNN
1. Use existing architectures like VGG and current state of the art RESNET to train a model
2. Tune parameters and check results on validation set (a subset of train images held out for model tuning)
3. Use tuned model to score test images

## Create a web service which consumes the model
1. Leverage Azure Web App Services to deploy the model
    
