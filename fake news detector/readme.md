# FAKE NEWS DETECTOR
In last few year there is surge of fake news on social media. We aim to solve this big social problem with state of the art techniques of Neural Networks. In this application, we intend to predict the truth/fakeness of a news.
The dataset has been collected from [Kaggle](hhttps://www.kaggle.com/c/fake-news) .


##### The various packages used are:

`numpy`: It is a general-purpose array-processing package which provides a high-performance multidimensional array object, and tools for working with these arrays.

`pandas`: It is an open source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the Python programming language.

`matplotlib.pyplot`: It is a state-based interface to matplotlib. It provides a MATLAB-like way of plotting. pyplot is mainly intended for interactive plots and simple cases of programmatic plot generation.

`keras`: Keras is a high-level neural networks API, written in Python and capable of running on top of TensorFlow, CNTK, or Theano. We have used Tensorflow as backend. 
It allows easy and fast prototyping, supports both convolutional networks and recurrent networks and runs seamlessly on CPU and GPU. For faster training we used Nvidia 940M GPU with 4 GB RAM. 

##### The functions are mentioned below:
`read_csv()`: It is used to import data which is the very first step in the project. </br>
`drop()`: It is used to delete the column *id* and inplace is used to avoid reassigning the value to df. </br>
`head()`: It is used to view the first 5 data from the data set.

After the data set has been imported, convertion of title, author and text to lower case is done using the function `lower()`. The reason behind this is that the user may enter the data in lower as well as upper case so for our simplicity we convert the text to lower case and proceed with the same.


We also remove all the punctuations and digits from the text.
Then tokenization of the text is done using the Keras Tokenizer assuming that the maximum limit of the text is 5000. Tokenization refers to splitting up a large body of text into smaller lines or words.  </br>
Pre padding is done using the Keras preprocessing utils. </br>

###### Training and Test data splitting
Data has been splitted into 75% and 25% for training and testing respectively. </br>

### LSTM (CuDNNLSTM has been used for faster training over GPU)
LSTM is a state of the art technique for Learning from Sequence data. </br>

![LSTM img](https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Peephole_Long_Short-Term_Memory.svg/450px-Peephole_Long_Short-Term_Memory.svg.png)

There are several architectures of LSTM units. A common architecture is composed of a memory cell, an input gate, an output gate and a forget gate.

An LSTM cell takes an input and stores it for some period of time. This is equivalent to applying the identity function **( f(x)=x )**  to the input. Because the derivative of the identity function is constant, when an LSTM network is trained with backpropagation through time, the gradient does not vanish.

The activation function of the LSTM gates is often the logistic function. Intuitively, the input gate controls the extent to which a new value flows into the cell, the forget gate controls the extent to which a value remains in the cell and the output gate controls the extent to which the value in the cell is used to compute the output activation of the LSTM unit.

There are connections into and out of the LSTM gates, a few of which are recurrent. The weights of these connections, which need to be learned during training, determine how the gates operate.


###### Our model has layers as following:
1. `Embedding` : Max feature 5000, embed dimension 128 and the input layer is set as the length of texts  to be fed.
2. `Dropout` : 50%
3. `LSTM layer` : Output shape 196
4. `Drop out` : 50%
5. `Dense` : 2 units

The **softmax** activation unit has been used for prediction with **Adam** as optimizer.

*Achieved 84% training and 90% test accuracy.* </br>

*Now working on the Tensorflow lite to create the app to preditc the Hoax on mobile phones.*




