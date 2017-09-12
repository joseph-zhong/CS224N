# Word2Vec Tutorial: The Skip-Gram Model

- Sept. 2017
- University of Washington, Department of Computer Science Summer 2017

Tutorial Link:
http://mccormickml.com/2016/04/19/word2vec-tutorial-the-skip-gram-model/

> McCormick, C. (2016, April 19). Word2Vec Tutorial - The Skip-Gram Model.
> Retrieved from http://www.mccormickml.com

## Overview 

Tutorial covering the details about Word2Vec with motivation via a skip gram
neural network.

- [Word2Vec](#word2vec)
- [Word2Vec Version 2](#word2vec-version-2)

## Word2Vec Intuition

The basic idea from Word2Vec utilizes a similar trick from
[autoencoders](http://www.deeplearningbook.org/contents/autoencoders.html),
where a neural network is trained to learn the identity function for some input,
under some contrained hidden layer. This hidden layer are the weights which
represent some sort of "compressed" representation. In the context of Word2Vec,
these weights are exactly the "word vectors".

### Skip-Gram Model

With some window size $k$, a sentence, and some known vocabulary of words, the
neural network randomly chooses a word within $k$ words to the left or right
from the middle word in the sentence, and outputs the probability for each word
in the vocabulary that it was the chosen word.

### Training

Utilizing training documents of many sentences, learn $k$-gram pairing of middle
words, and words seen within the window size for each sentence, where we
represent the middle word input as a one-hot vector out of the entire
vocabulary.

Explicitly, the supervised learning problem statement is as follows:

- Input: One-hot vector over the vocabulary, choosing the word
- Label: $k$-gram one-hot vector over the vocabulary for the words taken from
  the sentences in the training documents
- Loss Function: Softmax across the output vector, of the same size as input

### Representation 

Intuitively, after training, the weights of the hidden layers in the neural
network can be represented as a $NxM$ matrix of weights for $N$ rows as the number of words
in the vocabulary, and $M$ columns as the number of neurons, or features each
word.

Additionally, having the input as a one-hot vector effectively "selects" the
corresponding matrix row for the word, hence the representation, "Word2Vec".

## Word2Vec Version 2 

For a vocabulary of 10K words and 300 features each word, the network would need
to learn 3M weights in the hidden layer and output layer each.

Three key innovations are mentioned in the second Word2Vec Paper: ["Distributed
Representations of Words and Phrases and their Compositionality"](https://arxiv.org/pdf/1310.4546.pdf)

- Treat common word pairs, $N$-Grams or phrases as single "words" in the
  vocabulary
- Subsample frequent words to decrease training examples (?)
- Utilize "Negative Sampling": Update a small percentage of model weights

### Subsampling Frequent Words



### Negative Sampling


