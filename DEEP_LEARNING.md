# Deep Learning Models

- Cheatsheets on Deep Learning models https://www.globalsqa.com/deep-learning-cheat-sheet/
- Simple explanations of deep learning models https://lilianweng.github.io/lil-log/2017/06/21/an-overview-of-deep-learning.html
- Explanations of when to use lots of the deep learning algorithms https://towardsdatascience.com/6-deep-learning-models-10d20afec175

## Key Concepts

### Feedforward and Backpropagation

There is no pure backpropagation or pure feed-forward neural network.

Backpropagation is algorithm to train (adjust weight) of neural network. Input for backpropagation is output_vector, target_output_vector, output is adjusted_weight_vector. Backpropagation is a training algorithm consisting of 2 steps: 1) Feed forward the values 2) calculate the error and propagate it back to the earlier layers. So to be precise, forward-propagation is part of the backpropagation algorithm but comes before back-propagating.

Feed-forward is algorithm to calculate output vector from input vector. Input for feed-forward is input_vector, output is output_vector.

When you are training neural network, you need to use both algorithms.

## Architectures

### Convolutional Neural Network

- Convolutional neural networks, short for “CNN”, is a type of feed-forward artificial neural networks, in which the connectivity pattern between its neurons is inspired by the organization of the visual cortex system.
- Layers:
    - The primary visual cortex (V1) does edge detection out of the raw visual input from the retina. 
    - The secondary visual cortex (V2), also called prestriate cortex, receives the edge features from V1 and extracts simple visual properties such as orientation, spatial frequency, and color. 
    - The visual area V4 handles more complicated object attributes. All the processed visual features flow into the final logic unit, inferior temporal gyrus (IT), for object recognition.
    - Residual Block: The shortcut between V1 and V4 inspires a special type of CNN with connections between non-adjacent layers
- Specially designed kernels can process images for common purposes like blurring, sharpening, edge detection and many others, fast and efficiently.

- Uses:
    - CNNs were designed for image data and might be the most efficient and flexible model for image classification problems.
    - Image Datasets (including OCR document analysis).
    - Input data is a 2-dimensional field but can be converted to 1-dimensional internally for faster processing.
    - When the model may require great complexity in calculating the output.
- Jargon:
    - Convolution: a process in which feature maps are created out of our input data. A function is then applied to filter maps. 
    - Max-Pooling: enables our CNN to detect an image when presented with modification.
    - Flattening: Flatten the data into an array so CNN can read it.
    - Full Connection: The hidden layer, which also calculates the loss function for our model.


### Recurrent Neural Network

A sequence model is usually designed to transform an input sequence into an output sequence that lives in a different domain.

- Subtypes:
    - “Long-short term memory (LSTM)” cell is smart enough to learn for how long it should memorize the old information, when to forget, when to make use of the new data, and how to combine the old memory with new input.
    - Same as RNN, a sequence-to-sequence model operates on sequential data, but particularly it is commonly used to develop chatbots or personal assistants, both generating meaningful response for input questions.
- When to use:
    - One to one: a single input mapped to a single output. e.g — Image Classification
    - One to many: a single input mapped to a sequence of outputs. e.g — Image captioning (multiple words from a single image)
    - Many to one: A sequence of inputs produces a single output. e.g — Sentiment Analysis (binary output from multiple words)
    - Many to many: A sequence of inputs produces a sequence of outputs. e.g — Video classification (splitting the video into frames and labeling each frame separately)


### Autoencoders

- Different from the previous models, autoencoders are for unsupervised learning. It is designed to learn a low-dimensional representation of a high-dimensional data set, similar to what Principal Components Analysis (PCA) does.

Types of Autoencoders:
- Sparse AutoEncoders: Where the hidden layer is greater than the input layer but a regularization technique is applied to reduce overfitting. Adds a constraint on the loss function, preventing the autoencoder from using all its nodes at a time.
- Denoising AutoEncoders: Another regularization technique in which we take a modified version of our input values with some of our input values turned in to 0 randomly.
- Contractive AutoEncoders: Adds a penalty to the loss function to prevent overfitting and copying of values when the hidden layer is greater than the input layer.
- Stacked AutoEncoders: When you add another hidden layer, you get a stacked autoencoder. It has 2 stages of encoding and 1 stage of decoding.

When to use:
- Dimensionality reduction/Feature detection
- Building powerful recommendation systems (more powerful than BM)
- Encoding features in massive datasets

### Generative Adversarial Network

GAN is able to create new examples after learning through the real data. It is consist of two models competing against each other in a zero-sum game framework.

- In the original GAN paper, GAN was proposed to generate meaningful images after learning from real photos.

It comprises two independent models: the Generator and the Discriminator. 
- The generator produces fake images and sends the output to the discriminator model. It is trying to learn to "cheat" the discriminator.
- The discriminator works like a judge, as it is optimized for identifying the real photos from the fake ones.

### Self-Organizing Maps

Self-Organizing Maps or SOMs work with unsupervised data and usually help with dimensionality reduction (reducing how many random variables you have in your model).

When to use:
- When data provided does not contain an output or a Y column.
- Exploration projects to understand the framework behind a dataset.
- Creative projects (Music/Text/Video produced by AI).
- Dimensionality reduction for feature detection.


### Boltzmann Machines

Boltzmann machines don’t follow a certain direction. All nodes are connected to each other in a circular kind of hyperspace like in the image.
A Boltzmann machine can also generate all parameters of the model, rather than working with fixed input parameters.

When to use:
- When monitoring a system (since the BM will learn to regulate)
- Building a binary recommendation system
- When working with a very specific set of data