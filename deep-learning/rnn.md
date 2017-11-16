## Recurrent Neural Network

* Mingfei Sun
* Created: 2017-11-16
* Updated: 2017-11-16

### Optimizing RNN performance
This is part I of a multi-part series detailing some of the techniques we've used here at Baidu's Silicon Valley AI Lab to accelerate the training of recurrent neural networks. This part focuses on GEMM performance. Later entries might focus on how we parallelize across GPUs, working with half precision, efficient GPU CTC calculation, GRU and LSTM implementation tricks…

[Link](http://svail.github.io/rnn_perf/)

### The Unreasonable Effectiveness of Recurrent Neural Networks
There’s something magical about Recurrent Neural Networks (RNNs). I still remember when I trained my first recurrent network for Image Captioning. Within a few dozen minutes of training my first baby model (with rather arbitrarily-chosen hyperparameters) started to generate very nice looking descriptions of images that were on the edge of making sense. Sometimes the ratio of how simple your model is to the quality of the results you get out of it blows past your expectations, and this was one of those times. What made this result so shocking at the time was that the common wisdom was that RNNs were supposed to be difficult to train (with more experience I’ve in fact reached the opposite conclusion). Fast forward about a year: I’m training RNNs all the time and I’ve witnessed their power and robustness many times, and yet their magical outputs still find ways of amusing me. This post is about sharing some of that magic with you. 

[Link](http://karpathy.github.io/2015/05/21/rnn-effectiveness/)


### How to use Different Batch Sizes when Training and Predicting with LSTMs
In this tutorial, you will discover how you can address this problem and even use different batch sizes during training and predicting.

After completing this tutorial, you will know:

* How to design a simple sequence prediction problem and develop an LSTM to learn it.
* How to vary an LSTM configuration for online and batch-based learning and predicting.
* How to vary the batch size used for training from that used for predicting.

[Link](https://machinelearningmastery.com/use-different-batch-sizes-training-predicting-python-keras/)

### Stateful LSTM in Keras
The idea of this post is to provide a brief and clear understanding of the stateful mode, introduced for LSTM models in Keras. If you have ever typed the words lstm and stateful in Keras, you may have seen that a significant proportion of all the issues are related to a misunderstanding of people trying to use this stateful mode. This post attempts to give insight to users on how to use for their applications.

[Link](http://philipperemy.github.io/keras-stateful-lstm/)
