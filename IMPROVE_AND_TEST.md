# Improve and Test Models

## Links

- Machine Learning performance cheatsheet https://machinelearningmastery.com/machine-learning-performance-improvement-cheat-sheet/
- How to Visualize Filters and Feature Maps in Convolutional Neural Networks https://machinelearningmastery.com/how-to-visualize-filters-and-feature-maps-in-convolutional-neural-networks/
- Contains code for visualising filters and feature maps for deep learning models https://towardsdatascience.com/visualising-filters-and-feature-maps-for-deep-learning-d814e13bd671
- This contains great code for visualising each layer in a model (and what it is looking for) https://towardsdatascience.com/convolutional-neural-network-feature-map-and-filter-visualization-f75012a5a49c
- Contains descriptions of all the different metrics you can use to measure the success of a model https://medium.com/ml-cheat-sheet/machine-learning-evaluation-metrics-b89b8832e275

### Improve Performance with Data

Tactics for improving the performance with data 
- Get more data
- Invent more data (i.e. generate it)
- Clean the data
- Resample the data
- Rescale the data
- Transform the data
- Project your data (into a lower dimensional space)
- Feature selection
- Feature engineering (can you add more features)


### Improve Performance with Algorithms

- Spot Check Linear Algorithms
- Spot Check Nonlinear Algorithms
- Steal from the literature

### Improve Performance with Algorithm Tuning

- Diagnostics (looking at learning curves https://machinelearningmastery.com/how-to-control-neural-network-model-capacity-with-nodes-and-layers/)
- Random search of hyperparameters
- Grid search of hyperparameters 
- Optimize. What parameters can you optimize? Perhaps there are parameters like structure or learning rate than can be tuned using a direct search procedure (like pattern search) or stochastic optimization (like a genetic algorithm).
- Algorithm Extensions. What are common extensions to the algorithm?
- Algorithm Customizations. What customizations can be made to the algorithm for your specific case? Perhaps there are modifications that you can make to the algorithm for your data, from loss function, internal optimization methods to algorithm specific decisions.

### Improve Performance With Ensembles

- Blend Model Predictions. Take the mean or mode from the predictions of multiple well-performing models.
- Blend Data Representations. You may have many different projections of your problem which can be used to train well-performing algorithms, whose predictions can then be combined.
- Correct Predictions. Perhaps you can explicitly correct predictions or use a method like boosting to learn how to correct prediction errors.
- Learn to Combine. This is called stacked generalization or stacking and often works well when the submodels are skillful but in different ways and the aggregator model is a simple linear weighting of the predictions. This process can be repeated multiple layers deep.

### Visualising for Deep Learning

Links:
- https://towardsdatascience.com/visualising-filters-and-feature-maps-for-deep-learning-d814e13bd671
- https://machinelearningmastery.com/how-to-visualize-filters-and-feature-maps-in-convolutional-neural-networks/
- https://towardsdatascience.com/convolutional-neural-network-feature-map-and-filter-visualization-f75012a5a49c

- Contains code for visulising all the filters https://machinelearningmastery.com/how-to-visualize-filters-and-feature-maps-in-convolutional-neural-networks/
- Contains code for visualising feature maps (which are the the images that look like the thing you are trying to detect) https://machinelearningmastery.com/how-to-visualize-filters-and-feature-maps-in-convolutional-neural-networks/
- This contains great code for visualising what each layer is looking for https://towardsdatascience.com/convolutional-neural-network-feature-map-and-filter-visualization-f75012a5a49c