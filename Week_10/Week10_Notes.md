# DG1AID - Week 10 Notes
## Unit 4 - Introduction to Artificial Neural Networks
### Aston University - Foundations of AI and Data Science (2025-26)

---

## Lecture Overview

Week 10 covers Artificial Neural Networks (ANNs):

- Biological inspiration
- The artificial neuron model
- Activation functions
- Single Layer Perceptrons (SLPs)
- The XOR problem and its significance
- Multi Layer Perceptrons (MLPs)
- Training neural networks (backpropagation)
- Modern neural network architectures

---

## Motivation: Why Neural Networks?

Traditional ML models (like linear/logistic regression) struggle with complex non-linear patterns. They can only draw straight lines (linear decision boundaries).

Neural networks can:

- Automatically learn non-linear transformations
- Scale well with large datasets
- Work well with high-dimensional data (images, audio, language)
- Model almost any complex function

**Linear patterns:** classes can be separated by a straight line. Data points can be summarised by a straight line too.

**Non-linear patterns:** classes cannot be separated by a straight line. Data cannot be summarised by a straight line either. This is where neural networks excel.

---

## Biological Inspiration

Neural networks are loosely inspired by how biological brains work.

**Biological neuron components:**

- **Dendrites:** receive input signals from other neurons
- **Synapses:** connection points between neurons
- **Cell body:** processes the incoming information
- **Axon:** sends output signal to other neurons

The key principle: neurons fire electrical signals. If enough input signals arrive (the total exceeds a threshold), the neuron fires and sends a signal onwards. This is the basis of the artificial neuron.

---

## The Artificial Neuron Model

An artificial neuron is a mathematical model inspired by biological neurons.

```text
  x1 --w1--\
  x2 --w2---(Sigma z = w.x + b)--(activation phi)--> output
  x3 --w3--/
   1  --b--/
```

**Components:**

- **Inputs** (x1, x2, ..., xn): values received from other neurons or raw data
- **Weights** (w1, w2, ..., wn): determine how important each input is. Higher weight means more influence.
- **Bias** (b): an adjustable constant that shifts the activation threshold. Provides a consistent input of 1.
- **Summation** (Sigma): computes the weighted sum of inputs plus bias: z = sum(wi * xi) + b
- **Activation function** (phi): takes the weighted sum z and produces the output

**Mathematical formula:**

```text
z = w1*x1 + w2*x2 + ... + wn*xn + b
output = phi(z)
```

In vector notation: output = phi(w . x + b)

**Spam detection example:**

| Feature | Weight | Meaning |
|---|---|---|
| Contains "free" | Strong positive | Strong indicator of spam |
| Sender known | Negative | Known senders are not spam |
| Contains "urgent" | Positive | Spam often uses urgency |

---

## Activation Functions

Without an activation function, stacking multiple layers of neurons only produces a weighted sum, equivalent to a single linear layer. You can prove mathematically that adding more linear layers without activation functions just collapses to one linear equation.

The activation function introduces non-linearity, allowing the network to learn complex patterns.

### Common Activation Functions

**Step Function (Threshold Function):** everything below threshold maps to 0, everything above threshold maps to 1. Used in the original perceptron. Binary output only.

**Sigmoid:** "squashes" output to between 0 and 1. Smooth continuous mapping. Used in early neural networks. Problem: vanishing gradients in deep networks.

**ReLU (Rectified Linear Unit):** negative inputs map to 0, positive inputs pass through unchanged (linear). Computationally very efficient. Most common activation function in modern deep learning.

```python
def relu(x):
    if x >= 0:
        return x
    else:
        return 0

# Or with NumPy:
# np.maximum(0, x)
```

**Activation function summary:**

| Function | Formula | Used in |
|---|---|---|
| Step | 0 if z < theta, else 1 | Original Perceptron |
| Sigmoid | 1/(1+e^-z) | Early neural networks |
| ReLU | max(0, z) | Modern deep learning |

**Why ReLU dominates modern AI:** it is computationally simple, avoids the vanishing gradient problem of sigmoid and works extremely well in practice.

---

## Single Layer Perceptrons (SLPs)

Developed by Frank Rosenblatt in 1957/58. The first "learning" hardware.

A perceptron is a simple neural network classifier that learns a linear decision boundary.

**Why "single layer"?** there is only one layer of calculations to get from input to output.

**Structure:**

- n inputs: x1, x2, ..., xn
- A weight for each input: w1, w2, ..., wn
- A bias unit: b
- A summation: z = sum(wi * xi) + b
- A step activation function with threshold theta

**Output rule:** y = 0 if z < theta, y = 1 if z >= theta

### Perceptron Learning Algorithm

Goal: adjust weights so the perceptron correctly classifies all training examples (finds the correct linear decision boundary).

**Algorithm:**

1. Initialise all weights (randomly or to 0)
2. For each training instance (x, y_target): compute output y, compute error delta = y_target - y. If correct (delta = 0), do nothing. If wrong, update weights using the update rule.
3. Repeat until it correctly classifies all instances (or max iterations reached)

**Weight update rule:** w_new = w_old + alpha * delta * x

Where alpha is the learning rate (controls how much to adjust weights), delta is the error (y_target - y) and x is the input value.

Conceptual rules: if a positive example is misclassified, increase weights; if a negative example is misclassified, decrease weights.

---

## Logical Operations with SLPs

Perceptrons can learn basic logical operations. This connects directly to Week 3 logic content.

### OR Gate

| x1 | x2 | y_target |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

**Solution:** w1 = 1, w2 = 1, theta = 0.5

Verify:

- Input (0,0): 1x0 + 1x0 = 0 < 0.5, output 0 (correct)
- Input (0,1): 1x0 + 1x1 = 1 >= 0.5, output 1 (correct)
- Input (1,0): 1x1 + 1x0 = 1 >= 0.5, output 1 (correct)
- Input (1,1): 1x1 + 1x1 = 2 >= 0.5, output 1 (correct)

### AND Gate

| x1 | x2 | y_target |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

**Solution:** w1 = 1, w2 = 1, theta = 1.5

Verify:

- Input (0,0): 0 < 1.5, output 0 (correct)
- Input (0,1): 1 < 1.5, output 0 (correct)
- Input (1,0): 1 < 1.5, output 0 (correct)
- Input (1,1): 2 >= 1.5, output 1 (correct)

---

## The XOR Problem - Why It Matters

**XOR truth table:**

| x1 | x2 | y_target |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

**The problem:** XOR is not linearly separable. You cannot draw a single straight line that correctly separates the 0s from the 1s. Whatever boundary you try, at least one point is misclassified.

**Historical significance:**

- Minsky and Papert proved in their 1969 book "Perceptrons" that SLPs cannot solve XOR
- This was a devastating blow to neural network research
- It unintentionally triggered the First AI Winter
- Funding for neural networks dried up for over a decade
- This is why the XOR problem is historically so important

Note: the problem was specifically that SLPs could not solve XOR. As we will see, MLPs can solve XOR.

---

## Multi Layer Perceptrons (MLPs)

The solution to the XOR problem and non-linear patterns.

By adding one or more hidden layers between input and output, networks can learn non-linear decision boundaries.

**Hidden layers:** layers between input and output. Hidden neurons learn intermediate features, they detect patterns and combinations of patterns at increasing levels of abstraction.

**Why MLPs were delayed:** the idea of multiple layers had existed since the 1950s. But there was no efficient algorithm for training them (adjusting all the weights). That changed in 1986.

**Backpropagation (1986):** Rumelhart, Hinton and Williams solved the training problem. Backpropagation efficiently calculates how much each weight contributed to the error and adjusts all weights accordingly.

### MLP Structure

A fully connected feed-forward MLP:

- **Fully connected:** every neuron in layer k is connected to every neuron in layer k-1
- **Feed-forward:** information flows from input to output, never backwards, never in loops

```text
Input layer    Hidden layer    Output layer
   x1  ---\    /-- h1 --\
           \  /          \
   x2  ----(mesh)        (sum) --> output
           /  \          /
   x3  ---/    \-- h2 --/
```

**Layers:**

1. **Input layer:** one neuron per input feature
2. **Hidden layer(s):** one or more layers of neurons that learn intermediate representations
3. **Output layer:** produces the final prediction

### Solving XOR with an MLP

XOR can be decomposed into simpler operations.

**Key insight:** x1 XOR x2 = (x1 AND NOT x2) OR (NOT x1 AND x2)

This requires 3 simpler operations (AND NOT, NOT AND, OR), which can each be solved by individual perceptrons. An MLP with one hidden layer can combine these:

| x1 | x2 | h1 (AND NOT) | h2 (NOT AND) | output (OR) |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 (correct) |
| 0 | 1 | 0 | 1 | 1 (correct) |
| 1 | 0 | 1 | 0 | 1 (correct) |
| 1 | 1 | 0 | 0 | 0 (correct) |

This works. MLPs can solve problems that SLPs cannot.

---

## Training MLPs: The Training Loop

**Forward pass:** send input values through the network, layer by layer, to produce a prediction.

**Compute error (loss):** compare prediction to the correct target. Calculate the loss (how wrong the prediction is).

**Backpropagation:** work backwards through the network, calculating how much each weight contributed to the error. Adjust each weight to reduce the error.

**Gradient descent:** the optimisation method used to adjust weights. Follow the gradient of the loss function downhill to find the minimum error.

**Learning rate (alpha):** controls how much to adjust weights each step. Too high means overshoot and oscillate, too low means converge very slowly.

**Repeat:** do this for all training examples, many times (epochs), until the error is acceptably low.

**MLP training loop:**

1. Forward pass, make a prediction
2. Compute error using a loss function
3. Backpropagation, calculate gradients
4. Gradient descent, adjust weights
5. Repeat until error is acceptable

---

## Modern Neural Network Architectures

The basic MLP has been extended into many specialised architectures:

**Convolutional Neural Networks (CNNs):**

- Designed for image data
- Use convolutional layers that detect local patterns (edges, textures, shapes)
- Each layer learns increasingly complex features: layer 1 detects edges, layer 2 shapes, layer 3 object parts, layer 4 objects
- Applications: image recognition, medical imaging, self-driving cars

**Recurrent Neural Networks (RNNs):**

- Designed for sequential data
- Have loops that allow information to persist across time steps
- Applications: time series prediction, speech recognition, language translation

**Transformers:**

- The architecture behind all modern LLMs (ChatGPT, Claude, Gemini)
- Introduced by Vaswani et al. in 2017 ("Attention is All You Need")
- Uses attention mechanisms to process all tokens in parallel
- Can capture long-range dependencies in text
- Scales extremely well with more data and compute
- Applications: language models, translation, code generation

**Generative Adversarial Networks (GANs):**

- Two networks competing: a generator creates fake data, a discriminator tries to detect fakes
- Generator gets better at fooling the discriminator
- Applications: generating realistic images, video, audio
- Used in deepfake creation (ethical concern from Week 2)

---

## Unit 4 Summary

Key points:

- Neural Networks are capable of dealing with complex non-linear patterns
- The Artificial Neuron Model is inspired by biological neurons
- Single Layer Perceptrons can learn linear classifications but fail on non-linear problems (XOR)
- Multi Layer Perceptrons with hidden layers can deal with complex non-linear patterns
- Training uses backpropagation and gradient descent to adjust weights
- Modern deep learning extends these ideas to very deep networks with billions of parameters

### Connection to Earlier Content

**Week 1:** you learned about backpropagation being invented in 1986 and how it triggered the deep learning revolution. Now you understand why it was so important, it solved the MLP training problem.

**Week 2:** you learned about AlexNet (2012) and Transformers (2017). Now you understand what kind of neural networks these are.

**Week 3:** you learned about logical operations (AND, OR, NOT). Perceptrons literally implement these, SLPs can compute AND and OR but not XOR. This connection to logic is direct.

**Lab II:** you implemented relu(x), a real activation function used in modern deep learning. Every forward pass through a deep neural network applies relu millions of times.

---

## Key Terms for Week 10

| Term | Definition |
|---|---|
| Artificial Neural Network (ANN) | A computational model inspired by biological neurons |
| Neuron | A processing unit that computes a weighted sum and applies an activation function |
| Weight | A parameter determining the importance of each input connection |
| Bias | A constant added to the weighted sum, shifting the activation threshold |
| Activation function | A function applied to the weighted sum to introduce non-linearity |
| Step function | Binary activation, 0 below threshold, 1 above |
| Sigmoid | Smooth activation squashing output to (0,1) |
| ReLU | Rectified Linear Unit, max(0, z). Most common modern activation function |
| Perceptron | A single artificial neuron classifier (Rosenblatt, 1957) |
| Single Layer Perceptron (SLP) | One layer of computation from input to output |
| Linear decision boundary | A straight line separating two classes |
| Linearly separable | Data that can be correctly classified by a straight line |
| XOR problem | A logical operation that cannot be solved by an SLP, triggered the First AI Winter |
| Multi Layer Perceptron (MLP) | Neural network with one or more hidden layers |
| Hidden layer | A layer between input and output that learns intermediate features |
| Fully connected | Every neuron in layer k connects to every neuron in layer k-1 |
| Feed-forward | Information flows only from input to output, no loops |
| Backpropagation | Algorithm for training MLPs, propagates error backwards to adjust weights |
| Gradient descent | Optimisation method that adjusts weights in the direction that reduces error |
| Learning rate | Controls how much weights are adjusted per training step |
| Forward pass | Computing predictions by sending input through the network |
| Loss function | Measures how wrong the model's predictions are |
| Epoch | One complete pass through the entire training dataset |
| CNN | Convolutional Neural Network, designed for image data |
| RNN | Recurrent Neural Network, designed for sequential data |
| Transformer | Architecture using attention mechanisms, powers all modern LLMs |
| GAN | Generative Adversarial Network, two competing networks for generating data |
| Deep learning | ML using very deep multi-layer neural networks |
| Non-linear pattern | A pattern that cannot be represented by a straight line |
