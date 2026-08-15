# Neural Network from Scratch – XNOR Logic Gate

## Overview

This project implements a simple feedforward neural network from scratch in Python to learn the **XNOR logic gate**.

The neural network is implemented manually using **NumPy** without using deep learning libraries such as TensorFlow, Keras, or PyTorch.

The implementation covers:

* Forward Propagation
* Sigmoid Activation Function
* Mean Squared Error
* Backpropagation
* Gradient Descent
* Weight and Bias Updates
* Training Loss Visualization
* Final Prediction
* Accuracy Evaluation

---

## Objective

To implement a simple feedforward neural network from scratch in Python without using any in-built deep learning libraries.

The main objective is to understand the internal working of:

* Forward propagation
* Loss calculation
* Backpropagation
* Gradient calculation
* Gradient descent
* Parameter updates

---

## Problem Definition

The **XNOR logic gate** is used as the dataset.

XNOR produces an output of `1` when both input values are the same and produces `0` when the input values are different.

| Input 1 | Input 2 | Output |
| ------: | ------: | -----: |
|       0 |       0 |      1 |
|       0 |       1 |      0 |
|       1 |       0 |      0 |
|       1 |       1 |      1 |

XNOR is a **non-linearly separable problem**, therefore a hidden layer is used in the neural network.

---

## Neural Network Architecture

The network consists of:

* **Input Layer:** 2 neurons
* **Hidden Layer:** 2 neurons
* **Output Layer:** 1 neuron
* **Hidden Layer Activation:** Sigmoid
* **Output Layer Activation:** Sigmoid
* **Loss Function:** Mean Squared Error
* **Optimization:** Gradient Descent

Architecture:

```text
2 Input Neurons
       ↓
2 Hidden Neurons
    Sigmoid
       ↓
1 Output Neuron
    Sigmoid
```

The architecture can be represented as:

```text
2 → 2 → 1
```

---

## Dataset

The XNOR truth table is used as the complete dataset.

```text
[0, 0] → 1
[0, 1] → 0
[1, 0] → 0
[1, 1] → 1
```

There are four input samples and one binary output for each sample.

---

## Activation Function

The Sigmoid activation function is used in both the hidden and output layers.

```text
Sigmoid(x) = 1 / (1 + e^(-x))
```

Its derivative is:

```text
Sigmoid'(x) = Sigmoid(x) × (1 - Sigmoid(x))
```

The derivative is required during backpropagation.

---

## Forward Propagation

During forward propagation, the input values are passed through the network.

### Hidden Layer

```text
Z1 = X · W1 + b1
A1 = Sigmoid(Z1)
```

### Output Layer

```text
Z2 = A1 · W2 + b2
A2 = Sigmoid(Z2)
```

`A2` represents the predicted output of the neural network.

---

## Loss Function

Mean Squared Error is used to calculate the difference between the actual and predicted outputs.

```text
MSE = Mean((Actual - Predicted)²)
```

A lower MSE indicates that the predicted values are closer to the expected values.

---

## Backpropagation

Backpropagation calculates the gradients of the weights and biases.

The error is first calculated at the output layer and then propagated backward to the hidden layer.

The gradients are calculated for:

```text
W1
b1
W2
b2
```

These gradients are then used by gradient descent to update the network parameters.

---

## Gradient Descent

The network parameters are updated using the gradient descent rule:

```text
New Parameter =
Old Parameter - Learning Rate × Gradient
```

The process is repeated for multiple epochs so that the neural network gradually reduces the prediction error.

---

## Initial Parameters

The experiment uses manually supplied initial weights and biases.

```text
W1 =
[[ 0.4 -0.3]
 [ 0.2  0.5]]

b1 =
[[ 0.1 -0.2]]

W2 =
[[ 0.3]
 [-0.4]]

b2 =
[[ 0.1]]
```

These values are updated during training using backpropagation and gradient descent.

---

## Training

The network is trained using:

```text
Epochs = 10000
Learning Rate = 0.5
```

During each epoch:

1. Forward propagation is performed.
2. MSE loss is calculated.
3. Backpropagation calculates the gradients.
4. Gradient descent updates weights and biases.
5. The loss value is stored.

---

## Training Results

The loss decreases during training.

The recorded training results are approximately:

```text
Epoch     0 | Loss: 0.250585
Epoch  1000 | Loss: 0.249700
Epoch  2000 | Loss: 0.228396
Epoch  3000 | Loss: 0.043300
Epoch  4000 | Loss: 0.006202
Epoch  5000 | Loss: 0.003042
Epoch  6000 | Loss: 0.001977
Epoch  7000 | Loss: 0.001452
Epoch  8000 | Loss: 0.001143
Epoch  9000 | Loss: 0.000940
```

Final training loss:

```text
0.000797
```

The decreasing loss demonstrates that the neural network is learning the XNOR relationship.

---

## Evaluation

After training, the final Sigmoid output is converted into binary values using a threshold of `0.5`.

```text
Predicted Output >= 0.5 → 1
Predicted Output < 0.5  → 0
```

The expected XNOR predictions are:

```text
[0, 0] → 1
[0, 1] → 0
[1, 0] → 0
[1, 1] → 1
```

The trained network produces approximately:

```text
[1, 0, 0, 1]
```

Therefore:

```text
Accuracy = 100%
```

on the four XNOR samples.

---

## Final Predicted Probabilities

The final network outputs approximately:

```text
[0, 0] → 0.9717
[0, 1] → 0.0262
[1, 0] → 0.0326
[1, 1] → 0.9748
```

After applying the threshold of `0.5`:

```text
[0, 0] → 1
[0, 1] → 0
[1, 0] → 0
[1, 1] → 1
```

---

## Why a Hidden Layer is Required

XNOR is non-linearly separable.

The positive samples are:

```text
[0, 0]
[1, 1]
```

while the negative samples are:

```text
[0, 1]
[1, 0]
```

A simple linear model cannot correctly separate these two groups.

The hidden layer introduces non-linearity through the Sigmoid activation function, allowing the network to learn the required relationship.

---

## Model Analysis

The model successfully learns the XNOR relationship.

The initial MSE is approximately:

```text
0.250585
```

After training, the MSE decreases to approximately:

```text
0.000797
```

This significant reduction demonstrates that the network parameters were successfully optimized.

The final predictions exactly match the XNOR truth table.

The model therefore achieves 100% accuracy on the four available samples.

However, because the dataset contains only four samples, this accuracy should not be interpreted as evidence of generalization to larger datasets.

---

## Strengths

* Neural network implemented from scratch.
* No TensorFlow, Keras, or PyTorch.
* Forward propagation implemented manually.
* Backpropagation implemented manually.
* Gradient descent implemented manually.
* Training process is visualized.
* Successfully solves a non-linear problem.
* Easy to understand and demonstrate.

---

## Limitations

1. The dataset contains only four samples.
2. Training and evaluation use the same samples.
3. The model has limited complexity.
4. MSE is used instead of binary cross-entropy.
5. Only basic gradient descent is used.
6. No advanced optimization methods are implemented.
7. The manually selected initial parameters may affect training behavior.

---

## Technologies Used

* Python
* NumPy
* Matplotlib
* Google Colab
* Jupyter Notebook
* GitHub

No deep learning framework is used.

---

## How to Run

### 1. Clone or Download the Repository

Download the project or clone the GitHub repository.

### 2. Open the Notebook

Open:

```text
Neural_Network_XNOR.ipynb
```

in Google Colab or Jupyter Notebook.

### 3. Install Required Libraries

```bash
pip install numpy matplotlib
```

### 4. Run All Cells

Run the notebook cells sequentially from beginning to end.

### 5. Observe

The notebook displays:

* Input data
* Expected XNOR outputs
* Initial weights and biases
* Initial predictions
* Initial MSE
* Training progress
* Training loss
* Loss graph
* Final predictions
* Binary predictions
* Accuracy
* Final weights and biases

---

## Project Structure

```text
Neural-Network-XNOR/
│
├── Neural_Network_XNOR.ipynb
├── README.md
└── screenshots/
    ├── training_loss.png
    ├── initial_prediction.png
    └── final_prediction.png
```

---

## Learning Outcome

This experiment demonstrates the internal working of a basic neural network without using high-level deep learning libraries.

The implementation provides an understanding of:

* Input data
* Weights
* Biases
* Weighted sums
* Activation functions
* Forward propagation
* Loss calculation
* Backpropagation
* Gradient calculation
* Gradient descent
* Weight and bias updates
* Prediction
* Accuracy evaluation

---

## Conclusion

A simple feedforward neural network was successfully implemented from scratch using NumPy.

The network uses a `2-2-1` architecture with Sigmoid activation functions and Mean Squared Error loss.

Forward propagation, backpropagation, and gradient descent were implemented manually.

The training loss decreased from approximately `0.250585` to `0.000797`.

The final predictions correctly reproduce the XNOR truth table:

```text
[0, 0] → 1
[0, 1] → 0
[1, 0] → 0
[1, 1] → 1
```

The model achieved 100% accuracy on the four training examples.

This experiment demonstrates how a neural network can learn a non-linear relationship using a hidden layer, activation functions, backpropagation, and gradient descent.

---

## Author

**Name:** Ragav Sharma

**PRN:** 202401110012

**Class:**  AI & ML

**Batch:** A2

**Subject:** Generative AI Lab

---


---

## Declaration

This project has been implemented for the Practice Lab Assignment on Neural Network Implementation from Scratch.

The neural-network calculations are implemented manually using NumPy without using high-level deep learning frameworks such as TensorFlow, Keras, or PyTorch.
