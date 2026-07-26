# Image Representation

## Introduction

Humans see images.

Computers do not.

A computer cannot understand a cat, a dog, or a car directly. It only understands numbers.

The first step in every Computer Vision project is converting an image into numerical data that a machine learning model can process.

This numerical representation of an image is called **Image Representation**.

---

# What is an Image?

For humans,

an image is a photograph.

For a computer,

an image is a collection of pixels arranged in rows and columns.

Every pixel contains numerical information.

Therefore,

> An image is simply a matrix (or tensor) of pixel values.

---

# What is a Pixel?

Pixel stands for

**Picture Element**

A pixel is the smallest unit of a digital image.

Thousands or millions of pixels together form an image.

Example

```
⬜⬜⬜⬜⬜
⬜⬜⬜⬜⬜
⬜⬜⬜⬜⬜
```

Each small square is one pixel.

---

# Pixel Values

A pixel stores intensity information.

For a grayscale image,

```
0
```

means

Black

```
255
```

means

White

Everything between them represents different shades of gray.

```
0 ---------------------- 255

Black      Gray       White
```

---

# Grayscale Images

A grayscale image contains only one color channel.

Each pixel stores only one number.

Example

```
120
180
25
90
```

Image Shape

```
(height, width, 1)
```

Example

```
28 × 28 × 1
```

MNIST uses grayscale images.

---

# RGB Images

Most real-world images are color images.

Instead of one value,

each pixel contains three values.

```
Red

Green

Blue
```

Example

```
[255,120,40]
```

means

```
Red = 255

Green = 120

Blue = 40
```

Every pixel stores three values.

---

# Why RGB?

Different combinations of

Red

Green

Blue

produce millions of colors.

Example

```
[255,0,0]
```

Pure Red

```
[0,255,0]
```

Pure Green

```
[0,0,255]
```

Pure Blue

```
[255,255,255]
```

White

```
[0,0,0]
```

Black

---

# Image Shape

Suppose an image is

```
150 × 150 × 3
```

This means

Height = 150 pixels

Width = 150 pixels

Channels = 3 (RGB)

TensorFlow represents images as

```
(height, width, channels)
```

Example

```
(150,150,3)
```

---

# Why Does a Computer See Numbers?

Suppose we have this image.

🐱

Humans immediately recognize a cat.

The computer does not.

Instead,

TensorFlow reads the image file and converts it into numbers.

Example

```
[
 [ [120,80,30], [255,200,100], ... ],

 [ [90,70,40], [150,120,50], ... ],

 ...
]
```

The computer only processes these numerical values.

---

# Does TensorFlow Generate These Numbers?

No.

This is a very common misconception.

TensorFlow **does not create** the RGB values.

The RGB values are already stored inside the image file.

TensorFlow simply

1. Reads the image file
2. Decodes it
3. Extracts the pixel values
4. Converts them into a tensor

Therefore,

TensorFlow is **reading** image data,

not generating it.

---

# Why Convert Images into Tensors?

Deep Learning models cannot understand image files.

They only understand numerical tensors.

Therefore,

```
cat.jpg

↓

TensorFlow reads image

↓

Tensor

↓

CNN

↓

Learns Features

↓

Prediction
```

Notice something important.

TensorFlow does not learn features.

The CNN learns the features.

TensorFlow only prepares the input.

---

# Why Do We Need Fixed Image Shapes?

Suppose one image is

```
600 × 400 × 3
```

Another image is

```
1024 × 768 × 3
```

A CNN expects every input to have the same dimensions.

Therefore,

before training,

all images are resized to a common size such as

```
150 × 150 × 3
```

or

```
224 × 224 × 3
```

---

# Industry Perspective

In production,

Computer Vision engineers rarely work with image files directly.

The first stage of every pipeline is

```
Image File

↓

Decode

↓

Tensor

↓

Preprocessing

↓

Deep Learning Model
```

Understanding image representation is essential because every Computer Vision model—from CNNs to Vision Transformers—expects numerical tensors as input.

---

# Common Misconceptions

❌ TensorFlow creates RGB values.

✔ TensorFlow reads RGB values already stored in the image.

---

❌ TensorFlow understands images.

✔ TensorFlow converts images into tensors.

The CNN learns image features.

---

❌ A computer sees pictures.

✔ A computer only processes numerical tensors.

---

# Key Takeaways

• An image is a collection of pixels.

• A pixel is the smallest unit of an image.

• RGB images contain three color channels.

• TensorFlow reads pixel values from the image.

• TensorFlow converts images into tensors.

• CNN learns features from tensors.

• Computers never "see" images the way humans do.

---

# Interview Questions

1. What is a pixel?

2. How does a computer represent an image?

3. Why are RGB images represented as three channels?

4. Does TensorFlow generate RGB values?

5. Why are images converted into tensors?

6. What does the shape (150,150,3) represent?

7. Who learns image features, TensorFlow or CNN?

