# Introduction to Computer Vision

## What is Computer Vision?

Computer Vision (CV) is a branch of Artificial Intelligence (AI) that enables computers to acquire, process, analyze, and understand images and videos, allowing them to perform tasks that normally require human vision.

In simple words,

> Computer Vision gives computers the ability to "see" and understand visual information.

For example, humans can easily recognize a cat, a dog, a car, or a person by looking at an image. A computer cannot naturally understand images because it only understands numbers. Computer Vision provides techniques and algorithms that allow computers to interpret those numbers and identify meaningful objects.

---

## Why is Computer Vision a Part of Artificial Intelligence?

Artificial Intelligence aims to build systems capable of performing tasks that normally require human intelligence.

Some examples include:

- Seeing
- Speaking
- Understanding language
- Making decisions
- Learning from experience

Since understanding images is a human intelligence task, Computer Vision is considered a branch of Artificial Intelligence.

---

## Different Approaches to Building AI

Artificial Intelligence is a goal rather than a single algorithm. Different techniques can be used to achieve that goal.

### 1. Rule-Based Systems

In traditional AI, developers manually write rules.

Example:

```
IF fever AND cough
THEN possible flu
```

The computer does not learn; it simply follows predefined rules.

---

### 2. Machine Learning

Instead of writing rules, we provide historical data.

The algorithm learns patterns from the data and uses those patterns to make predictions on unseen data.

Example:

Historical emails

↓

Learn spam patterns

↓

Predict whether a new email is spam

---

### 3. Deep Learning

Deep Learning is a specialized branch of Machine Learning.

Instead of manually selecting features, Deep Learning models automatically learn useful features from large amounts of data.

Deep Learning is built using Artificial Neural Networks (ANNs).

Examples:

- Artificial Neural Networks (ANN)
- Convolutional Neural Networks (CNN)
- Recurrent Neural Networks (RNN)
- Transformers

---

## Where Does Computer Vision Fit?

```
Artificial Intelligence
        │
        ├── Rule-Based Systems
        │
        └── Machine Learning
                │
                └── Deep Learning
                        │
                        ├── ANN
                        ├── CNN
                        ├── Vision Transformer (ViT)
                        └── ...
```

Computer Vision is an application area within AI. Modern Computer Vision often uses Deep Learning models such as CNNs and Vision Transformers to solve visual problems.

---

## Computer Vision vs CNN

Many beginners think Computer Vision and CNN are the same thing.

They are not.

| Computer Vision | CNN |
|-----------------|-----|
| Branch of AI | Deep Learning model |
| Goal is to understand images and videos | Learns visual features from images |
| Includes many techniques | One technique used in Computer Vision |
| Broad field | Specific neural network architecture |

In simple words:

> Computer Vision is the problem domain.

> CNN is one of the tools used to solve Computer Vision problems.

---

## Computer Vision Pipeline

A typical Computer Vision system follows this pipeline:

```
Image

↓

Preprocessing

↓

Feature Learning (CNN)

↓

Classification

↓

Prediction
```

For this project:

```
Cat/Dog Image

↓

Resize

↓

Normalize

↓

CNN

↓

Cat or Dog
```

---

## Applications of Computer Vision

Computer Vision is widely used in industry.

Some common applications include:

- Face Recognition
- Medical Image Analysis
- Autonomous Vehicles
- OCR (Optical Character Recognition)
- Security and Surveillance
- Industrial Defect Detection
- Agriculture
- Satellite Image Analysis

---

## Computer Vision in This Project

This repository focuses on one Computer Vision task:

**Binary Image Classification**

Problem:

Given an image,

predict whether it contains

- Cat
- Dog

To solve this problem we will use:

- TensorFlow
- Keras
- Convolutional Neural Networks (CNN)

---

## Industry Perspective

Computer Vision engineers rarely work directly with raw image files.

A production pipeline usually consists of:

1. Reading images
2. Image preprocessing
3. Data augmentation
4. Feature extraction using deep learning models
5. Model training
6. Evaluation
7. Deployment for real-time predictions

The Cats vs Dogs project follows the same pipeline on a smaller scale, making it an excellent beginner project for learning Computer Vision.

---

## Key Takeaways

- Computer Vision is a branch of Artificial Intelligence.
- Its goal is to enable computers to understand images and videos.
- Computer Vision is a field, not a single algorithm.
- CNN is one of the most popular deep learning models used in Computer Vision.
- Our Cats vs Dogs assignment is a Computer Vision project that uses a CNN for binary image classification.

---

## Interview Questions

### 1. What is Computer Vision?

### 2. Why is Computer Vision considered a branch of AI?

### 3. Is CNN the same as Computer Vision?

### 4. What are some real-world applications of Computer Vision?

### 5. Explain the Computer Vision pipeline.

### 6. Why is the Cats vs Dogs project considered a Computer Vision project?

