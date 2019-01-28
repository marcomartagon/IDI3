# IDI3 - ITESO - PhD  Engineering Sciences
FLIR Thermal PIC Metadata
Marco Antonio Ramirez Martagon
PhD in Engineering Sciences
ITESO & CONACYT 2019
Guadalajara Jalisco, México

Keywords 
    sklearn, KNeighborsClassifier, neuronal network, PIL, img, crop, python, numpy, jupyter

Abtract
FLIR Thermal cameras create a simple thermal PICS with few EXIF data.
We need insert on the commants EXIF tag extra information as Max and Min Temp, GPS location as latitude, longitude, angle.
Use of sklearn library to train the model with some traing pictures that contain the digits to obtain the predicted label 0,1,2,3,4,5,6,7,8,9,-,. that represent the characters, this will ensure high acuracy to extract the temperature digits from the image, instead of use a generic OCR software.

Note : 
  Python code not obtimised, this process was designed  to teach the entire pricess from collec the pictures, group, use the right model and train the model  on class room.
  
Solution :

It was divided into 6 parts
1) Obtain 500 FLIR imagens and extract the digits in pure Black and White color, the image size is 9 pixels cols by 14 pixels rows, save each image with a random label from 1 to 1,000,000 in BPM format
2) Manual review of each image to label it according the digit contained i.e 1-XXXX.BMP for all the PICs (images) with the digit 1, and use minus-XXXXXX.BMP for all the imagens with a minus sign, use dot-XXXXX.BMP for all the images with dot sign.
   Reduce each class of images to obtain unique imagens representation 
   Save the list of unique images by class using the below notation :  1-UXXX.BMP where the 1 is the class, U means unique, XXX is the sequence 
3) Load each traing image  and ensure keep the right label-class 
   Convert from 2D array to 1D array
   Choose sklearn.neighbors.KNeighborsClassifier(n_neighbors=3) and sklearn.neighbors.KNeighborsRegressor(n_neighbors=3
   Compare which is better obtaing the accuracy  ( just to School Example )
   Save the best model, in this case: sklearn.neighbors.KNeighborsClassifier
4) Load the model sklearn.neighbors.KNeighborsClassifier
   Load a new FLIR thermal image, this should use Raimbow thermal scale
   Predict the labels
   Compare the lables
   Generate a file with the labels, using the same file name of picture but whith extension .LBL, the fle contain 
    MAT:XXX.XX,MIT:-/+XXX,LA:-/+XXXX.XX,LO:-/+XXXX.XX,AG:+/-XXX.XX
    explanation : 
    MAT=Max Temp 
    MIT=Min Temp
    LA = GPS latitude ( we can use the EXIF label, but or my Work I'll apped it into comments EXIF label)
    LO = GPS longitude ( we can use the EXIF label,but or my Work I'll apped it into comments EXIF label )
 4.1) A second code of this phase was designed to make it more efficient 
 
 
 Whow reproduce all the steps
 Ofcourse I can't give you all the 500 themal PIC's, but I'll give you the 500 files with the digit reporesentation 
 Run Part2, Part3 and Part4
 
 
 Files
 
     ./digits
            contain all the pictures 9x14 pixels, labeled manually with the class, 3815 files in BPM format in black and white color
     ./unique_digits
            contain the reduced imagens ( unique imagens ) fomr 3815 to optain the list of images by class
     ./test
            contain 3 FLIR Thermal imagens to test the model 
     ./jupyter
            contain 5 notebooks
                  Part1
                  Part2
                  Part3
                  Part4
                  Part4 Custom Version
                  
            
   
   
   Ref:
   
   [1]Geron, A."Hands-On Machine Learning with Scikit-Learn & TensorFlow",O'REALLY, 2017 USA
   
   [2]EXIF,"Exchangeable Image File Format", online : https://www.sno.phy.queensu.ca/~phil/exiftool/TagNames/EXIF.html
   
   [3]Anaconda IDE. online: https://www.anaconda.com/
   
   [4]Anaconda Scki-learn. online : https://anaconda.org/anaconda/scikit-learn
   
   
   

