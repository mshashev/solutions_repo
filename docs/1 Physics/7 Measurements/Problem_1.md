

# Problem 1

# Measuring Earth's Gravitational Acceleration with a Pendulum

## Experiment Overview
This report presents the analysis of a pendulum experiment designed to measure Earth's gravitational acceleration ($g$) using a simple pendulum. The experiment includes data collection, error propagation, and statistical analysis.

## Experimental Setup

### Materials and Equipment
- **Pendulum length ($L$)**: 0.8500 ± 0.0010 m  
- **Weight**: Small dense metal bob  
- **Timing device**: Smartphone stopwatch (±0.01 s resolution)  
- **Measurement protocol**: Time for 10 oscillations, repeated 10 times  

### Theoretical Background
The period of a simple pendulum under the small-angle approximation is:

$$
T = 2\pi\sqrt{\frac{L}{g}}
$$

Solving for $g$:

$$
g = \frac{4\pi^2 L}{T^2}
$$

## Raw Data

### Length Measurement
- **Measured length**: 0.8500 m  
- **Uncertainty**: ±0.0010 m  
- **Relative uncertainty**:  
  $$
  \frac{0.0010}{0.8500} = 0.001176 \text{ or } 0.12\%
  $$

### Timing Measurements ($T_{10}$ in seconds)

| Trial | Time for 10 Oscillations (s) |
|-------|------------------------------|
|  1    | 19.42                        |
|  2    | 19.28                        |
|  3    | 19.35                        |
|  4    | 19.31                        |
|  5    | 19.39                        |
|  6    | 19.27                        |
|  7    | 19.45                        |
|  8    | 19.30                        |
|  9    | 19.33                        |
| 10    | 19.40                        |

### Statistical Analysis

- **Mean $T_{10}$**:  
  $$
  \bar{T}_{10} = 19.35 \, \text{s}
  $$

- **Standard deviation**:  
  $$
  \sigma = 0.061 \, \text{s}
  $$

- **Standard error**:  
  $$
  \text{SE} = \frac{\sigma}{\sqrt{n}} = \frac{0.061}{\sqrt{10}} = 0.0193 \, \text{s}
  $$

## Calculations

### Period ($T$) and Uncertainty

- **Period**:  
  $$
  T = \frac{T_{10}}{10} = \frac{19.35}{10} = 1.935 \, \text{s}
  $$

- **Uncertainty in $T$**:  
  $$
  \Delta T = \frac{0.0193}{10} = 0.00193 \, \text{s}
  $$

- **Relative uncertainty in $T$**:  
  $$
  \frac{0.00193}{1.935} = 0.001 \text{ or } 0.1\%
  $$

### Gravitational Acceleration

Using:

$$
g = \frac{4\pi^2 L}{T^2}
$$

Substitute values:

$$
g = \frac{4\pi^2 \cdot 0.8500}{(1.935)^2} = \frac{33.5103}{3.7442} = 8.951 \, \text{m/s}^2
$$

### Uncertainty in $g$

Using:

$$
\Delta g = g \cdot \sqrt{\left( \frac{\Delta L}{L} \right)^2 + \left( 2\frac{\Delta T}{T} \right)^2}
$$

Substitute:

- $\Delta L / L = 0.001176$
- $2\Delta T / T = 2 \cdot 0.001 = 0.002$

So:

$$
\Delta g = 8.951 \cdot \sqrt{(0.001176)^2 + (0.002)^2} = 8.951 \cdot \sqrt{0.00000138 + 0.000004} = 8.951 \cdot 0.0023 = 0.021 \, \text{m/s}^2
$$

## Results and Analysis

### Final Result

$$
g = 8.951 \pm 0.021 \, \text{m/s}^2
$$

### Comparison with Theoretical Value

- **Standard value**: $g_0 = 9.80665 \, \text{m/s}^2$  
- **Absolute error**:  
  $$
  |g - g_0| = 0.856 \, \text{m/s}^2
  $$

- **Relative error**:  
  $$
  \frac{0.856}{9.80665} \approx 8.73\%
  $$

### Statistical Significance

- **Z-score**:

$$
z = \frac{g - g_0}{\Delta g} = \frac{8.951 - 9.80665}{0.021} \approx -40.8
$$

- **P-value**: $\ll 0.001$ → Result is **statistically different** from accepted value.

## Error Analysis

### 1. Systematic Errors
- **Air resistance**: Not accounted for in ideal model  
- **Amplitude**: May exceed small-angle approximation  
- **Pivot friction** and **string flexibility**  

### 2. Random Errors
- **Timing error** from manual stopwatch use  
- **Reaction delay** and **oscillation count accuracy**  

### 3. Dominant Source
- Timing uncertainty dominates due to its squared effect on $T$:

$$
\frac{\partial g}{\partial T} = -\frac{8\pi^2 L}{T^3}
$$

## Conclusions

1. **Measured $g$**: $8.951 \pm 0.021$ m/s²  
2. **Accuracy**: Off by ~8.7% from standard value  
3. **Uncertainty**: Small relative uncertainty (0.23%) but systematic error dominates  
4. **Recommendations**:
   - Use photogate or motion sensors for timing  
   - Ensure small angular displacement  
   - Increase length to reduce effect of timing error  
   - Repeat with multiple pendulums and locations  

## Mathematical Framework

### Error Propagation

For $g = \frac{4\pi^2 L}{T^2}$:

$$
\Delta g = g \cdot \sqrt{ \left( \frac{\Delta L}{L} \right)^2 + \left( 2\frac{\Delta T}{T} \right)^2 }
$$
