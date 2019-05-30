
## How to use

### main.py
- использует model.py и data.py
- обучает сеть и создает обработанные картинки в  data/membrane/test
- а так же сохраняет сеть

### dataPrepare.ipynb
генерация датасета на основе малой выборки




- unet/data/membrane/train/label маски картинок (0.png)
- unet/data/membrane/train/image картинки (0.png)
- unet/data/membrane/train/aug/ сгенерированные картинки (image_0_6144147.png) и маски  (mask_0_6144147.png)



- unet/data/membrane/test/  маски картинок (0.png) 
- unet/data/membrane/test/  картинки (0_predict.png)



- ?
- unet/data/membrane/test-volume.tif
- unet/data/membrane/train-labels.tif	
- unet/data/membrane/train-volume.tif



- картинки оформления
- unet/img/0label.png  маска картинки
- unet/img/0test.png картинка
- unet/img/-net-architecture.png архитектура сети





### Results

Use the trained model to do segmentation on test images, the result is statisfactory.

![img/0test.png](img/0test.png)

![img/0label.png](img/0label.png)

### Model

![img/u-net-architecture.png](img/u-net-architecture.png)

This deep neural network is implemented with Keras functional API, which makes it extremely easy to experiment with different interesting architectures.

Output from the network is a 512*512 which represents mask that should be learned. Sigmoid activation function
makes sure that mask pixels are in \[0, 1\] range.

### Training

The model is trained for 5 epochs.

After 5 epochs, calculated accuracy is about 0.97.

Loss function for the training is basically just a binary crossentropy.


## Data

The original dataset is from [isbi challenge](http://brainiac2.mit.edu/isbi_challenge/), and I've downloaded it and done the pre-processing.

You can find it in folder data/membrane.

### Data augmentation

The data for training contains 30 512*512 images, which are far not enough to feed a deep learning neural network. I use a module called ImageDataGenerator in keras.preprocessing.image to do data augmentation.

See dataPrepare.ipynb and data.py for detail.





# Implementation of deep learning framework -- Unet, using Keras

The architecture was inspired by [U-Net: Convolutional Networks for Biomedical Image Segmentation](http://lmb.informatik.uni-freiburg.de/people/ronneber/u-net/).

---

## Overview




