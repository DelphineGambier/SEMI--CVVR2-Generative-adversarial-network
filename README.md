# EMI--CVVR2-Generative-adversarial-network
The aim of this project is to generate images of apples to build a database that will be used to train other networks using Python and Tensorflow.
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

## I - GAN
## II - Autoencoder
## III - Evaluation 
```python
! python compare_output.py -o out -g gold
```
## IV -  To go further
