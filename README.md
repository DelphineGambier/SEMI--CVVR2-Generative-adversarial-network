# EMI--CVVR2-Generative-adversarial-network
The aim of this project is to generate images of apples to build two databases, a database of good apples and an other database of dammaged apples, that will be used to train other networks using Python and Tensorflow.

![Database1](/Ressources/database1.JPG) ![DataBase2](/Ressources/database2.JPG)
## 0 - Requierement 
For this project you need to use [Google Colaboratory](https://colab.research.google.com/notebooks/intro.ipynb) to run the code. 
You also need the following libraries and versions (some of them can be already installed in google colaboratory or will be installed directly by running the notebooks) :
```
numpy==1.19.5
matplotlib==3.2.2
scipy==1.4.1
sklearn == 0.22.2.post1
scikit_image==0.16.2
skimage==0.0
keras==2.4.3
keras_nightly==2.5.0.dev2021032900
tensorflow_datasets == 4.0.1
tensorflow == 2.5.0
pillow == 7.1.2
opencv_contrib_python==4.1.2.30
IPython == 5.5.0
```
This project requires pix2pix model for GAN avalable [here](https://github.com/tensorflow/examples.git) by installing `tensorflow_examples` with :
```python
! pip install -q git+https://github.com/tensorflow/examples.git
```

Download the datasets used [here](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/tree/main/Datasets).  
*(You can also use your own images datasets)*

## I - Generative Adversarial Networks
### 1 - Apple Generator
This GAN is a DCGAN that have to generate good apple images to feed the first database.
- Data :
To train the Apple Generator use the [Clean_apple.zip](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/blob/main/Datasets/Clean_apple-20210701T103559Z-001.zip) as training data.
- Training :
To train the Apple Generator run the [Apple_Generator.ipynb](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/blob/main/1-GANs/Apple_Generator.ipynb) Notebook.
- Results : 
Images obtained after training  :

![Results 1](/Ressources/results1.png)

*Note : this GAN is not functional but is published to find ways to improve it so the results are not the expected results*

### 2 - Clean apples to dammaged apples
The idea was to turn the clean apple aimages obtained with the first GAN into dammaged apple images in order to feed the second database. For this we compute a cyclegan based on the pix2pix model.
- Data :
To train the Clean to Dammaged GAN use the [Clean_apple.zip](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/blob/main/Datasets/Clean_apple-20210701T103559Z-001.zip) for the good apples and [Dammaged_apple.zip](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/blob/main/Datasets/Dammaged_apple-20210701T103602Z-001.zip) for the dammaged ones.
- Training :
To train the Clean to Dammaged GAN run the [Clean_to_dammaged_apples.ipynb](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/blob/main/1-GANs/Clean_to_dammaged_apples.ipynb) Notebook.
- Results : 

![Results 2](/Ressources/results2.png)

We can see that the GAN turn a good red apple in yellow and green.

## II - Autoencoders
We looked for a solution to the Apple Generator GAN and found that the Autoencoder could be an alternative to this GAN.
- Data : 
To train the Autoencoders use the [Autoencoder_Apples.zip](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/blob/main/Datasets/Autoencoder_Apples-20210701T103555Z-001.zip).
### 1 - Gray autoencoder
The first version of the autoencoder is a grayscale autoencoder that encode apple images.
- Training : 
To train the Gray Autoencoder run the [Gray_Autoencoder.ipynb](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/blob/main/2-Autoencoders/Gray_Autoencoder.ipynb) Notebook.
- Results : 

![Results 3](/Ressources/results3.png)

### 2 - RGB autoencoder
- Training :
To train the RGB Autoencoder run the [RGB_Autoencoder.ipynb](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/blob/main/2-Autoencoders/RGB_Autoencoder.ipynb) Notebook.
- Results : 

![Results R](/Ressources/resultsr.png)
![Results G](/Ressources/resultsg.png)
![Results B](/Ressources/resultsb.png)

![Results 4](/Ressources/results4.png)

## III - Evaluation 
To evaluate the models we use the [FID](https://en.wikipedia.org/wiki/Fr%C3%A9chet_inception_distance) (Fréchet inception distance) : the FID is the performance measure used to evaluate the quality of images created by a generative model. 

![FID](/Ressources/FID.jpg)

Find the compute FID in [3-Evaluation](https://github.com/DelphineGambier/EMI--CVVR2-Generative-adversarial-network/tree/main/3-Evaluation).
To calculate de FID you juste have to drag and drop the python files in Google Colaboratory : 

![Evaluation Files](/Ressources/eval_files.png) 

Then create two directories : 'gold' and 'out'
- import your training images (originals) in 'gold' directory
- import your result images in 'out' directory 

**Warning :** There must be the same number of images in both folders. 

Get the FID by entering the following command in Google Colaboratory :
```python
! python compare_output.py -o out -g gold
```
## IV -  To go further
If you want to go deeper into the subject, here are some links to other projects about GANs (but they use Pytorch instead of Tensorflow) :
- GAN that generates foreground and background separately : https://github.com/jwyang/lr-gan.pytorch
- GAN that generates several objects in one image : https://github.com/tohinz/multiple-objects-gan
- GAN that generates an image from coordinates : https://github.com/bioinf-jku/TTUR
