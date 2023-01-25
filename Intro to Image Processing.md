# Image Processing

**Sampling Artifacts in Graphics** are ugly and evil! e.g. Jaggies

![](https://cs184.eecs.berkeley.edu/public/sp22/lectures/lec-3-sampling-and-aliasing/slides/slide-11.jpg)
## Anti-Aliasing

Core idea: filter out **high frequencies**(Make the signal change less abruptly)before sampling.

![](https://cs184.eecs.berkeley.edu/public/sp22/lectures/lec-3-sampling-and-aliasing/slides/slide-18.jpg)

The dots on the processed image above are blurred, leading to lower frequency and better visual effects.

**Pre-Filtering** is essential to antialising, sampling then filtering is not enough.

Simple idea: remove/reduce signal frequencies above the Nyquist frequency, before sampilng.



## Frequency Space

e.g. trigonometric functions ![f(x) = sin(x)](https://render.githubusercontent.com/render/math?math=f(x)%20%3D%20sin(x))

undersampling leads to **frequency aliases**
samples from high-frequency signal may become indistinguishable from samples from low-frequency signal with underampling.

### Fourier Transform

Idea: any function can be decomposed into a sum of sinusoids.

"Decomposing a signal into frequencies" 
**spatial domain** => **frequency domain**

### Visualization Of Frequency Space
More on https://cs184.eecs.berkeley.edu/sp23/lecture/3-33/sampling-and-aliasing

![](https://cs184.eecs.berkeley.edu/public/sp22/lectures/lec-3-sampling-and-aliasing/slides/slide-33.jpg)

### Filtering
**Convolution Theorem** - Convolution in spatial domain is equivalent to multiplication in frequency domain.

2 options to filter:
1. Convolution in spatial domain
2. Multiplication in frequency domain

#### Nyquist Frequency & Antialiasing
Nyquist Theorem:
We get no aliasing form frequencies in the signal that are less than the nyquist frequency.

`Nyquist frequency = 1/2 * sampling frequency`

Example:
for sin(2pi/32)x, the nyquist frequency is 1/32, so we can sample at 1/16 without aliasing.

Intuition: once the image is blurred enough, sampling it at a lower frequency will not go wrong, as the point that could've gone wrong with the original image has been diluted to other possible points.


## Antialiasing By Super-Sampling

tbd...