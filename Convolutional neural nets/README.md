*OBJECT CLASSIFIER MODEL*

Classifier is a Keras Sequential model
```python
from keras.model import Sequential
classifier = Sequential()
```
A CNN is with 1 2D-Convolutional layer, 1 MaxPool layer and a flatten layer is built which is further passed on to a ANN having two dense layers with activation of first layer being 'relu' and second being 'sigmoid'.

```python
from keras.layers import Convolution2D
from keras.layers import MaxPooling2D
from keras.layers import Flatten
from keras.layers import Dense

classifier.add(Convolution2D(32,3,3,input_shape=(64,64,3),activation='relu'))

#step 2: Pooling
classifier.add(MaxPooling2D(pool_size=(2,2)))

#step 3:Flattening
classifier.add(Flatten())

#step 4: ANN
classifier.add(Dense(output_dim= 128,activation='relu'))
classifier.add(Dense(output_dim=n,activation='sigmoid'))
```

As it is a classifier we are using Binary cross entropy loss and adam optimizer with evaluation metric being accuracy

```python
#compiling CNN
classifier.compile(optimizer='adam',loss='binary_crossentropy',metrics=['accuracy'])
```

preprocessing the images with the inbuilt keras image data generator
```python
#fitting to training set
from keras.preprocessing.image import ImageDataGenerator
train_datagen = ImageDataGenerator(
        rescale=1./255,
        shear_range=0.2,
        zoom_range=0.2,
        horizontal_flip=True)

test_datagen = ImageDataGenerator(rescale=1./255)

training_set = train_datagen.flow_from_directory(
        'dataset/training_set',
        target_size=(64, 64),
        batch_size=32,
        class_mode='binary')

test_set = test_datagen.flow_from_directory(
        'dataset/test_set',
        target_size=(64, 64),
        batch_size=32,
        class_mode='binary')

classifier.fit_generator(
        training_set,
        steps_per_epoch=8000,
        nb_epoch=25,
        validation_data=test_set,
        nb_val_samples=2000)
```
read the documentation for better unerstanding: https://keras.io/preprocessing/image/

Finally making predictions of the images in the test set.
```python
#Part 3 - Making new/single predictions

import numpy as np
from keras.preprocessing import image
test_image = image.load_img('path',target_size=(64,64))
test_image = image.img_to_array(test_image)
test_image = np.expand_dims(test_image,axis =0)
result = classifier.predict(test_image)
training_set.class_indices
if result[0][0] == 1:
        prediction = 'dog'
else:
        prediction = 'cat'
```
