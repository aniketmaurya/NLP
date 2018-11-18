# FAKE NEWS DETECTOR
In this application, we intend to predict the truth/ fakeness of a news.

The various packages used are:
`numpy`:It is a general-purpose array-processing package which provides a high-performance multidimensional array object, and tools for working with these arrays.
`pandas`: It is an open source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the Python programming language.
`matplotlib.pyplot`:It is a state-based interface to matplotlib. It provides a MATLAB-like way of plotting. pyplot is mainly intended for interactive plots and simple cases of programmatic plot generation:
`keras`: Keras is a high-level neural networks API, written in Python and capable of running on top of TensorFlow, CNTK, or Theano.
It allows easy and fast prototyping, supports both convolutional networks and recurrent networks and runs seamlessly on CPU and GPU.

The functions are mentioned below:
`read_csv()`: It is used to import data which is the very first step in the project.
`drop()`: It is used to delete the column *id* and inplace is used to avoid reassigning the value to df.
`head()`: It is used to view the first 5 data from the data set.

After the data set has been imported, convertion of title, author and text to lower case is done using the function `lower()`. The reason behind this is that the user may enter the data in lower as well as upper case so for our simplicity we convert the text to lower case and proceed with the same.
We also remove all the punctuations and digits from the text.
Then tokenization of the text is done using the Keras Tokenizer assuming that the maximum limit of the text is 5000. Tokenization refers to splitting up a large body of text into smaller lines or words.  

