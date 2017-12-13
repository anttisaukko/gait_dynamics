Distinguishing healthy population from series of neuro-degenerative diseases using LSTM with Keras
===================

I founded an interesting **neuro-degenerative disease dataset** on [PhysioNet](https://www.physionet.org) that has samples of individuals with Parkinson's, Huntington's and Amyotrophic Lateral Sclerosis (ALS) diseases and healthy control subjects. The data ([doi:10.13026/C27G6C](https://www.physionet.org/physiobank/database/gaitndd/)) was obtained using force-sensitive resistors while the subjects were walking. So, I wanted to see if I could train a machine learning model to classify the healthy from the unhealthy based on their walking pattern. Since the number of subjects and samples was quite limited (n=64), I could not afford having too much features for the model. However, I could split the samples into subsamples and attempt to use those for classification.

Since data is time series data, I thought that a RNN (recurrent neural network) would be a suitable solution and in this case a LSTM (long short-term memory) would work well. In my implementation, I am using a time series of 30 samples with 12 features. This is about 60 seconds of walking. The 12 features are; left and right stride intervals, swing intervals, swing to stride ratio, stance intervals, stance to stride ratio, and double supports, and hope that this won’t be too many features for the limited data set. The dataset contains additional information about the progression of the disease but I left it out for now due to lack of data. 

The implementation details are in the notebook in this repo but for those interested, I used two LSTM’s with 20 and 8 neurons and a dense fully connected 2 neuron network with binary cross validation. I am using 50% dropout on the LSTM layers. I’ve also included a code to classify all four classes with a categorical cross-entropy at the bottom of the notebook. I managed to reach **86.2%** validation accuracy for the healthy/unhealthy, and for all four classes about 70%.


[Gait](https://en.wikipedia.org/wiki/Gait) (in the repo name) means the pattern of movement of the limbs of animals, including humans, during locomotion over a solid substrate.

Have fun,
Antti
