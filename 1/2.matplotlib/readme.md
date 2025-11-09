# Matplotlib — Detailed documentation for the uploaded notebook (`matplotlib.ipynb`)

> Purpose
> This document explains every cell, every code snippet, the outputs and expected behavior of the uploaded notebook. The style follows the structure and clarity of official documentation: short summary, API / code, parameter explanation, examples, expected outputs and notes.

---

## Table of contents

1. Overview
2. Requirements / installation
3. Imports used in the notebook
4. Data preparation (numpy arrays)
5. Printing arrays (console output)
6. Line plots

   * Single line
   * Multiple lines
   * Line/marker styles
   * Titles and axis labels
   * Overlaying multiple plots (sin/cos)
7. Parabola example
8. Bar chart
9. Pie chart
10. Scatter plot (2D)
11. 3D scatter plot
12. Typical Matplotlib workflow summary
13. Appendix — full notebook code listing (cells & outputs)

---

# 1. Overview

This notebook demonstrates common Matplotlib features using NumPy-generated data:

* creating numeric arrays with `numpy`
* visualizing data with `matplotlib.pyplot` (`plt`)
* basic plot types: line, bar, pie, scatter, 3D scatter
* basic plot styling: labels, title, markers, colors
* using `Figure` and `Axes` objects for bar/pie/axes control

Each example shown below contains the notebook code, a short line-by-line explanation, and the observed/expected output.

---

# 2. Requirements / installation

The notebook uses:

* Python 3.x
* `numpy`
* `matplotlib` (typically >= 3.0, but any recent Matplotlib will work)

Install with `pip` if missing:

```bash
pip install numpy matplotlib
```

---

# 3. Imports used in the notebook

Notebook cells:

```python
# importing
import matplotlib.pyplot as plt

# import numpy to get data for our plots
import numpy as np
```

**Explanation**

* `matplotlib.pyplot` (`plt`) — stateful plotting interface (recommended for quick/imperative plotting).
* `numpy` (`np`) — used to create numerical arrays (e.g., `linspace`, `sin`, `cos`, random).

---

# 4. Data preparation (NumPy arrays)

Notebook code:

```python
x = np.linspace(0, 10, 100)
y = np.sin(x)
z = np.cos(x)
```

**Explanation**

* `np.linspace(0, 10, 100)` creates 100 evenly spaced values from 0 to 10 inclusive. This is a common way to create an x-axis vector for plotting smooth curves.
* `y = np.sin(x)` and `z = np.cos(x)` evaluate sine and cosine elementwise — they return NumPy arrays with the same shape as `x`.

**Why use `linspace`?**
`linspace` is ideal when you want a fixed number of sample points over an interval (better than `arange` for exact endpoint inclusion).

---

# 5. Printing arrays (console output)

Notebook cells:

```python
print(x)
print(y)
print(z)
```

**Expected output (truncated)**

Because these are 100-element arrays, the notebook output was the truncated array representation typical for NumPy:

Example `print(x)` output (truncated):

```
[ 0.          0.1010101   0.2020202   0.3030303   ... 9.7979798   9.8989899  10.        ]
```

Example `print(y)` output (truncated):

```
[ 0.          0.10083842  0.20064886  ... -0.0205576   0.0803643   0.18046693 ... ]
```

Example `print(z)` output (truncated):

```
[ 1.          0.99490282  0.97966323 ... -0.96318398 -0.93116473 -0.88965286 ... ]
```

**Notes**

* NumPy prints long arrays with `...` in the middle by default to keep output concise.
* If you want the full array printed, use `np.set_printoptions(threshold=...)` (not used in the notebook).

---

# 6. Line plots

The notebook demonstrates several line plotting examples. Key points for `plt.plot`:

* `plt.plot(x, y)` draws a line connecting `(x[i], y[i])`.
* `plt.show()` displays the figure in interactive/IPython environments or opens a window when run as a script.

### 6.1 Single sine wave

Code:

```python
# sine wave
plt.plot(x, y)
plt.show()
```

**Explanation**

* Draws a line plot of `y = sin(x)` over `x` (0 to 10).
* `plt.show()` renders the figure.

**Observed output**
A Matplotlib figure object was displayed (the notebook recorded `<Figure size 640x480 with 1 Axes>`).

---

### 6.2 Cosine wave

Code:

```python
plt.plot(x, z)
plt.show()
```

**Explanation**

* Plots `z = cos(x)` using the default line color and style.

---

### 6.3 Adding axis labels and title

Code:

```python
# adding title to x-axis and y-axis labels
plt.plot(x, y)
plt.xlabel('x')
plt.ylabel('sin(x)')
plt.title('Sine Wave')
plt.show()
```

**Explanation**

* `plt.xlabel`, `plt.ylabel` set axis labels.
* `plt.title` sets the main title.
* These functions are convenience wrappers around `Axes.set_xlabel`, `Axes.set_ylabel`, `Axes.set_title`.

---

### 6.4 Multiple line styles / markers

Notebook shows several style strings:

```python
# plot a parabola (different example for markers)
x = np.linspace(-10, 10, 20)
y = x**2
plt.plot(x, y)             # default line
plt.xlabel('x')
plt.ylabel('y')
plt.title('Parabola')
plt.show()
```

Then different marker/line combos were used:

```python
plt.plot(x, y, 'r+')       # red plus markers (no connecting line)
plt.xlabel('x')
plt.ylabel('y')
plt.title('Parabola')
plt.show()

plt.plot(x, y, 'g--')      # green dashed line
plt.xlabel('x')
plt.ylabel('y')
plt.title('Parabola')
plt.show()

plt.plot(x, y, 'rx')       # red x markers
plt.show()
```

**Style string explanation** (the `'fmt'` parameter in `plot`):

* `'r+'`: red (`r`) plus marker (`+`).
* `'g--'`: green dashed line.
* `'rx'`: red `x` markers.

You can also use keyword arguments for more explicit control:

```python
plt.plot(x, y, color='blue', linestyle='--', marker='o', label='parabola')
plt.legend()
```

---

### 6.5 Overlaying sine and cosine

Notebook cell:

```python
x = np.linspace(-5, 5, 50)
plt.plot(x, np.sin(x), 'g--')
plt.plot(x, np.cos(x), 'r--')
plt.show()
```

**Explanation**

* Two `plt.plot` calls on the same axes overlay sine and cosine.
* Using `'g--'` and `'r--'` sets dashed green and dashed red lines respectively.
* If you want a legend, use `plt.legend()` and pass `label='...'` to each `plot()`.

---

# 7. Parabola example (explicit cell)

Code (complete):

```python
# plot a parabola
x = np.linspace(-10, 10, 20)
y = x**2
plt.plot(x, y)
plt.xlabel('x')
plt.ylabel('y')
plt.title('Parabola')
plt.show()
```

**Explanation**

* Demonstrates plotting a simple function (`y = x^2`) and adding axis labels and a title.

---

# 8. Bar chart

Code:

```python
# bar plot
fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
languages = ['English', 'French', 'German', 'Bangla', 'Chinese']
people = [100, 85, 67, 43, 21]
ax.bar(languages, people)
plt.xlabel('Languages')
plt.ylabel('Number of People')
plt.title('Programming Languages')
plt.show()
```

**Explanation**

* Creates a `Figure` with `fig = plt.figure()` and explicit axes with `add_axes([left, bottom, width, height])`. The coordinates are in figure fraction units (\[0,0,1,1] fills the whole figure).
* `ax.bar(x_labels, heights)` draws categorical bar chart. Here the x positions are the category names; Matplotlib will position them automatically.
* Use `ax.set_xlabel`, `ax.set_ylabel`, `ax.set_title` on `ax` for the object-oriented approach; notebook used `plt.xlabel` and `plt.ylabel` which affects current axes.

**Notes & tips**

* For more control (rotation of xticks, colors, widths), use `ax.bar(..., color=..., width=...)` and `plt.xticks(rotation=...)`.
* When working with categorical bars often `ax.bar(range(len(categories)), values)` + `ax.set_xticks(...)` + `ax.set_xticklabels(...)` is used.

---

# 9. Pie chart

Code (complete):

```python
# Pie Chart
fig1 = plt.figure()
ax1 = fig1.add_axes([0,0,1,1])
languages = ['English', 'French', 'German', 'Bangla', 'Chinese']
people = [100, 85, 67, 43, 21]
ax1.pie(people, labels = languages, autopct='%1.1f')
plt.show()
```

**Explanation**

* `ax1.pie(people, labels=languages, autopct='%1.1f')` draws a pie chart. `autopct` formats the percentage label on each slice (e.g., `1.1f` means one decimal place).
* `add_axes([0,0,1,1])` was used to control axes position; for typical usage `fig, ax = plt.subplots()` is preferred.

**Notes**

* Pie charts are best for simple, small-number categorical shares; interpret with caution.
* You can explode slices via `explode` parameter, and specify `colors`, `startangle`, `shadow`, etc.

---

# 10. Scatter plot (2D)

Code:

```python
# Scatter Plot
x = np.linspace(0, 10, 30)
y = np.sin(x)
z = np.cos(x)
fig2 = plt.figure()
ax2 = fig2.add_axes([0,0,1,1])
ax2.scatter(x, y, color='r')
ax2.scatter(x, z, color='b')
plt.show()
```

**Explanation**

* `ax2.scatter(x, y, color='r')` plots red markers for `(x,y)`. `ax2.scatter(x,z,color='b')` adds blue markers for `(x,z)`.
* `scatter` accepts many visual parameters: `s` (marker size), `c` (colors, can be array for colormap), `alpha` (transparency), `marker` (shape), etc.

**Example variations**

* Color by value: `ax2.scatter(x, y, c=y, cmap='viridis')`
* Size by value: `ax2.scatter(x, y, s=100*abs(y))`

---

# 11. 3D scatter plot

Code:

```python
# 3d scatter plot
fig3 = plt.figure()
ax = plt.axes(projection='3d')
z = 20 * np.random.random(100)
x = np.sin(z)
y = np.cos(z)
ax.scatter(x, y, z, c=z, cmap='Greens')
plt.show()
```

**Explanation**

* `plt.axes(projection='3d')` constructs a 3D axes (requires `mpl_toolkits.mplot3d` backend, usually available by default with Matplotlib).
* `z = 20 * np.random.random(100)` — 100 random z-values in \[0, 20).
* `ax.scatter(x, y, z, c=z, cmap='Greens')` creates a 3D scatter with a colormap based on `z` values (the color set is `cmap='Greens'`).
* The notebook recorded a figure object: `<Figure size 640x480 with 1 Axes>`.

**Notes**

* 3D axes support additional methods (`ax.view_init(elev, azim)` to change viewing angle).
* For complex 3D visualizations consider `plot_surface`, `plot_trisurf`, etc.

---

# 12. Typical Matplotlib workflow summary

1. **Prepare data** (arrays via NumPy).
2. **Create figure/axes**:

   * Quick: `plt.figure()` and `plt.plot()` or `plt.subplots()`.
   * OO style: `fig, ax = plt.subplots()` or `fig = plt.figure(); ax = fig.add_axes([...])`.
3. **Plot data**: `ax.plot`, `ax.scatter`, `ax.bar`, etc. or stateful `plt.plot`.
4. **Label / style**: `ax.set_xlabel`, `ax.set_ylabel`, `ax.set_title`, `ax.legend`, `ax.grid`.
5. **Display or save**:

   * Display: `plt.show()` in interactive/notebook contexts.
   * Save: `plt.savefig('figure.png', dpi=150, bbox_inches='tight')`.

**Object-oriented vs. stateful interface**

* For scripts and complex plots prefer object-oriented (OO) API: get `Figure` and `Axes` objects and call their methods.
* For quick exploration, `plt` stateful API is fine.

---

# 13. Appendix — full notebook code listing (cells & outputs)

Below is a cleaned, ordered copy of the notebook code cells (reconstructed exactly as in the uploaded notebook) with brief notes about outputs.

> **Cell 1 — imports**

```python
# importing
import matplotlib.pyplot as plt
```

> **Cell 2 — numpy import**

```python
# import numpy to get data fpr out plots
import numpy as np
```

> **Cell 3 — prepare sine/cos arrays**

```python
x = np.linspace(0, 10, 100)
y = np.sin(x)
z = np.cos(x)
```

> **Cell 4 — print x**

```python
print(x)
```

*Output (truncated)*:

```
[ 0.          0.1010101   0.2020202   0.3030303   0.4040404   0.50505051
  ...
  9.6969697   9.7979798   9.8989899  10.        ]
```

> **Cell 5 — print y**

```python
print(y)
```

*Output (truncated)*:

```
[ 0.          0.10083842  0.20064886  ... -0.99075324 -0.97202182 -0.94338126 ... ]
```

> **Cell 6 — print z**

```python
print(z)
```

*Output (truncated)*:

```
[ 1.          0.99490282  0.97966323 ... -0.83907153 ... ]
```

> **Cell 8 — sine line plot**

```python
# sine wave
plt.plot(x, y)
plt.show()
```

*Output recorded by notebook*: `<Figure size 640x480 with 1 Axes>`

> **Cell 9 — cosine line plot**

```python
plt.plot(x, z)
plt.show()
```

*Output*: `<Figure size 640x480 with 1 Axes>`

> **Cell 10 — titled sine wave**

```python
# adding title to x-axsis and y-axsis labels
plt.plot(x, y)
plt.xlabel('x')
plt.ylabel('sin(x)')
plt.title('Sine Wave')
plt.show()
```

*Output*: `<Figure size 640x480 with 1 Axes>`

> **Cell 11 — parabola**

```python
# plot a parabola
x = np.linspace(-10, 10, 20)
y = x**2
plt.plot(x, y)
plt.xlabel('x')
plt.ylabel('y')
plt.title('Parabola')
plt.show()
```

*Output*: `<Figure size 640x480 with 1 Axes>`

> **Cell 12 — parabola with red plus markers**

```python
plt.plot(x, y, 'r+')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Parabola')
plt.show()
```

> **Cell 13 — parabola with green dashed line**

```python
plt.plot(x, y, 'g--')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Parabola')
plt.show()
```

> **Cell 14 — parabola with red x markers**

```python
plt.plot(x, y, 'rx')
plt.show()
```

> **Cell 15 — sin and cos overlay**

```python
x = np.linspace(-5, 5, 50)
plt.plot(x, np.sin(x), 'g--')
plt.plot(x, np.cos(x), 'r--')
plt.show()
```

> **Cell 16 — bar plot**

```python
# bar plot
fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
languages = ['English', 'French', 'German', 'Bangla', 'Chinese']
people = [100, 85, 67, 43, 21]
ax.bar(languages, people)
plt.xlabel('Languages')
plt.ylabel('Number of People')
plt.title('Programming Languages')
plt.show()
```

*Output*: `<Figure size 640x480 with 1 Axes>`

> **Cell 17 — pie chart**

```python
# Pie Chart
fig1 = plt.figure()
ax1 = fig1.add_axes([0,0,1,1])
languages = ['English', 'French', 'German', 'Bangla', 'Chinese']
people = [100, 85, 67, 43, 21]
ax1.pie(people, labels = languages, autopct='%1.1f')
plt.show()
```

*Output*: `<Figure size 640x480 with 1 Axes>`

> **Cell 18 — scatter plot**

```python
# Scatter Plot
x = np.linspace(0, 10, 30)
y = np.sin(x)
z = np.cos(x)
fig2 = plt.figure()
ax2 = fig2.add_axes([0,0,1,1])
ax2.scatter(x,y,color='r')
ax2.scatter(x,z,color='b')
plt.show()
```

*Output*: `<Figure size 640x480 with 1 Axes>`

> **Cell 19 — 3D scatter plot**

```python
# 3d scatter plot
fig3 = plt.figure()
ax = plt.axes(projection='3d')
z = 20 * np.random.random(100)
x = np.sin(z)
y = np.cos(z)
ax.scatter(x, y, z, c=z, cmap='Greens')
plt.show()
```

*Output*: `<Figure size 640x480 with 1 Axes>`

---

# Additional tips & best practices

* **Prefer the OO API for complex plots**:

  ```python
  fig, ax = plt.subplots()
  ax.plot(x, y, label='sin')
  ax.set_xlabel('x')
  ax.set_ylabel('sin(x)')
  ax.set_title('Sine wave')
  ax.legend()
  fig.savefig('sine.png', dpi=150)
  ```

* **Saving figures**: use `fig.savefig('name.png', dpi=..., bbox_inches='tight')` (or `plt.savefig(...)`) before `plt.show()`.

* **Plotting styles**: Matplotlib has style sheets: `plt.style.use('seaborn')` or `'ggplot'` for quick improved aesthetics.

* **Interactive notebooks**: `%matplotlib inline` (or `%matplotlib notebook`) controls inline display; your notebook environment sometimes handles this automatically.

* **3D plotting**: for 3D use `fig = plt.figure(); ax = fig.add_subplot(111, projection='3d')` or `plt.axes(projection='3d')`.

---

