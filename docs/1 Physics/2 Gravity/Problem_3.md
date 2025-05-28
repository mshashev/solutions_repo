# Problem 3
# Trajectories of a Freely Released Payload Near Earth

The motion of a payload released near Earth (ignoring air resistance) follows one of the **conic section trajectories**—**circle**, **ellipse**, **parabola**, or **hyperbola**—depending on its **initial speed** relative to Earth and **direction**.

---

###  1. Circular Orbit
- **Condition**:  
  $v = v_{\text{circular}}$
- **Shape**:  
  Circle (special case of ellipse)
- **Energy**:  
  Total mechanical energy $E < 0$
- **Nature**:  
  Closed orbit, constant speed and altitude.
- **Example**:  
  Idealized geostationary satellite.

---

###  2. Elliptical Orbit
- **Condition**:  
  $v_{\text{circular}} < v < v_{\text{escape}}$
- **Shape**:  
  Ellipse
- **Energy**:  
  $E < 0$
- **Nature**:  
  Closed orbit, speed and altitude vary.
- **Examples**:  
  Low Earth Orbit (LEO), Medium Earth Orbit (MEO), Molniya orbit.

---

###  3. Parabolic Trajectory
- **Condition**:  
  $v = v_{\text{escape}}$
- **Shape**:  
  Parabola
- **Energy**:  
  $E = 0$
- **Nature**:  
  Marginal escape – object escapes Earth, reaching infinity with zero velocity.
- **Example**:  
  Theoretical boundary between bound and unbound motion.

---

###  4. Hyperbolic Trajectory
- **Condition**:  
  $v > v_{\text{escape}}$
- **Shape**:  
  Hyperbola
- **Energy**:  
  $E > 0$
- **Nature**:  
  Open trajectory – object escapes Earth’s gravity with residual velocity.
- **Examples**:  
  Interplanetary missions (e.g., Voyager, New Horizons after Earth flyby).

---

###  Summary Table

| **Trajectory**       | **Velocity Condition**                   | **Total Energy**   | **Orbit Type**     |
|----------------------|------------------------------------------|--------------------|---------------------|
| Circular             | $v = v_{\text{circular}}$                | $E < 0$            | Bound (closed)      |
| Elliptical           | $v_{\text{circular}} < v < v_{\text{escape}}$ | $E < 0$        | Bound (closed)      |
| Parabolic            | $v = v_{\text{escape}}$                  | $E = 0$            | Unbound (open)      |
| Hyperbolic           | $v > v_{\text{escape}}$                  | $E > 0$            | Unbound (open)      |

![alt text](image-9.png)




## Numerical Analysis of a Payload Trajectory Near Earth

This analysis computes the path of a payload released near Earth using Newtonian gravitational physics. We simulate the trajectory based on initial conditions using numerical integration techniques.

---

### Step 1: Define Constants and Initial Conditions

Let:

- Earth mass: $M = 5.972 \times 10^{24} \ \text{kg}$
- Gravitational constant: $G = 6.67430 \times 10^{-11} \ \text{N} \cdot \text{m}^2/\text{kg}^2$
- Earth radius: $R_e = 6.371 \times 10^6 \ \text{m}$
- Initial altitude: $h = 400 \times 10^3 \ \text{m}$ (Low Earth Orbit)
- Total initial radius: $R = R_e + h$

**Initial position and velocity:**

- $\vec{r}_0 = (R, 0)$
- $\vec{v}_0 = (0, v)$

**Reference velocities:**

- Circular orbit velocity: $v_{\text{circular}} = \sqrt{\frac{GM}{R}}$
- Escape velocity: $v_{\text{escape}} = \sqrt{2} \cdot v_{\text{circular}}$

---

### Step 2: Governing Equations

Using **Newton's Law of Gravitation** and **Newton's Second Law**, the equations of motion in 2D are:

$$
\vec{F} = -\frac{GMm}{r^2} \hat{r}
$$

$$
\vec{a} = \frac{\vec{F}}{m} = -\frac{GM}{r^3} \vec{r}
$$

In component form:

$$
\frac{d^2x}{dt^2} = -\frac{GMx}{(x^2 + y^2)^{3/2}}, \quad
\frac{d^2y}{dt^2} = -\frac{GMy}{(x^2 + y^2)^{3/2}}
$$

---

### Step 3: Numerical Integration (Runge-Kutta 4th Order)

To numerically solve these equations, we define:

Let:

- $\vec{r} = (x, y)$  
- $\vec{v} = (v_x, v_y)$

Convert to first-order ODEs:

$$
\frac{dx}{dt} = v_x, \quad
\frac{dy}{dt} = v_y
$$

$$
\frac{dv_x}{dt} = -\frac{GMx}{(x^2 + y^2)^{3/2}}, \quad
\frac{dv_y}{dt} = -\frac{GMy}{(x^2 + y^2)^{3/2}}
$$

These can be integrated using the Runge-Kutta 4th order method or Euler’s method.

---

### Step 4: Trajectory Classification

We compute total mechanical energy to classify the orbit:

### Total Energy

$$
E = \frac{1}{2}mv^2 - \frac{GMm}{r}
$$

- $E < 0$ → Elliptical orbit (bound)
- $E = 0$ → Parabolic escape
- $E > 0$ → Hyperbolic escape

### Eccentricity (Optional)

The trajectory's **eccentricity**:

$$
e = \sqrt{1 + \frac{2EL^2}{G^2M^2m^3}}
$$

Where $L = mrv_\perp$ is the angular momentum.

- $e < 1$ → Elliptical
- $e = 1$ → Parabolic
- $e > 1$ → Hyperbolic

---

![alt text](image-4.png)

---

### The trajectories—circular, elliptical, parabolic, and hyperbolic—dictate **orbital insertion**, **reentry**, and **escape scenarios** based on initial velocity and energy ($E = \frac{1}{2}mv^2 - \frac{GMm}{r}$).

- **Orbital Insertion**:
  - **Circular Orbit ($v = v_{\text{circular}}$, $E < 0$)**: Stable, constant-altitude orbit (e.g., geostationary satellites). Requires $v_{\text{circular}} \approx 7.67 \, \text{km/s}$ at 400 km altitude.
  - **Elliptical Orbit ($v_{\text{circular}} < v < v_{\text{escape}}$, $E < 0$)**: Bound orbit with varying altitude (e.g., LEO, GPS satellites). Achieved via precise burns, often using transfer orbits.
  - **Process**: Velocity adjustments ensure $E < 0$, $e < 1$.

- **Reentry**:
  - **Circular/Elliptical Orbits**: Starts bound ($E < 0$). A retro-burn ($\Delta v \approx 100-200 \, \text{m/s}$) lowers perigee into the atmosphere (e.g., Crew Dragon).
  - **Parabolic/Hyperbolic Trajectories ($E \geq 0$)**: Rare, often uncontrolled (e.g., meteoroids, Stardust capsule).
  - **Process**: Energy loss via burns or drag shifts trajectory to descent.

- **Escape Scenarios**:
  - **Parabolic Trajectory ($v = v_{\text{escape}}$, $E = 0$)**: Marginal escape, zero velocity at infinity. Theoretical minimum.
  - **Hyperbolic Trajectory ($v > v_{\text{escape}}$, $E > 0$)**: Unbound, with residual velocity (e.g., Voyager). Needs $\Delta v \approx 3.2 \, \text{km/s}$ from LEO.
  - **Process**: Burns or gravitational assists achieve $E \geq 0$, $e \geq 1$.

**Relation**: Energy and eccentricity ($e = \sqrt{1 + \frac{2EL^2}{G^2M^2m^3}}$) classify trajectories:
- Insertion: $E < 0$, $e < 1$ (bound).
- Reentry: Bound, energy reduced for atmospheric entry.
- Escape: $E \geq 0$, $e \geq 1$ (unbound).
Numerical integration (e.g., Runge-Kutta) ensures precise trajectory prediction.

---

**Circular**, **elliptical**, **parabolic**, and **hyperbolic** trajectories, driven by velocity and energy ($E = \frac{1}{2}mv^2 - \frac{GMm}{r}$), enable **space mission planning**, **satellite deployment**, and **planetary exploration**. Numerical integration ensures accuracy.

---

## Real-world applications

### 1. Space Mission Planning
Optimizes trajectories for **insertion**, **reentry**, or **escape**.
- **Circular ($v = v_{\text{circular}}$, $E < 0$)**: Stable orbits (e.g., geostationary, $v \approx 3.07 \, \text{km/s}$). Precise burns.
- **Elliptical ($v_{\text{circular}} < v < v_{\text{escape}}$, $E < 0$)**: Variable orbits (e.g., GPS). Hohmann transfers, $e < 1$.
- **Hyperbolic ($v > v_{\text{escape}}$, $E > 0$)**: Escapes (e.g., New Horizons, $v > 11.2 \, \text{km/s}$). Uses flybys.

---

### 2. Satellite Deployment
Places satellites in **circular** or **elliptical** orbits.
- **Circular**: LEO (e.g., Starlink, $v \approx 7.6 \, \text{km/s}$). Burn-circularized, $e \approx 0$.
- **Elliptical**: Specialized (e.g., Molniya). Transfer orbits, debris avoidance.

---

### 3. Planetary Exploration
**Elliptical** for departure, **hyperbolic** for travel, **circular/elliptical** for arrival.
- **Elliptical**: Parking orbits (e.g., Perseverance). Low $\Delta v$.
- **Hyperbolic**: Interplanetary (e.g., Voyager, $e > 1$). Flybys, corrections.
- **Circular/Elliptical**: Target orbits (e.g., Juno at Jupiter). Burns/aerobraking.

---

### Summary
- **Planning**: Circular for stability, elliptical for transfers, hyperbolic for escapes.
- **Deployment**: Circular LEO, elliptical specialized.
- **Exploration**: Elliptical to hyperbolic to target orbits.
Uses $\vec{a} = -\frac{GM}{r^3}\vec{r}$, $E$, $e = \sqrt{1 + \frac{2EL^2}{G^2M^2m^3}}$, numerical precision.

---
---

Okay, let's go through these function problems step by step in English.

**Q1. Determine if $f(x) = 2x + 3$ is one-to-one.**

To check if a function is one-to-one (injective), we need to show that if $f(a) = f(b)$, then $a = b$.

If $f(a) = f(b)$. Then:$$2a + 3 = 2b + 3$$Subtracting 3 from both sides, we get:$$2a = 2b$$Dividing both sides by 2, we get:$$a = b$$
Therefore, the function $f(x) = 2x + 3$ is one-to-one.

**Q2. Is $f(x) = x^2$ one-to-one on $\mathbb{R}$?**

No, the function $f(x) = x^2$ is not one-to-one on the set of real numbers $\mathbb{R}$. We can find two different inputs that give the same output. For example:
$$f(2) = 2^2 = 4$$
$$f(-2) = (-2)^2 = 4$$
Since $f(2) = f(-2)$ but $2 \neq -2$, the function is not one-to-one on $\mathbb{R}$.

**Q3. Show that $f(x) = \frac{1}{x}$ is one-to-one on $\mathbb{R} \setminus \{0\}$.**

Assume $f(a) = f(b)$ for $a, b \in \mathbb{R} \setminus \{0\}$. Then:$$\frac{1}{a} = \frac{1}{b}$$Multiplying both sides by $ab$ (which is allowed since $a \neq 0$ and $b \neq 0$), we get:$$b = a$$
Therefore, the function $f(x) = \frac{1}{x}$ is one-to-one on $\mathbb{R} \setminus \{0\}$.

**Q4. Is $f(x) = 3x + 1$ onto $\mathbb{R}$?**

To check if a function is onto (surjective), we need to show that for every $y \in \mathbb{R}$, there exists an $x \in \mathbb{R}$ such that $f(x) = y$.

Let $y$ be any real number. We want to find $x$ such that:
$$3x + 1 = y$$Subtracting 1 from both sides, we get:$$3x = y - 1$$Dividing both sides by 3, we get:$$x = \frac{y - 1}{3}$$
Since for every $y \in \mathbb{R}$, $x = \frac{y - 1}{3}$ is also a real number and satisfies $f(x) = y$, the function $f(x) = 3x + 1$ is onto $\mathbb{R}$.

**Q5. Is $f(x) = e^x$ onto $\mathbb{R}$?**

No, the function $f(x) = e^x$ is not onto $\mathbb{R}$. The range of the function $e^x$ is $(0, \infty)$, which is the set of all positive real numbers. There is no real number $x$ such that $e^x$ is non-positive (zero or negative). Therefore, not every element in $\mathbb{R}$ has a pre-image in the domain.

**Q6. Show that $f(x) = x^3$ is onto $\mathbb{R}$.**

Let $y$ be any real number. We want to find $x$ such that $f(x) = y$, which means:
$$x^3 = y$$Taking the cube root of both sides, we get:$$x = \sqrt[3]{y}$$
For every real number $y$, there exists a unique real number $x = \sqrt[3]{y}$ such that $x^3 = y$. Therefore, the function $f(x) = x^3$ is onto $\mathbb{R}$.

**Q7. Find the inverse of $f(x) = 2x + 5$.**

To find the inverse function, we swap $x$ and $y$ and solve for $y$.
Let $y = f(x) = 2x + 5$. Swap $x$ and $y$:
$$x = 2y + 5$$Now solve for $y$:$$x - 5 = 2y$$
$$y = \frac{x - 5}{2}$$
Therefore, the inverse function is $f^{-1}(x) = \frac{x - 5}{2}$.

**Q8. Find the inverse of $f(x) = \frac{x - 1}{x + 2}$.**

Let $y = f(x) = \frac{x - 1}{x + 2}$. Swap $x$ and $y$:
$$x = \frac{y - 1}{y + 2}$$Now solve for $y$:$$x(y + 2) = y - 1$$$$xy + 2x = y - 1$$$$xy - y = -2x - 1$$$$y(x - 1) = -2x - 1$$$$y = \frac{-2x - 1}{x - 1} = \frac{2x + 1}{1 - x}$$
Therefore, the inverse function is $f^{-1}(x) = \frac{2x + 1}{1 - x}$.

**Q9. Does $f(x) = x^2$ have an inverse over $\mathbb{R}$?**

No, the function $f(x) = x^2$ does not have an inverse over the set of real numbers $\mathbb{R}$. For a function to have an inverse, it must be a bijection (both one-to-one and onto). As shown in Q2, $f(x) = x^2$ is not one-to-one on $\mathbb{R}$, so it cannot have an inverse function on this set.

**Q10. Verify $f(f^{-1}(x)) = x$ for $f(x) = 3x - 4$.**

First, let's find the inverse function $f^{-1}(x)$. Let $y = 3x - 4$. Swap $x$ and $y$:
$$x = 3y - 4$$$$x + 4 = 3y$$$$y = \frac{x + 4}{3}$$
So, $f^{-1}(x) = \frac{x + 4}{3}$.

Now, let's compute $f(f^{-1}(x))$:
$$f(f^{-1}(x)) = f\left(\frac{x + 4}{3}\right) = 3\left(\frac{x + 4}{3}\right) - 4 = (x + 4) - 4 = x$$
Thus, $f(f^{-1}(x)) = x$ is verified.

**Q11. Show that $f(x) = x + 1$ is a bijection.**

To show that $f(x) = x + 1$ is a bijection, we need to show that it is both one-to-one and onto.

* **One-to-one:** Assume $f(a) = f(b)$. Then $a + 1 = b + 1$, which implies $a = b$. Therefore, $f(x)$ is one-to-one.
* **Onto:** Let $y$ be any real number. We want to find $x$ such that $f(x) = y$, i.e., $x + 1 = y$. Solving for $x$, we get $x = y - 1$. Since for every $y \in \mathbb{R}$, $x = y - 1$ is also a real number, the function is onto.

Since $f(x) = x + 1$ is both one-to-one and onto, it is a bijection.

**Q12. Is $f(x) = \sin x$ a bijection on $\mathbb{R}$?**

No, the function $f(x) = \sin x$ is not a bijection on $\mathbb{R}$.

* **Not one-to-one:** For example, $\sin(0) = 0$ and $\sin(\pi) = 0$, but $0 \neq \pi$.
* **Not onto:** The range of the function $\sin x$ is $[-1, 1]$, which is not the entire set of real numbers $\mathbb{R}$. For example, there is no $x \in \mathbb{R}$ such that $\sin x = 2$.

Therefore, $f(x) = \sin x$ is not a bijection on $\mathbb{R}$.

**Q13. Find the inverse of $f(x) = \frac{1}{x + 1}$.**

Let $y = f(x) = \frac{1}{x + 1}$. Swap $x$ and $y$:
$$x = \frac{1}{y + 1}$$Now solve for $y$:$$x(y + 1) = 1$$$$xy + x = 1$$$$xy = 1 - x$$
$$y = \frac{1 - x}{x}$$
Therefore, the inverse function is $f^{-1}(x) = \frac{1 - x}{x}$.

**Q14. Let $f(x) = 2x + 3$, $g(x) = x^2$. Find $(f \circ g)(x)$.**

The composition of functions $(f \circ g)(x)$ is defined as $f(g(x))$.
$$f(g(x)) = f(x^2) = 2(x^2) + 3 = 2x^2 + 3$$
Therefore, $(f \circ g)(x) = 2x^2 + 3$.

**Q15. Let $f(x) = \sqrt{x}$, $g(x) = x + 1$. Find $(f \circ g)(x)$ and domain.**

The composition of functions $(f \circ g)(x)$ is defined as $f(g(x))$.
$$f(g(x)) = f(x + 1) = \sqrt{x + 1}$$
Therefore, $(f \circ g)(x) = \sqrt{x + 1}$.

To find the domain of $(f \circ g)(x)$, we need to consider the domain of the inner function $g(x)$ and the domain of the outer function $f(x)$ after substituting $g(x)$.
* The domain of $g(x) = x + 1$ is all real numbers $\mathbb{R}$.
* The domain of $f(x) = \sqrt{x}$ is $x \ge 0$.

For the composition $f(g(x)) = \sqrt{x + 1}$, the argument of the square root must be non-negative:
$$x + 1 \ge 0$$
$$x \ge -1$$
Therefore, the domain of $(f \circ g)(x)$ is $[-1, \infty)$.

**Q16. If $f(x) = \frac{1}{x}$, $g(x) = x^2$, find $(g \circ f)(x)$.**

The composition of functions $(g \circ f)(x)$ is defined as $g(f(x))$.
$$g(f(x)) = g\left(\frac{1}{x}\right) = \left(\frac{1}{x}\right)^2 = \frac{1}{x^2}$$
Therefore, $(g \circ f)(x) = \frac{1}{x^2}$. The domain of this function is $\mathbb{R} \setminus \{0\}$, since $x$ cannot be zero (due to $f(x) = \frac{1}{x}$).

**Q17. Show that composition of two bijections is a bijection.**

Let $f: A \to B$ and $g: B \to C$ be two bijections. We need to show that their composition $g \circ f: A \to C$ is also a bijection, meaning it is both one-to-one and onto.

* **One-to-one:** Assume $(g \circ f)(a_1) = (g \circ f)(a_2)$ for $a_1, a_2 \in A$. Then $g(f(a_1)) = g(f(a_2))$. Since $g$ is one-to-one, it must be that $f(a_1) = f(a_2)$. Since $f$ is one-to-one, it must be that $a_1 = a_2$. Therefore, $g \circ f$ is one-to-one.

* **Onto:** Let $c \in C$ be any element. Since $g: B \to C$ is onto, there exists a $b \in B$ such that $g(b) = c$. Since $f: A \to B$ is onto, there exists an $a \in A$ such that $f(a) = b$. Then $g(f(a)) = g(b) = c$. For every $c \in C$, there exists an $a \in A$ such that $(g \circ f)(a) = c$, so $g \circ f$ is onto.

Since $g \circ f$ is both one-to-one and onto, it is a bijection.

**Q18. Find $f$ and $g$ such that $f \circ g = \sqrt{x^2 + 1}$.**

There are many possible answers. One simple possibility is:
$$g(x) = x^2 + 1$$
$$f(x) = \sqrt{x}$$
Then $(f \circ g)(x) = f(g(x)) = f(x^2 + 1) = \sqrt{x^2 + 1}$.

Another possibility is:
$$g(x) = x$$
$$f(x) = \sqrt{x^2 + 1}$$
Then $(f \circ g)(x) = f(g(x)) = f(x) = \sqrt{x^2 + 1}$.

**Q19. Is $f(x) = \ln x$ invertible? Find its inverse.**

For a function to be invertible, it must be a bijection from its domain to its range.

* The function $f(x) = \ln x$ has a domain of $(0, \infty)$ and a range of $\mathbb{R}$.
* It is one-to-one because if $\ln a = \ln b$, then $a = b$.
* It is onto its range $\mathbb{R}$ because for every $y \in \mathbb{R}$, there exists an $x = e^y \in (0, \infty)$ such that $\ln(e^y) = y$.

Therefore, $f(x) = \ln x$ is invertible on its domain $(0, \infty)$ and range $\mathbb{R}$.

To find its inverse, let $y = \ln x$. Swap $x$ and $y$:
$$x = \ln y$$To solve for $y$, we rewrite the equation in exponential form:$$e^x = y$$
Therefore, the inverse function is $f^{-1}(x) = e^x$.

**Q20. If $f(x) = 3x + 2$, $g(x) = \frac{x - 2}{3}$, show $f \circ g = g \circ f = x$.**

Let's compute $f \circ g$:
$$(f \circ g)(x) = f(g(x)) = f\left(\frac{x - 2}{3}\right) = 3\left(\frac{x - 2}{3}\right) + 2 = (x - 2) + 2 = x$$

Now, let's compute $g \circ f$:
$$(g \circ f)(x) = g(f(x)) = g(3x + 2) = \frac{(3x + 2) - 2}{3} = \frac{3x}{3} = x$$

Since $(f \circ g)(x) = x$ and $(g \circ f)(x) = x$, we have shown that $f \circ g = g \circ f = x$. This means that $g$ is the inverse function of $f$, and $f$ is the inverse function of $g$.