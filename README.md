# Mini Phyto CNN #
This repository can be used to train and test a small toy Convolutional Neural Network using Jupyter Notebooks.

1. Notebook 1 : How to access .roi files using pyifcb
   - Skills: Loading images into memory, writing files to .png, features extraction(?)
   - profile downloading and accessing files from server versus from mount.
   - Image Cleaning: https://cleanvision.readthedocs.io/en/latest/index.html
2. Notebook 2 : Training a model
3. Notebook 3: Testing a model
4. Notebook 4: Testing a model on roi file


- __[miniPhytoCNN-train.ipynb](./miniPhytoCNN-train.ipynb)__: Pulls down a small training set (6 classes, 400 images each class) and trains two different CNNs (A very simple model and a model that uses ResNet18 structure and weights). Each take about 3-5 minutes to train.
- __[miniPhytoCNN-test.ipynb](./miniPhytoCNN-test.ipynb)__: Loads the trained ResNet18 model, pulls some individual images down from an IFCB Dashboard and runs them through the classifier.



