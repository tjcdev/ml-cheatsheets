# Models

- Advantage/Disadvantages https://leportella.com/cheatsheet/machine-learning/
- Cheatsheets on Deep Learning models https://www.globalsqa.com/deep-learning-cheat-sheet/
- Simple explanations of deep learning models https://lilianweng.github.io/lil-log/2017/06/21/an-overview-of-deep-learning.html
- Explanations of when to use lots of the deep learning algorithms https://towardsdatascience.com/6-deep-learning-models-10d20afec175

## Classic Models

### Logistic Regression

| Advantages | Disadvantages |
| - | - |
| Simple; Don't have to worry about features being correlated | Deals bad with outliers; |


### Decision Trees

| Advantages | Disadvantages |
| - | - |
| Easy to understand and interpret; Handles outliers well; Doesn't need normalisation or dummy variables | It can overfit; Unstable (small changes in data lead to very different trees); Doesn't support online learning |


### K-Nearest Neighbours

| Advantages | Disadvantages |
| - | - |
| Little training time; Works well with multi-class datasets; Good for unusual data | You need to pick value of k; Neighbors-based methods are known as non-generalizing machine learning methods, since they simply “remember” all of its training data; Not good with highly dimensional data |

### Gaussian Naive Bayes

| Advantages | Disadvantages |
| - | - |
| Highly scalabe; Not sensitive to irrelevant features; Returns a degree of certainty for the answers; | Cannot learn interactions between features |

### SVM

| Advantages | Disadvantages |
| - | - |
| High accuracy; Theoretical gaurantess regarding overfitting; Popular in text classification; | Memory intensive; Hard to interpret; Complicated to run and tune; |

### K-Means

Unsupervised models

| Advantages | Disadvantages |
| - | - |
| Good when you know how many clusters you need; Scales well with lots of samples; | Doesn't handle missing values well; Can't find clusters that aren't circles or spherical |

### Hierarchical Clustering

| Advantages | Disadvantages |
| - | - |
| Resulting hierarchical representation can be very informative; Provides an additional ability to visualize;  | Sensitive to noise and outliers; Computationally intensive O(N^2); |

### Gaussian Mixture Model

| Advantages | Disadvantages |
| - | - |
| Soft-clustering (you can see percentages of cluster participation on each sample); Cluster shape flexibility; | Sensitive to initialization values; Possible to converge to a local optimum; Slow convergence rate; |


## Deep Learning Models

### Convolutional Neural Network

- Convolutional neural networks, short for “CNN”, is a type of feed-forward artificial neural networks, in which the connectivity pattern between its neurons is inspired by the organization of the visual cortex system.
- Layers:
    - The primary visual cortex (V1) does edge detection out of the raw visual input from the retina. 
    - The secondary visual cortex (V2), also called prestriate cortex, receives the edge features from V1 and extracts simple visual properties such as orientation, spatial frequency, and color. 
    - The visual area V4 handles more complicated object attributes. All the processed visual features flow into the final logic unit, inferior temporal gyrus (IT), for object recognition.
    - Residual Block: The shortcut between V1 and V4 inspires a special type of CNN with connections between non-adjacent layers
- Specially designed kernels can process images for common purposes like blurring, sharpening, edge detection and many others, fast and efficiently.
- CNNs were designed for image data and might be the most efficient and flexible model for image classification problems.
- Jargon:
    - Convolution: a process in which feature maps are created out of our input data. A function is then applied to filter maps. 
    - Max-Pooling: enables our CNN to detect an image when presented with modification.
    - Flattening: Flatten the data into an array so CNN can read it.
    - Full Connection: The hidden layer, which also calculates the loss function for our model.
- When to use:
    - Image Datasets (including OCR document analysis).
    - Input data is a 2-dimensional field but can be converted to 1-dimensional internally for faster processing.
    - When the model may require great complexity in calculating the output.

### Recurrent Neural Network

- A sequence model is usually designed to transform an input sequence into an output sequence that lives in a different domain. Recurrent neural network, short for “RNN”, is suitable for this purpose and has shown tremendous improvement in problems like handwriting recognition, speech recognition, and machine translation.
- “Long-short term memory (LSTM)” cell is smart enough to learn for how long it should memorize the old information, when to forget, when to make use of the new data, and how to combine the old memory with new input.
- When to use:
- One to one: a single input mapped to a single output. e.g — Image Classification
- One to many: a single input mapped to a sequence of outputs. e.g — Image captioning (multiple words from a single image)
- Many to one: A sequence of inputs produces a single output. e.g — Sentiment Analysis (binary output from multiple words)
- Many to many: A sequence of inputs produces a sequence of outputs. e.g — Video classification (splitting the video into frames and labeling each frame separately)

### RNN: Sequence to Sequence Model

- Same as RNN, a sequence-to-sequence model operates on sequential data, but particularly it is commonly used to develop chatbots or personal assistants, both generating meaningful response for input questions.


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

### Reinforcement (Deep) Learning 

- RL is a subfield of machine learning which allows machines and software agents to automatically determine the optimal behavior within a given context, with a goal to maximize the long-term performance measured by a given metric.

### Generative Adversarial Network

- GAN is able to create new examples after learning through the real data. It is consist of two models competing against each other in a zero-sum game framework.
- In the original GAN paper, GAN was proposed to generate meaningful images after learning from real photos. It comprises two independent models: the Generator and the Discriminator. The generator produces fake images and sends the output to the discriminator model. The discriminator works like a judge, as it is optimized for identifying the real photos from the fake ones. The generator model is trying hard to cheat the discriminator while the judge is trying hard not to be cheated. This interesting zero-sum game between these two models motivates both to develop their designed skills and improve their functionalities. Eventually, we take the generator model for producing new images.

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