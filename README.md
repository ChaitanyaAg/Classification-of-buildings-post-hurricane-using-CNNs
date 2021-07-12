# Univ-AI-Final-Project

Hurricane Iota had 61 total fatalities, and 41 were missing. After a hurricane, damage assessment is vital to the relief helpers and first responders so that resources and help can be planned and allocated appropriately. One way to measure the damage is to detect and quantify the number of damaged buildings, usually done by driving around the affected area and noting down manually. This process can be labor-intensive and time-consuming and not the most efficient method as well.

The project enables the government all over the world to switch from the current inefficient process, driving down to the affected area and identify the relief required area, to capturing the satellite image of the calamity affected area and process through the neural network model to identify where immediate government attention is required.


## Preprocessing: Sharpening
We used Image Enhancer from PILLOW library to sharpen the images.

![image](https://user-images.githubusercontent.com/68959251/103087441-88e28d80-460d-11eb-927a-1e8f3123ba6e.png)

<pre>Top row: Original Images                               Bottom row: Sharpened Images</pre>

## Data Augmentation
We used the following data augmentations:-
* Horizontal flip
* Vertical flip
* Rotation
* Shear
* Zoom
* Width shift
* Height shift

![image](https://user-images.githubusercontent.com/68959251/103088186-014a4e00-4610-11eb-879b-a35ea57a3d5e.png)
*We can see the effect of interpolation near the edges due to data augmentation.*


## Model
We have used transfer learning using the pretrained Resnet50 model.

![image](https://user-images.githubusercontent.com/68959251/103088882-3e174480-4612-11eb-8eff-e98ce6bd2eca.png)
We used two stage training:

* Freeze the convolutional base.
* Unfreeze the last two convolutional layer.

## Training Configuration & Results
We used the following configurations for training:-

![image](https://user-images.githubusercontent.com/68959251/103089303-9b5fc580-4613-11eb-9380-3c79aa841ef1.png)


Following is the loss function plot we obtained. The red dotted line differentiates the **two stage training.**

![image](https://user-images.githubusercontent.com/68959251/103089474-07dac480-4614-11eb-8d4d-d6ac2e0d663b.png)

We got the following results for training:-

![image](https://user-images.githubusercontent.com/68959251/103089692-c1d23080-4614-11eb-846b-cb73b97e3d74.png)

## Visualization
### GradCAM
**For no damage images:-** <br/> We can see the rigid structure of the building after the hurricane with no damage.

![image](https://user-images.githubusercontent.com/68959251/103090030-e4b11480-4615-11eb-8bac-c67886c684d9.png)

**For damage images:-** <br/> We can see that the focus of the model is on water surrounding the buildings.

![image](https://user-images.githubusercontent.com/68959251/103090509-327a4c80-4617-11eb-993a-e8b5150cdd5d.png)

## Predictions
***Test Accuracy – 98%***

![image](https://user-images.githubusercontent.com/68959251/103090866-5c803e80-4618-11eb-9aa7-65c635b917cc.png)
