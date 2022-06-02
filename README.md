Transfer Learning
Its not always efficient for an ML practitioner to write the model from scratch, i.e. Forming a descent Model Architecture, the sizes of the layers, the functions, etc etc. And a very common practice for an Engineer to do, is Transfer Learning. What is it, is that we use a prebuilt model and optimize it and change according to our needs.

For example, if we want to build a flower classifier, we can use a VGG model. The main reason is that instead of making a new model and start to train it from start, we can use a trained model and change some parameters to get the desired answer. The Benefit? Let’s recap what Training a model actually does. We initialize some random weights, more on this later. Perform epochs, feed forwarding and back propagation, and update the weights. So, if we take a prebuilt model, it will have weights are actually are trained for a task, and not just random numbers. Hence, we will be able to easily manipulate them to do our desired work.

You might ask how manipulating them works. Let's talk abit more about what the layers actually do. Let’s say we take face classifying model and its architecture is that it has 3 Hidden Layers. What these Layers are doing, is that the First layer is always looking for easiest patterns, i.e. straight lines, and thats how far the extent of this layers is. The Second layer is then responsible for saving information about somewhat more complex patterns than straight lines, for example, circles or ovals, etc. And the Last layer is the layer which is responsible for the most complex information, i.e. Eyes, Mouth, Nose, etc. What we learn from this, is that the first layers are always the simple ones that have generic information and the more the hidden layers, the more complex patterns the model could get.

Transfer learning involves taking a pre-trained neural network and adapts the neural network to a new, different data set.


Hidden Layer saves Info Example
Okay, then?
The thing is that when we import a prebuilt model, we do not keep all the layers. Let’s discuss types of Transfer Learings.

Training the last layers
In this type, we import a model. Keep some of the first layers and replace the last layers with our newly made Layers. And then we keep the first layers, imported from the model, intact and do not change their weights and just train the layer that we have included. This can cut the time took to train the model on a large scale. Why we train these? Well, the first layers contain the basic information and hence, can be used but in the deep layers is where the complexity rises and the main patterns are present. Hence, we change those layers because we want our model to classify our need, not for what it was previously built. Hence, we train the layers keeping our desired data. And then this practice, trains the model in accordance to our needs.

Find Tuning
Its same as the upper one, it imports a previously trained model and uses its early layers and replaces its deep learning with newly built layers, but the difference here is that we train all the layers, the newly made ones as well as the imported ones. This is for more accurate results. And why we do this over just random weights? Again, these have somewhat working weights and we would just have to change these slightly to get it working and not waste a lot of computing power which it takes in starting the process from randomized weights. There is always some kind of relativity in the previous weights and the newer ones and are, hence, easier to get to.

What are we presented with?
Lets now discuss some various possibilities.

- New Data is small
If the new data set is small and similar to the original training data:

Slice off the end of the neural network.
Add a new fully connected layer that matches the number of classes in the new data set.
Randomize the weights of the new fully connected layer
Freeze all the weights from the pre-trained network.
Train the network to update the weights of the new fully connected layer.
- Small Data Set, Different Data
If the new data set is small and different from the original training data:

Slice off all but some of the pre-trained layers near the beginning of the network.
Add to the remaining pre-trained layers a new fully connected layer that matches the number of classes in the new data set.
Randomize the weights of the new fully connected layer .
Freeze all the weights from the pre-trained network.
Train the network to update the weights of the new fully connected layer.
- Large Data Set, Similar Data
If the new data set is large and similar to the original training data:

Remove the last fully connected layer and replace with a layer matching the number of classes in the new data set.
Randomly initialize the weights in the new fully connected layer.
Initialize the rest of the weights using the pre-trained weights.
Re-train the entire neural network.
- Large Data Set, Different Data
If the new data set is large and different from the original training data:

Remove the last fully connected layer and replace with a layer matching the number of classes in the new data set.
Retrain the network from scratch with randomly initialized weights.
Alternatively, you could just use the same strategy as the “large and similar” data case
And that is it for the topic of Transfer Leanring.

Weight Initialization
In using pretrained models, we have the existing best weights to start from but otherwise, we need to start at least somewhere. And this somewhere, plays an important role in determining the output, the accuracy, of the model. Lets take some examples. All the examples are of a model trained for Fashion MNIST Dataset.

Fashion-MNIST is a dataset of Zalando's article images—consisting of a training set of 60,000 examples and a test set of 10,000 examples. Each example is a 28x28 grayscale image, associated with a label from 10 classes. We intend Fashion-MNIST to serve as a direct drop-in replacement for the original MNIST dataset for benchmarking machine learning algorithms. It shares the same image size and structure of training and testing splits. — From Github

Zero-ed Weights
In this, we initialize all the elements of the Weights Vector to zero, thinking it will benefit to start from neutral and zero is the lower limit of the set of probabilities.

One-ed Weights
In this, we initialize all the elements to one, being the upper limit of teh probability.

The Output?


Weights = 0 & 1
What happened here? We thought these were the neutral values and hence, would be easiest to train. While weights are equal to zero, the gradients become same, think of it this way, all the values are equal, hence, same gradient. Hence, its very hard for the neural network to choose the nodes that need to be changed while performing back propagation. And what about while weights are 1? In this as well, the gradients are same, hence, it’s difficult for the network to choose the nodes that need to be changed. These are very large probabilities and the model has a hard time getting them back to where they should be.

Using consistent weights makes the back propagation to fail.
