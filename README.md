# QNN MNIST

Here, I elaborated on the software engineering aspects of [this example](https://www.tensorflow.org/quantum/tutorials/mnist) from tensorflow.

## What This Does
By reading the code and the documentation, we can see that this example does the following:
1. Load data
    1.1. Load raw MNIST dataset from keras and visualize it using mathplotlib
    1.2. Filter the DB to only 3s and 6s
    1.3. Downscale the images to 4x4 -> `tf.images.resize()` -> display the results with mathplotlib
    1.4. Remove contradictory examples -> remove images that are labeled as both classes (both 3 and 6) from the main database
    1.5. Convert binary images to cirq circuits -> represent each pixel with a qubit -> 16 qubits per image
2. Quantum neural network
    2.1. Build the model circuit -> a layered circuit where each layer has a 4x4 grid of qubits which hold the data for each pixel of the image. And the circuit has a readout qubit. the classification is based on the expectation of the readout qubit. Farhi et al. propose using two qubit gates, with the readout qubit always acted upon.
    The first layer of the model gets the raw data, and passes the evaluation of each qubit with the readout qubit, to the next layer.
    We can add more layers to improve accuracy. Think of it as a refinement process.
    2.2. Wrap the model-circuit in a tfq-keras model ->
    Build the Keras model with the quantum components. This model is fed the "quantum data", that encodes the classical data. It uses a Parametrized Quantum Circuit layer, tfq.layers.PQC, to train the model circuit on the quantum data.
    To classify these images, Farhi et al. proposed taking the expectation of a readout qubit in a parameterized circuit. The expectation returns a value between 1 and -1.

    The model is a sequential keras model, where the input to each layer’s tensor is given the data-circuit encoded as a `tf.string`. Then , the PQC layer returns the expected value of the readout gate, range [-1,1].
    Next we optimize the model by hinge optimization and using keras Adam() optimizer.
    2.3 Train the quantum model -> Training the model in 3 epochs with 32 parameters on the test  dataset, we get >85% accuracy.

## CNN vs. QNN
After a single epoch, a classical neural network can achieve >98% accuracy on the holdout set.
In an example, a classical neural network is used for the 3-6 classification problem using the entire 28x28 image instead of subsampling the image. This easily converges to nearly 100% accuracy of the test set.
 Higher resolution input and a more powerful model make this problem easy for the CNN. While a classical model of similar power (~32 parameters) trains to a similar accuracy in a fraction of the time. One way or the other, the classical neural network easily outperforms the quantum neural network. For classical data, it is difficult to beat a classical neural network.

## High Level Overview of Example
1. Get data from mnist
2. Create QNN, create a model and train the model on the dataset
3. Now we have a model where given an image of the numbers 3 or 6, it can classify which images are the number 3 and which images are the number 6



## What has been added:
[ ] the original code is unmaintained and does not work, trying to make it work.
[x] added UML use-case diagram for the implementation
[ ] added `checklist.md` as a personal checklist, according to concepts of SE, to go through in such implementations (A scientific demo in the quantum software field)
[ ] define a guideline on how to do future real-world projects similiar to this(how to start, how to implement, how to present)
