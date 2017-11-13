### Insights on Keras Framework

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
