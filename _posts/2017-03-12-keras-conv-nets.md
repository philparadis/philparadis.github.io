---
layout: post
title: Using Keras to implement convolutional nets
date: Sun Mar 12 13:12:20 EDT 2017
published: true
permalink: /:year/:month/:day/:title/
author: Phil
categories: IFT6266-project
---

# Using Keras to implement convolutional nets

See [yesterday's blog post](/2017/03/11/setting-up-keras/) for installing Keras and TensorFlow. Today, we will test our setup on a simple example: a Keras convnet for classifying MNIST handwritten digits. We expect at least 99% accuracy. Then, we will tweak the code a bit to understand better Keras.

## First test: just copy/paste from a good tutorial

We will test our setup with the code from this tutorial: [Keras Tutorial: The Ultimate Beginner’s Guide to Deep Learning in Python](https://elitedatascience.com/keras-tutorial-deep-learning-in-python "Keras Tutorial"). We reproduce the code as one block below for convenience:

(% highlight_python linenos %)
# 3. Import libraries and modules
import numpy as np
np.random.seed(123)  # for reproducibility

from keras.models import Sequential
from keras.layers import Dense, Dropout, Activation, Flatten
from keras.layers import Convolution2D, MaxPooling2D
from keras.utils import np_utils
from keras.datasets import mnist

from keras import backend

backend.set_image_dim_ordering('th')
(% endhighlight %)


```python
# 3. Import libraries and modules
import numpy as np
np.random.seed(123)  # for reproducibility

from keras.models import Sequential
from keras.layers import Dense, Dropout, Activation, Flatten
from keras.layers import Convolution2D, MaxPooling2D
from keras.utils import np_utils
from keras.datasets import mnist

from keras import backend

backend.set_image_dim_ordering('th')

# 4. Load pre-shuffled MNIST data into train and test sets
(X_train, y_train), (X_test, y_test) = mnist.load_data()

# 5. Preprocess input data
X_train = X_train.reshape(X_train.shape[0], 1, 28, 28)
X_test = X_test.reshape(X_test.shape[0], 1, 28, 28)
X_train = X_train.astype('float32')
X_test = X_test.astype('float32')
X_train /= 255
X_test /= 255

# 6. Preprocess class labels
Y_train = np_utils.to_categorical(y_train, 10)
Y_test = np_utils.to_categorical(y_test, 10)

# 7. Define model architecture
model = Sequential()

model.add(Convolution2D(32, 3, 3, activation='relu', input_shape=(1,28,28)))
model.add(Convolution2D(32, 3, 3, activation='relu'))
model.add(MaxPooling2D(pool_size=(2,2)))
model.add(Dropout(0.25))

model.add(Flatten())
model.add(Dense(128, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(10, activation='softmax'))

# 8. Compile model
model.compile(loss='categorical_crossentropy',
                            optimizer='adam',
                            metrics=['accuracy'])

# 9. Fit model on training data
model.fit(X_train, Y_train,
                    batch_size=32, nb_epoch=10, verbose=1)

# 10. Evaluate model on test data
score = model.evaluate(X_test, Y_test, verbose=0)
```

