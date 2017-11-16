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
