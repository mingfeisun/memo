### Insights on Keras Framework
* Mingfei Sun
* Created: 2017-11-13
* Updated: 2017-11-15

### model.fit() does not return the best model
Unless you are using ModelCheckpoint callback with save_best_only parameter, model.fit() returns not the best model encountered during the training (i.e. the one with the lowest validation loss or with highest validation accuracy), but rather the model whatever it happens to be at the last epoch (which cannot be counted on to have lowest loss or highest accuracy).

Since many users, esp beginners are unaware of this callback, by default their results are always not the best possible with the current parameters and the accuracy of their network is unnecessarily negatively impacted, despite that a better model has likely been already encountered during the already performed training pass.

``` python
model = Sequential()
...
model.compile(loss='mse', optimizer=opt)
checkpointer = ModelCheckpoint(filepath="weights.hdf5", verbose=1, save_best_only=True)
hist = model.fit(..., callbacks=[checkpointer])
model.load_weights('weights.hdf5')
predicted = model.predict(X_test_mat)
```

[Link](https://github.com/fchollet/keras/issues/2768)

### dropout in Keras
In keras, the dropout is only applied in train phase, see [dropout in training and testing](https://github.com/fchollet/keras/issues/5357). And there is no need to scale the output in testing phase, see [Is the implementation of Dropout correct?](https://github.com/fchollet/keras/issues/3305). 

One example:
``` python
model = Sequential()
model.add(Conv2D(32, kernel_size=(3, 3),
                 activation='relu',
                 input_shape=input_shape))
model.add(Conv2D(64, (3, 3), activation='relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.25))
model.add(Flatten())
model.add(Dense(128, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(num_classes, activation='softmax'))

model.compile(loss=keras.losses.categorical_crossentropy,
              optimizer=keras.optimizers.Adadelta(),
              metrics=['accuracy'])

model.fit(x_train, y_train,
          batch_size=batch_size,
          epochs=epochs,
          verbose=1,
          validation_data=(x_test, y_test))
score = model.evaluate(x_test, y_test, verbose=0)
print('Test loss:', score[0])
print('Test accuracy:', score[1])
```

### Where do I call the BatchNormalization function in Keras?
Just to answer this question in a little more detail, and as Pavel said, Batch Normalization is just another layer, so you can use it as such to create your desired network architecture.

The general use case is to use BN between the linear and non-linear layers in your network, because it normalizes the input to your activation function, so that you're centered in the linear section of the activation function (such as Sigmoid). There's a small discussion of it here

In your case above, this might look like:
``` python
# import BatchNormalization
from keras.layers.normalization import BatchNormalization

# instantiate model
model = Sequential()

# we can think of this chunk as the input layer
model.add(Dense(64, input_dim=14, init='uniform'))
model.add(BatchNormalization())
model.add(Activation('tanh'))
model.add(Dropout(0.5))

# we can think of this chunk as the hidden layer    
model.add(Dense(64, init='uniform'))
model.add(BatchNormalization())
model.add(Activation('tanh'))
model.add(Dropout(0.5))

# we can think of this chunk as the output layer
model.add(Dense(2, init='uniform'))
model.add(BatchNormalization())
model.add(Activation('softmax'))

# setting up the optimization of our weights 
sgd = SGD(lr=0.1, decay=1e-6, momentum=0.9, nesterov=True)
model.compile(loss='binary_crossentropy', optimizer=sgd)

# running the fitting
model.fit(X_train, y_train, nb_epoch=20, batch_size=16, show_accuracy=True, validation_split=0.2, verbose = 2)
```
[Link](https://stackoverflow.com/questions/34716454/where-do-i-call-the-batchnormalization-function-in-keras)
