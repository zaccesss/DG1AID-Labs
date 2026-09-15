# DG1AID - Week 9 Notes
## Unit 4 - Introduction to Machine Learning
### Aston University - Foundations of AI and Data Science (2025-26)

---

## Lecture Overview

Week 9 begins Unit 4. It introduces Machine Learning:

- What ML is and how it differs from traditional programming
- Types of ML: supervised, unsupervised, reinforcement
- The ML workflow
- Linear regression and classification
- Generalisation, overfitting and underfitting

---

## What is Machine Learning?

### Key Definitions

**Arthur Samuel (1959):** "Field of study that gives computers the ability to learn from data without being explicitly programmed."

**Tom Mitchell (1998):** "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

**Russell and Norvig (2022), quoted verbatim:**
```text
Machine learning: a computer observes some data, builds a model based on the data, and uses the model as both a hypothesis about the world and a piece of software that can solve problems.
```

**Summary:** ML is a subset of AI where systems learn patterns from data to improve performance without being explicitly programmed for every scenario.

### Traditional Programming vs Machine Learning

This is one of the most important conceptual distinctions in the module.

**Traditional Programming:** Inputs + Rules (Program) -> Outputs

- Programmer explicitly writes rules and instructions
- Fixed rules that require manual updates when data changes
- Works best with structured, static data
- Ideal for well-defined, repeatable tasks with clear logic
- Examples: addition, subtraction, spell-checking

**Machine Learning:** Inputs + Outputs (Examples) -> Rules (Model)

- System learns rules automatically from examples
- More adaptable, handles new data through learning
- Can process dynamic and unstructured data
- Suited for complex tasks requiring continuous adaptation
- Examples: grammar checking, speech recognition, image recognition

**Why ML?** Consider handwriting recognition. It is extremely hard to write rules for every possible way a person might write the digit "2". But if you show an ML system thousands of examples of "2"s, it learns the pattern automatically. There may be no rules that are both simple and reliable, we need to combine a very large number of weak patterns.

### What Does it Mean to Learn?

Russell and Norvig (2022): "An agent is learning if it improves its performance after making observations about the world."

When you see 10 examples of spam emails, you learn:

- Patterns (certain words appear frequently)
- Relationships (certain senders are always spam)
- Regularities (spam often has unusual formatting)

**Formal abstraction:** learning is fitting a mapping from inputs to outputs, f: X -> Y, where X is the input features and Y is the output (label, prediction, class).

---

## Types of Machine Learning

### 1. Supervised Learning

**Definition:** the system is shown the correct answers during training. It learns from labelled input-output pairs.

**Formal definition:** we have access to a labelled dataset D = {(x, y)} where x is input and y is the correct label. We learn a function f that maps x to y, hoping to generalise to new unseen inputs.

Examples: spam detection (emails labelled spam/not spam), house price prediction (houses with known prices), medical diagnosis (patient records with known diagnoses), image classification (images labelled with categories).

Task-driven: you tell the system what the correct answer is and it learns to predict it.

### 2. Unsupervised Learning

**Definition:** the system is given data but no correct answers. It must find patterns, structure and groupings on its own.

Examples: customer segmentation (group customers by similar behaviour without pre-defined groups), topic discovery in news articles (find themes automatically), anomaly detection (identify unusual patterns without labelling them as anomalies first).

Data-driven: the system discovers hidden structure in the data.

### 3. Reinforcement Learning

**Definition:** the system learns by trial and error, receiving rewards for good actions and penalties for bad ones. No labelled data, just feedback.

Examples: learning to play chess or Go, self-driving car decision making, robot learning to walk.

Learn from experience: like training a dog with treats.

---

## Supervised ML in Detail

### The Supervised Learning Setup

You have labelled data: D = {(x1, y1), (x2, y2), ..., (xn, yn)}

Input x could be: pixel values, word frequencies, patient measurements, house features. Output y could be: class label (cat/dog), continuous value (price), binary (spam/not spam).

Goal: learn f such that f(x) is approximately equal to y for new unseen inputs.

### Two Types of Supervised Learning

**Classification:** output is a category/class label.

- Binary classification: spam vs not spam, fraud vs legitimate
- Multi-class classification: cat vs dog vs bird
- The model learns a decision boundary that separates classes
- Method: logistic regression

**Regression:** output is a continuous numerical value.

- House price prediction
- Temperature forecasting
- Sales prediction
- The model learns a continuous relationship between input and output
- Method: linear regression

| | Classification | Regression |
|---|---|---|
| Output type | Category/class | Continuous number |
| Example output | "Spam" or "Not spam" | £250,000 |
| Question | "Which class does this belong to?" | "What value will this have?" |
| Examples | Email spam, image recognition | House prices, temperature |

---

## The ML Workflow

### Step 1: Define the Problem

Be specific about what you want to predict. Vague goals cannot be measured.

**Bad:** "Make it easier for users to organise their photos", too vague, no measure of success.

**Good:** "Help a user find all photos matching a specific term such as Paris", clear measure: did the algorithm correctly identify all Paris photos?

Two questions to answer: what problem do I want to solve? What part of the problem can be solved by machine learning?

### Step 2: Construct the Dataset

**Training data:** the data shown to the model during training. The model adjusts its parameters to fit this data. Usually 2/3 (66%) of total data.

**Testing data:** held back from training. Used only to evaluate how well the model generalises to unseen data. Usually 1/3 (33%) of total data.

Requirements for supervised learning data: must be labelled with correct answers (gold-standard labels), must come from reliable sources, must contain relevant features.

### Step 3: Data Pre-processing and Feature Selection

**Data pre-processing:** clean and prepare the data (same as Unit 2): remove duplicates, handle missing values, fix outliers, normalise/standardise values, encode categorical variables.

**Feature selection:** not all available data is relevant to the prediction task. Including irrelevant features can reduce accuracy. Select only the features that contribute meaningfully.

Example, predicting house prices: relevant features are size, number of bedrooms, number of bathrooms, location; irrelevant features are names of current occupants, type of furniture.

### Step 4: Choose a Model

Common ML models include: Decision Trees / Random Forests, Artificial Neural Networks (ANNs), Support Vector Machines (SVMs), Hidden Markov Models (HMMs), Bayesian Networks (BNs), Evolutionary Algorithms (EAs).

There is no a priori way of knowing which model is best for your problem, often you must try several.

### Step 5: Train the Model

Feed training data through the model, calculate predictions, compare to correct answers and adjust model parameters to reduce error. Repeat many times.

**Loss function:** a mathematical measure of how wrong the model's predictions are. Training aims to minimise this.

### Step 6: Test and Evaluate

Use the held-back testing data to evaluate performance on data the model has never seen.

**Classification accuracy:** accuracy = correct predictions / total predictions

**Confusion matrix:** a table summarising correct and incorrect predictions:

```text
                  Predicted Positive   Predicted Negative
Actually Positive   True Positive (TP)   False Negative (FN)
Actually Negative   False Positive (FP)  True Negative (TN)
```

- **True Positive (TP):** correctly predicted spam as spam
- **False Positive (FP):** incorrectly predicted not-spam as spam (Type I error)
- **True Negative (TN):** correctly predicted not-spam as not-spam
- **False Negative (FN):** incorrectly predicted spam as not-spam (Type II error)

### Step 7: Use the Model

Deploy the trained, validated model to make predictions on new unseen data.

---

## Generalisation, Underfitting and Overfitting

Why split data into training and testing? The goal of ML is generalisation, performing well on data the model has never seen before.

**Overfitting:** the model learns the training data too well, including noise and irrelevant details. It performs perfectly on training data but poorly on new data. Like a student who memorises the exact practice exam questions and cannot answer any question that is even slightly different.

**Underfitting:** the model is too simple to capture the patterns in the data. It performs poorly on both training and testing data. Like a student who barely studied and cannot answer any questions.

**Good fit:** the model captures the genuine patterns in the training data and generalises well to new data.

| Problem | Training Performance | Testing Performance | Explanation |
|---|---|---|---|
| Overfitting | Very high | Low | Model memorised noise |
| Underfitting | Low | Low | Model too simple |
| Good fit | High | High | Generalises well |

---

## Linear Regression

The simplest ML model. Fits a straight line to data.

**Equation:** y = mx + c (or in ML notation: y = w1*x + w0)

Where y is the predicted output, x is the input feature, w1 is the weight (slope of the line) and w0 is the bias (intercept).

```text
 y
 |                     *
 |                *
 |           *
 |      *          <- best-fit line, minimises distance to all points
 | *
 +------------------------ x
```

Training adjusts w1 and w0 until the line best fits the training data (minimises prediction error).

**Limitation:** can only model linear relationships. If the true relationship is curved or complex, a straight line will not fit well.

---

## What Comes Next: ANNs

So far, models have been straight lines. But what if the relationship is non-linear?

Artificial Neural Networks (ANNs) are larger, more flexible functions that can model non-linear patterns. They are approximately inspired by the way biological brains work (the connectionist approach).

Deep Learning extends ANNs by creating very deep networks (many layers) with additional features, enabling complex learning at massive scale.

---

## Key Points from Week 9

- ML learns patterns from data
- In many real ML projects, improving the data improves performance more than changing the algorithm
- A model is just a function that maps inputs to outputs
- Learning means reducing error
- Generalisation matters more than training accuracy
- Neural networks and deep learning are natural extensions of these ideas

---

## Key Terms for Week 9

| Term | Definition |
|---|---|
| Machine Learning | Computers learn patterns from data without being explicitly programmed |
| Supervised learning | Learning from labelled examples with correct answers |
| Unsupervised learning | Finding patterns in data without labels |
| Reinforcement learning | Learning from rewards and penalties through trial and error |
| Training data | Data shown to the model during training (usually 66%) |
| Testing data | Data held back to evaluate generalisation (usually 33%) |
| Feature | An input variable used to make predictions |
| Label | The correct output for a training example |
| Model | A function that maps inputs to outputs |
| Loss function | A measure of how wrong the model's predictions are |
| Classification | Predicting a category or class label |
| Regression | Predicting a continuous numerical value |
| Decision boundary | The line (or surface) separating different classes |
| Overfitting | Model performs well on training data but poorly on new data |
| Underfitting | Model too simple to capture patterns, performs poorly on both |
| Generalisation | Performing well on data not seen during training |
| Confusion matrix | Table showing true/false positives and negatives |
| True Positive | Correctly predicted positive |
| False Positive | Incorrectly predicted positive (Type I error) |
| Feature selection | Choosing only the most relevant input variables |
| Linear regression | Fits a straight line to model continuous relationships |
| Logistic regression | Method for learning classification decision boundaries |
