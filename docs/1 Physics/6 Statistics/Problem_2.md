# Problem 2

# Estimating $\pi$ Using Monte Carlo Methods

## Introduction

Monte Carlo methods are **probabilistic simulation techniques** used to estimate unknown values through repeated random sampling. One of the most famous applications is estimating the value of $\pi$.

---

## Geometric Interpretation

The basic idea involves **randomly sampling points** in a 2D space and using geometry to estimate $\pi$.

### Setup:
- Imagine a **square** of side length 2, centered at the origin:  
  $x \in [-1, 1]$, $y \in [-1, 1]$
- Inside this square, inscribe a **circle of radius 1** (also centered at the origin).
- The **area of the square** is:  
  $$A_{\text{square}} = 2 \times 2 = 4$$
- The **area of the circle** is:  
  $$A_{\text{circle}} = \pi r^2 = \pi \cdot 1^2 = \pi$$

---

## Monte Carlo Estimation Procedure

### Step-by-step:

1. Randomly generate **$n$ points** $(x, y)$, where $x, y \in [-1, 1]$.
2. Count how many points fall **inside the circle**, i.e., those that satisfy:  
   $$x^2 + y^2 \leq 1$$
3. The ratio of points inside the circle to total points approximates the ratio of the areas:  
   $$\frac{\text{points in circle}}{\text{total points}} \approx \frac{\text{area of circle}}{\text{area of square}} = \frac{\pi}{4}$$
4. Multiply by 4 to estimate $\pi$:  
   $$\pi \approx 4 \cdot \frac{\text{points in circle}}{\text{total points}}$$

---

## Why It Works

- This method leverages the **law of large numbers**: as the number of samples increases, the estimate converges to the true value.
- The randomness introduces **statistical noise**, but this noise decreases as sample size grows.

---

## Advantages

- Simple to implement.
- Can be generalized to estimate other areas or integrals in higher dimensions.

## Limitations

- Convergence is slow — high precision requires a large number of samples.
- Not suitable for deterministic or high-precision applications unless heavily optimized.

---
### Circle Method Visualization:

![alt text](image-7.png)


### Understanding the Methods

**Circle Method Theory:**

***Geometric Principle:***

A unit circle inscribed in a $2 \times 2$ square has:

- Circle area:  
  $$\text{Area}_{\text{circle}} = \pi \times 1^2 = \pi$$

- Square area:  
  $$\text{Area}_{\text{square}} = 2 \times 2 = 4$$

- Ratio of areas:  
  $$\frac{\text{Area}_{\text{circle}}}{\text{Area}_{\text{square}}} = \frac{\pi}{4}$$

***Monte Carlo Estimation:***

- Generate random points in the square: $x, y \in [-1, 1]$
- Count how many fall inside the unit circle:  
  $$x^2 + y^2 \leq 1$$
- Estimate $\pi$ using:  
  $$\pi \approx 4 \times \frac{\text{points inside circle}}{\text{total points}}$$

## Results:

![alt text](image-10.png)

###  Buffon's Needle Visualization:
![alt text](image-9.png)

### Understanding the Methods

#### Geometric Setup

- **Parallel Lines**: The plane has parallel lines separated by a distance of 2.0 units.
- **Needles**: Each needle has a length of 1.0 unit and is dropped randomly.
- **Randomization**: Each needle has a random position (center) and a random angle relative to the lines.

---

#### Crossing Probability

- A needle crosses a line if it spans across the line boundary.
- For a needle of length $L$ and line separation $d$, the theoretical probability of a needle crossing a line is:  
  $$P = \frac{2L}{\pi d}$$
- In this setup, $L = 1.0$ and $d = 2.0$, so:  
  $$P = \frac{2 \times 1.0}{\pi \times 2.0} = \frac{1}{\pi}$$

---

#### $\pi$ Estimation

- The value of $\pi$ can be estimated using the formula:  
  $$\pi \approx \frac{2 \times \text{needle length} \times \text{total drops}}{\text{line distance} \times \text{crossings}}$$
- For the current setup ($L = 1.0$, $d = 2.0$):  
  $$\pi \approx \frac{2 \times 1.0 \times n}{2.0 \times \text{crossings}} = \frac{n}{\text{crossings}}$$
- As the number of needle drops increases, the estimate converges to the true value of $\pi$.

## Results:

![alt text](image-11.png)

## Method Comparison:

![alt text](image-12.png)

## Convergence Analysis:
![alt text](image-13.png)