# Image Dataset Exploratory Data Analysis (EDA)

## Introduction

Before training a Convolutional Neural Network (CNN), it is important to understand the quality and characteristics of the dataset.

In Machine Learning, this process is called **Exploratory Data Analysis (EDA)**.

Unlike tabular datasets, image datasets require inspection of both:

- Image metadata (size, format, color mode, etc.)
- Pixel-level information (brightness, contrast, etc.)

Performing EDA helps identify potential problems before model training, improving both model performance and data quality.

---

# Why Perform EDA Before CNN Training?

A CNN learns patterns directly from images.

If the dataset contains poor-quality images, duplicate images, inconsistent image sizes, corrupted files, or incorrect labels, the model may learn incorrect patterns.

Image EDA helps engineers answer questions such as:

- Is the dataset balanced?
- Are all images readable?
- Are image formats consistent?
- Do all images have the same color mode?
- Are there duplicate images?
- Are some images unusually bright or dark?
- Do some images have very low contrast?
- Is additional preprocessing required?

Performing EDA before training is considered a best practice in Computer Vision.

---

# Python Libraries Used

This project uses several Python libraries to inspect and analyze the image dataset.

---

# 1. pathlib

## What is pathlib?

`pathlib` is Python's object-oriented library for working with file and directory paths.

Instead of manipulating paths as strings, `pathlib` represents them as **Path objects**, making code cleaner and platform-independent.

---

## Functions Used

### Create a Path

```python
from pathlib import Path

DATASET_PATH = Path("/content/dataset")
```

Creates a Path object representing the dataset location.

---

### Join Paths

```python
DATASET_PATH / "cats"
```

Produces

```text
/content/dataset/cats
```

instead of manually concatenating strings.

---

### Iterate Through Directory

```python
DATASET_PATH.iterdir()
```

Returns an iterator over all files and folders inside the directory.

Used to loop through class folders and image files.

---

### Check Whether an Object is a Directory

```python
folder.is_dir()
```

Returns

```python
True
```

if the object represents a folder.

---

### Get Folder Name

```python
folder.name
```

Returns only

```text
cats
```

instead of the complete path.

---

## Why did we use pathlib?

To navigate the dataset structure in a clean, readable, and platform-independent manner.

---

# 2. Pillow (PIL)

## What is Pillow?

Pillow (Python Imaging Library) is a Python library used to work with digital images.

It allows us to:

- Open images
- Read image metadata
- Resize images
- Crop images
- Rotate images
- Save images
- Convert images into NumPy arrays

---

## Import

```python
from PIL import Image
```

---

## Functions Used

### Open an Image

```python
image = Image.open(image_path)
```

Loads an image from disk into memory.

Returns a **PIL Image object**.

---

### Image Size

```python
image.size
```

Returns

```python
(width, height)
```

Example

```python
(500,374)
```

---

### Image Width

```python
image.width
```

---

### Image Height

```python
image.height
```

---

### Color Mode

```python
image.mode
```

Possible values

- RGB
- RGBA
- L (Grayscale)
- CMYK

---

### Image Format

```python
image.format
```

Possible values

- JPEG
- PNG
- BMP

---

### Convert Image into NumPy Array

```python
image_array = np.array(image)
```

Converts a PIL Image into a NumPy array for numerical computations.

This enables calculations such as

```python
image_array.mean()
image_array.std()
```

---

## Why did we use Pillow?

Before training a CNN, engineers inspect image metadata and pixel values.

Pillow provides a simple and efficient interface for reading this information.

---

# 3. os

## What is os?

`os` is Python's built-in operating system library.

It provides functions for interacting with files and directories.

---

## Function Used

```python
os.path.getsize(image_path)
```

Returns the file size in bytes.

Converted into KB

```python
size_kb = os.path.getsize(image_path) / 1024
```

---

## Why did we use os?

To inspect

- Minimum file size
- Maximum file size
- Average file size

Large files may increase disk I/O and slow down model training.

---

# 4. hashlib

## What is hashlib?

`hashlib` is Python's built-in hashing library.

It generates a unique digital fingerprint (hash) for any input data.

If two files have identical content, they generate the same hash.

---

## Import

```python
import hashlib
```

---

## Function Used

```python
hashlib.sha256(file.read()).hexdigest()
```

### sha256()

Generates a SHA-256 hash object.

### hexdigest()

Returns the hash as a readable hexadecimal string.

Example

```text
8f14e45fceea167a5a36dedd4bea2543...
```

---

## Why did we use hashlib?

To detect **exact duplicate images**.

Instead of comparing millions of pixels, engineers compare hash values.

If two images produce the same SHA-256 hash, they are identical.

---

# 5. shutil

## What is shutil?

`shutil` is Python's high-level file operation library.

It provides functions for copying, moving, and deleting files and directories.

---

## Import

```python
import shutil
```

---

## Function Used

### Move a File

```python
shutil.move(source, destination)
```

Moves a file from one location to another.

Example

```python
shutil.move(
    "dogs/dog_703 (1).jpg",
    "duplicate_images/dog_703 (1).jpg"
)
```

---

## Why did we use shutil?

Instead of permanently deleting duplicate images, we moved them into a backup folder.

This is considered a safer and more professional data-cleaning workflow because duplicate files can be restored if needed.

---

# Summary of Python Libraries

| Library | Purpose in this Project |
|----------|-------------------------|
| pathlib | Navigate dataset folders and files |
| Pillow (PIL) | Read image metadata and pixel information |
| os | Analyze image file sizes |
| hashlib | Detect exact duplicate images |
| shutil | Move duplicate images into a backup folder |

---

## Key Takeaways

- `pathlib` simplifies working with file and folder paths.
- Pillow provides image-processing capabilities required for Computer Vision.
- `os` helps inspect file-level information such as file size.
- `hashlib` generates unique fingerprints for duplicate detection.
- `shutil` enables safe file management during dataset cleaning.

These libraries are commonly used together in Machine Learning and Computer Vision projects before model training begins.
