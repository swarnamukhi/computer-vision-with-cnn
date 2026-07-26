# Image Preprocessing

## Introduction

Before an image is given to a Convolutional Neural Network (CNN), it must be preprocessed.

Image preprocessing is the process of transforming raw images into a format suitable for training a deep learning model.

Raw images cannot always be directly used because they may have:

- Different sizes
- Different pixel ranges
- Noise
- Different orientations

Preprocessing makes the dataset consistent and improves the model's learning ability.

---

# Why Do We Need Image Preprocessing?

Imagine you are teaching a child to recognize cats.

One image is

600 × 400

Another image is

1024 × 768

Another image is

300 × 900

Every image has a different size.

If every image is different, learning becomes difficult.

Similarly,

CNNs require all input images to have the same dimensions.

Therefore,

we preprocess the images before training.

---

# Common Image Preprocessing Steps

Most Computer Vision projects include the following preprocessing steps.

```
Read Image

↓

Resize

↓

Normalize

↓

Convert to Tensor

↓

Feed to CNN
```

---

# Step 1 - Reading the Image

TensorFlow reads the image file.

Example

```
cat.jpg

↓

TensorFlow

↓

Tensor
```

At this stage,

the pixel values remain unchanged.

Example

```
[120,210,55]
```

---

# Step 2 - Resize

Images usually have different resolutions.

Example

```
Image 1

600 × 400
```

```
Image 2

1920 × 1080
```

```
Image 3

300 × 300
```

A CNN cannot process images with varying input sizes in the same batch.

Therefore,

all images are resized to a fixed shape.

Example

```
150 × 150 × 3
```

---

# Why Resize?

Resize provides

- Consistent input shape
- Faster computation
- Lower memory usage
- Efficient batch processing

Without resizing,

the CNN architecture would receive inconsistent input dimensions.

---

# Step 3 - Normalize Pixel Values

Original pixel values

```
0 → 255
```

Example

```
[255,120,80]
```

Most deep learning models perform better when input values are small.

Therefore,

pixel values are scaled to

```
0 → 1
```

Example

```
255 / 255 = 1.0

120 / 255 = 0.47

80 / 255 = 0.31
```

---

# Why Normalize?

Normalization

- Makes training more stable
- Helps gradient descent converge faster
- Prevents large input values from dominating learning
- Improves numerical stability

Almost every modern deep learning project normalizes input images.

---

# Step 4 - Convert to Tensor

After preprocessing,

the image is stored as a tensor.

Example

```
(150,150,3)
```

This tensor becomes the input to the CNN.

---

# Complete Preprocessing Pipeline

```
Image File

↓

Read Image

↓

Resize

↓

Normalize

↓

Tensor

↓

CNN
```

---

# What Happens If We Skip Preprocessing?

Without resizing

❌ Different image sizes

↓

CNN cannot process batches correctly.

---

Without normalization

❌ Large pixel values

↓

Slower learning

↓

Unstable optimization

↓

Lower accuracy

---

# Industry Perspective

In production,

image preprocessing is usually separated from the model.

Example

```
User uploads image

↓

Preprocessing Service

↓

Resize

↓

Normalize

↓

Convert to Tensor

↓

Model Server

↓

Prediction
```

This separation makes systems easier to maintain and ensures the same preprocessing is used during both training and inference.

---

# Common Mistakes

❌ Feeding raw images directly to the CNN.

✔ Always preprocess images first.

---

❌ Training with normalized images but predicting with raw images.

✔ Use the same preprocessing pipeline for both training and prediction.

---

❌ Using different image sizes during training.

✔ Resize every image to the same dimensions.

---

# Key Takeaways

• Raw images are not directly used for training.

• Image preprocessing prepares data for CNNs.

• Resize ensures consistent image dimensions.

• Normalize scales pixel values from 0–255 to 0–1.

• Preprocessed images are converted into tensors before being passed to the CNN.

---

# Interview Questions

1. What is image preprocessing?

2. Why do CNNs require fixed-size images?

3. Why do we normalize pixel values?

4. What happens if we skip normalization?

5. What is the preprocessing pipeline in a Computer Vision project?

6. Why should training and inference use the same preprocessing pipeline?
