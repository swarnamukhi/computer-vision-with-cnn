# Understanding Class Labels, Sigmoid Output, and Final Prediction

## Step 1: Class Labels are Created by `flow_from_directory()`

When using `flow_from_directory()`, TensorFlow automatically assigns a numerical label to each folder.

```python
train_generator.class_indices
```

Output:

```python
{'cats': 0, 'dogs': 1}
```

Therefore,

```
Cat  → Label 0
Dog  → Label 1
```

> **Important**
>
> The CNN never learns the words **Cat** or **Dog**.
> It only learns the numerical labels **0** and **1**.

---

# Step 2: Final Output Layer

For binary classification we use

```python
Dense(1, activation="sigmoid")
```

The sigmoid activation returns **one probability** between **0 and 1**.

```
Output Range

0 -----------------------------> 1
```

This single probability always represents

```
Probability of Class 1
```

In our dataset,

```
Class 1 = Dog
```

Therefore,

```
Sigmoid Output

↓

Probability(Dog)
```

---

# Step 3: Understanding Sigmoid Output

Suppose the network predicts

```
0.92
```

Interpretation

```
Probability(Dog) = 92%

Probability(Cat) = 8%
```

Since

```
92% > 8%
```

Prediction becomes

```
Dog
```

---

Another example

Network Output

```
0.07
```

Interpretation

```
Probability(Dog) = 7%

Probability(Cat)

= 1 - 0.07

= 93%
```

Therefore

```
Prediction = Cat
```

---

# Step 4: Decision Threshold

TensorFlow converts probability into a class using a threshold.

```
Probability >= 0.5

↓

Predict Class 1
```

```
Probability < 0.5

↓

Predict Class 0
```

Since our labels are

```
Class 0 = Cat

Class 1 = Dog
```

the prediction becomes

```
Probability >= 0.5

↓

Dog
```

```
Probability < 0.5

↓

Cat
```

---

# Internal Flow

```
Image
   │
   ▼
CNN
   │
   ▼
Dense(1)
   │
   ▼
Sigmoid
   │
   ▼
Probability of Class 1 (Dog)
   │
   ▼
Compare with 0.5
   │
   ▼
Return Class
```

---

# Our Debugging Example

We already verified

```python
train_generator.class_indices
```

Output

```python
{'cats':0,'dogs':1}
```

Now we checked one prediction

```
Image 381

Actual = 1

Predicted = 0

Probability = 0.0706
```

Let's understand every value.

---

## Actual = 1

Using

```python
{'cats':0,'dogs':1}
```

```
Actual = 1

↓

Dog
```

So the image is actually

```
🐶 Dog
```

---

## Network Output = 0.0706

Since sigmoid predicts the probability of **Class 1**

```
Probability(Dog)

= 7.06%
```

Therefore

```
Probability(Cat)

= 1 - 0.0706

= 92.94%
```

---

## Threshold Decision

TensorFlow now checks

```
Is

0.0706

>=

0.5 ?
```

Answer

```
No
```

Therefore

```
Return Class 0
```

Using

```python
{'cats':0,'dogs':1}
```

```
Class 0

↓

Cat
```

Final prediction becomes

```
Predicted = Cat
```

---

# Compare Prediction with Ground Truth

Actual

```
Dog
```

Predicted

```
Cat
```

Therefore

```
Wrong Prediction
```

This is why we concluded

> **The model predicted a Dog image as Cat.**

---

# Why did we say it predicted Cat?

We did **not** guess.

We used three facts.

### Fact 1

```python
{'cats':0,'dogs':1}
```

tells us

```
0 = Cat

1 = Dog
```

---

### Fact 2

Sigmoid output

```
0.0706
```

means

```
Probability(Dog)

=

7%
```

---

### Fact 3

```
7%

<

50%
```

Therefore TensorFlow returns

```
Class 0
```

Using the label mapping

```
Class 0 = Cat
```

Hence

```
Predicted = Cat
```

---

# Why was Validation Accuracy 50%?

During validation

```
shuffle=False
```

means images are read in folder order.

Suppose validation contains

```
200 Cats

200 Dogs
```

The generator reads

```
Cats
Cats
Cats
...

Dogs
Dogs
Dogs
```

Suppose the CNN predicts

```
Cat
```

for every image.

Then

### Cat Images

```
Actual = Cat

Predicted = Cat

Correct ✅
```

### Dog Images

```
Actual = Dog

Predicted = Cat

Wrong ❌
```

Total

```
Correct

=

200
```

Total Images

```
400
```

Validation Accuracy

```
200 / 400

=

50%
```

---

# Important Clarification

When we checked

```python
next(validation_generator)
```

the first batch contained only Cats.

That **does not** mean validation accuracy is computed using only that batch.

TensorFlow evaluates **all validation batches** before calculating

```
Validation Accuracy

Validation Loss
```

Therefore

- Cat batches may have high accuracy.
- Dog batches may have low accuracy.

The final validation accuracy is computed **after all 400 validation images have been evaluated.**

---

# Key Takeaways

- `flow_from_directory()` creates the mapping between folder names and numerical labels.
- The CNN learns only numerical labels (0 and 1), not class names.
- Sigmoid outputs the **probability of Class 1**, not the class name.
- In our dataset:
  - Class 0 = Cat
  - Class 1 = Dog
- TensorFlow compares the sigmoid output with the threshold (0.5).
- If the output is below 0.5, the prediction is Class 0 (Cat).
- If the output is above or equal to 0.5, the prediction is Class 1 (Dog).
- We concluded the model predicted Dogs as Cats because:
  - The actual label was **1 (Dog)**.
  - The sigmoid output was about **0.07**, meaning only a 7% probability of Dog.
  - Since **0.07 < 0.5**, TensorFlow predicted **Class 0 (Cat)**.
- Validation accuracy is computed **after evaluating the entire validation dataset**, not after the first validation batch.
