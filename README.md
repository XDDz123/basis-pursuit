# Basis Pursuit
This project implements the basis pursuit and basis pursuit denoising techniques described in the paper [Stable Signal Recovery from Incomplete and Inaccurate Measurements](https://doi.org/10.48550/arXiv.math/0503066) by Emmanuel Candes, Justin Romberg, and Terence Tao. </br>
Basis pursuit is capable of recovering sparse or approximately sparse signals from undersampled and noisy measurements under the correct conditions. </br>
For instance, a signal with the length of 1024 could be recovered exactly from 300 datapoints.

## Mechanics 
To recover a signal with length 1024 with 300 measurements: </br>
1. We construct a measurement matrix $A$, described by the paper as a "300 × 1024 Gaussian measurement ensemble."</br>
In general, the measurement matrix $A$ can be defined by $A \in \mathbb{R}^{n\times m}$ that obeys the uniform uncertainty principle.</br>
The gaussian random matrix can be defined by the distribution $\mathcal{N}(\mu=0,~\sigma^2=\frac{1}{n})$.</br>

2. The minimization threshold $\epsilon$ is defined as $\epsilon^2 = \sigma^2(n + \lambda*\sqrt{2n})$

3. We are solving the following minimization problem for Basis Pursuit:  
$\text{min } \lVert x \rVert_{\ell_1} \text{ subject to } \lVert Ax - y \rVert_{\ell_2} \leq \epsilon$  
where $x$ is the recovered signal, $y = Ax_0$, and $\epsilon$ is defined as described previously. 


4. As for Basis Pursuit De-Noising,
$y$ is redefined as $y = Ax_0 + e$, where the error equals $e \sim \mathcal{N}(0,~\sigma^2)$. </br>
Therefore we have $\text{min } \lVert x \rVert_{\ell_1} \text{ subject to } \lVert Ax - (Ax_0 + e) \rVert_{\ell_2} \leq \epsilon$  

## Libraries
* numpy
* scipy
* cvxpy
* matplotlib

## Sample Output
### Basis Pursuit
<img src="https://github.com/XDDz123/basis-pursuit/assets/20507222/9dd3490f-4d1b-4a28-a0e6-83d8f9bcf4d7" width="635" height="743"> </br>
### Basis Pursuit De-Noising
<img src="https://github.com/XDDz123/basis-pursuit/assets/20507222/be489728-3bcd-45a2-89b5-c6ef49089ae4" width="635" height="743"> </br>
