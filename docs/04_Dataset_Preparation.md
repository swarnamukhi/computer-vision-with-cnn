# Dataset Preparation

## Introduction

Machine Learning models learn from data.

Before training a Convolutional Neural Network (CNN), we must prepare the dataset in a format that TensorFlow can understand.

Dataset preparation involves:

- Downloading the dataset
- Organizing images into folders
- Splitting the data into Training, Validation, and Test sets
- Creating a directory structure that TensorFlow can read efficiently

Without proper dataset preparation, the model cannot be trained.

---

# What is a Dataset?

A dataset is a collection of examples used to train and evaluate a Machine Learning model.

For this project,

our dataset contains two classes.

```

Cat Images

Dog Images

```

Each image has a label.

```

cat.jpg

↓

Cat

```

```

dog.jpg

↓

Dog

```

The model learns the relationship between

Image

↓

Label

---

# Why Do We Need Labels?

A CNN cannot automatically know

"This is a cat."

"This is a dog."

We must provide the correct answer during training.

Example

```

Image

↓

Cat

```

The model compares

Prediction

↓

Actual Label

↓

Calculates Error

↓

Learns

This type of learning is called

**Supervised Learning.**

---

# Why Organize Images into Folders?

TensorFlow can automatically assign labels based on folder names.

Example

```

train/

cats/
cat1.jpg
cat2.jpg

dogs/
dog1.jpg
dog2.jpg

```

TensorFlow understands

```

cats/

↓

Label = Cat

```

```

dogs/

↓

Label = Dog

```

No separate label file is required.

---

# Standard Dataset Structure

Most TensorFlow Computer Vision projects use a directory structure like this.

```

dataset/

train/
cats/
dogs/

validation/
cats/
dogs/

test/
cats/
dogs/

```

Each folder represents one class.

---

# Why Split the Dataset?

A model should not be evaluated using the same images it learned from.

Therefore,

the dataset is divided into three parts.

```

Entire Dataset

↓

Training

↓

Validation

↓

Testing

```

---

# Training Dataset

Purpose

Teach the CNN.

The model updates its weights using these images.

Usually

70–80%

of the data.

---

# Validation Dataset

Purpose

Monitor model performance during training.

The model does NOT learn from these images.

Validation helps detect

- Overfitting
- Underfitting

Usually

10–20%

of the data.

---

# Test Dataset

Purpose

Evaluate the final model.

The test dataset is only used after training is complete.

It measures how well the model performs on completely unseen images.

Usually

10–20%

of the data.

---

# Complete Workflow

```

Entire Dataset

↓

Split

↓

Training
Validation
Testing

↓

CNN Training

↓

Evaluation

↓

Prediction

```

---

# Why Not Train Using All Images?

Suppose the model memorizes every training image.

Training Accuracy

100%

Now someone uploads a new image.

The model fails.

This is called

**Overfitting.**

Keeping separate Validation and Test datasets ensures the model learns patterns instead of memorizing images.

---

# How TensorFlow Reads the Dataset

TensorFlow scans the folders.

Example

```

train/

cats/

dogs/

```

Internally,

it creates something similar to

```

cat1.jpg → Cat

cat2.jpg → Cat

dog1.jpg → Dog

dog2.jpg → Dog

```

The folder names become the class labels.

---

# Industry Perspective

In production,

datasets are usually much larger.

Example

```

Millions of Images

↓

Cloud Storage

↓

Data Pipeline

↓

Preprocessing

↓

Training

```

Even though enterprise datasets are stored differently,

the idea remains the same.

Every image must have a corresponding label.

---

# Common Mistakes

❌ Mixing cat and dog images in one folder.

✔ Create separate folders for each class.

---

❌ Evaluating using training images.

✔ Use a separate Test dataset.

---

❌ Ignoring Validation data.

✔ Always monitor validation performance during training.

---

# Key Takeaways

• A dataset is a collection of labeled examples.

• CNNs learn from labeled data.

• Folder names act as class labels.

• The dataset should be split into Training, Validation, and Test sets.

• Training teaches the model.

• Validation monitors learning.

• Testing evaluates the final model.

---

# Interview Questions

1. What is a dataset?

2. Why do we split the dataset?

3. Difference between Training, Validation, and Test datasets?

4. Why are images organized into folders?

5. How does TensorFlow know which images are cats and which are dogs?

6. What happens if we evaluate using training data?

