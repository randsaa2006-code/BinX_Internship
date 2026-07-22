# Day 3 — NumPy: Numerical Computing 🔢

## Overview

This project explores the fundamentals of **NumPy** for numerical computing and array manipulation.

The goal is to understand how to create and manipulate arrays, perform mathematical operations efficiently, and apply important concepts such as **vectorization, boolean masking, and broadcasting**.

NumPy is the foundation of the Python data science ecosystem and is widely used in **Artificial Intelligence and Machine Learning workflows** because many libraries such as Pandas, Scikit-learn, TensorFlow, and PyTorch are built on top of it.

---

## Learning Objectives 🎯

By the end of this notebook, I learned how to:

- Create NumPy arrays using different methods.
- Understand array properties such as shape, dimensions, and data types.
- Access and modify elements using indexing and slicing.
- Work with 1D and 2D arrays.
- Apply boolean masking to filter data.
- Perform vectorized operations without using traditional loops.
- Understand and apply broadcasting between arrays with compatible shapes.

---

## Topics Covered 📚

### 1. Why NumPy?

Explored why NumPy is an essential library for numerical computing.

Learned that:

- NumPy arrays (`ndarray`) store data efficiently.
- Arrays are faster than Python lists because operations are optimized using lower-level implementations.
- NumPy provides the foundation for many AI and Machine Learning libraries.

---

### 2. Creating NumPy Arrays

Learned different ways to create arrays using NumPy:

Creating arrays from Python lists:

```python
np.array()
```

Creating arrays filled with zeros and ones:

```python
np.zeros()
np.ones()
```

Generating sequences:

```python
np.arange()
np.linspace()
```

Creating random arrays:

```python
np.random.rand()
```

These methods are useful for generating and preparing numerical data for analysis and modeling.

---

### 3. Array Attributes, Indexing and Slicing

Learned how to inspect NumPy arrays using:

```python
array.shape
array.dtype
array.ndim
```

Practiced accessing elements from arrays.

For 1D arrays:

```python
array[index]
```

For 2D arrays:

```python
array[row, column]
```

Applied slicing techniques to extract specific rows, columns, and sections from arrays.

Examples:

```python
array[:, 1]
```

Selects all rows from the second column.

```python
array[1, :]
```

Selects the entire second row.

---

### 4. Vectorized Operations

Learned how NumPy performs operations on entire arrays without using explicit loops.

Applied operations such as:

```python
array * 2
array + array
array.mean()
```

Benefits of vectorization:

- Faster execution.
- Cleaner and more readable code.
- Efficient processing of large numerical datasets.

---

### 5. Boolean Masking

Learned how to filter array values based on conditions.

Example:

```python
array[array > value]
```

Used boolean masks to select only the elements that satisfy specific conditions.

This technique is useful for filtering and analyzing numerical data.

---

### 6. Broadcasting

Learned how NumPy allows operations between arrays with different but compatible shapes.

Example:

```python
matrix + row
```

Broadcasting allows a smaller array to be automatically expanded across a larger array without manually copying data.

This concept is important for efficient numerical computations in Machine Learning.

---

## Hands-On Lab 🧪

### Step 1: Creating and Inspecting Arrays

Created a 2D array with shape `(4, 4)` containing values from 1 to 16.

Checked:

- Array shape.
- Data type (`dtype`).

---

### Step 2: Array Slicing

Used slicing operations to extract:

- The second column.
- The last row.

This helped practice accessing specific parts of multidimensional arrays.

---

### Step 3: Boolean Masking

Calculated the array mean and used a boolean mask to select values greater than the mean.

Example:

```python
array[array > array.mean()]
```

---

### Step 4: Broadcasting

Added a 1D row array to every row of a 2D array using broadcasting.

Verified the output manually to understand how NumPy applies operations across dimensions.

---

## Tools Used 🛠️

- Python 🐍
- NumPy
- Jupyter Notebook

---

## Summary 📌

During this project, I learned the fundamentals of **NumPy and numerical computing in Python**. I gained practical experience in creating arrays, inspecting their properties, and performing different operations on one-dimensional and multi-dimensional data.

I practiced creating arrays using different NumPy functions such as `array()`, `zeros()`, `ones()`, `arange()`, `linspace()`, and random array generation methods. I also learned how to examine array characteristics using attributes such as shape, dimensions, and data types.

I worked with indexing and slicing techniques to access specific elements, rows, and columns from arrays. Additionally, I learned how boolean masking can be used to filter numerical data based on certain conditions.

A major focus of this project was understanding **vectorization and broadcasting**. I learned how NumPy performs operations efficiently on entire arrays without relying on Python loops, and how broadcasting allows operations between arrays with compatible shapes.

Through this hands-on practice, I developed a stronger understanding of NumPy as a fundamental tool for data processing and as a core component of the Artificial Intelligence and Machine Learning ecosystem.
