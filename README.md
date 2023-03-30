## Interest-Points-Feature-Extraction
NTUA Computer Vision


### 1. Edge Detection
a. **Creation of Image Input**

  - Adding noise to I<sub>0</sub>, to create noisy images I(x, y) = I<sub>0</sub>(x, y) + n(x, y) to be used as inputs to the edge detection algorithm.
    The noise n(x, y) is a white gaussian, with mean 0 and standard deviation σn such that the PSNR (Peak-to-peak Signal to Noise Ratio) to have specific values.
    Use 2 different values for the noise PSNR:
        i) PSNR=20 dB, ii) PSNR=10 dB.
        PSNR is defined as:

```math
          PSNR = 20 log_{10} \left( {I_{max} − I_{min}} \over σ_n \right)   
```

```math
          I_{max} = \max_{x, y} I(x, y), I_{min} = \min_{x, y} I(x, y)  
```
                
b. **Edge Detection Algorithm**
  - Implementation:
    - i. Generating the impulse responses of two discrete linear filters that approximate continuous filters with the following impulse responses:
      - 2D Gaussian $$G_σ(x, y)$$
      - Laplacian of Gaussian $$h(x, y) =  \nabla ^ 2 G_σ(x, y)$$ 
    - ii. Laplacian Estimation $$I_σ = G_σ * I(x, y):$$
      - Linear: $$L =  \nabla ^ 2 (G_σ(x, y) * I) = \nabla ^ 2 (G_σ(x, y)) * I = h * I$$ 
      - Non-Linear: $$L = I_σ \oplus B + I_σ \ominus B - 2I$$
    - iii. Zerocrossings removal in smooth regions
  - Evaluation comparing with the edge operator: $$M = (I_0 \oplus B) - (I_0 \ominus B)$$
    
### 2. Interest Point Detection
  - **Angle**: 
    - Implementation of Harris-Stephens method 
    - Implementation of Harris-Laplacian for mutliscale
  - **Blobs**:
    - Use of Hessian Matrix of the derivatives of L
    - Hessian-Laplace for multiscale 
  - **Box Filters**: 
    - Speed Up Hessian matrix calculation  

### 3. Image Classification:
  - HOGS
  - SURF
