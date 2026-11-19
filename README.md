# Magnetic-Levitation-Control-System---State-Space-Modeling-Validation

This project applies linear systems and state-space control theory to a magnetic levitation (MagLev) ball system. The objective is to model the nonlinear dynamics, linearize the system around a hovering operating point, analyze its properties, and design a state-feedback controller that stabilizes the ball.
Project objectives
- Derive the nonlinear equation of motion from a free-body diagram.
- Linearize the nonlinear model using Jacobian/Taylor-series linearization.
- Form the continuous-time state-space model.
- Analyze open-loop stability.
- Verify controllability and observability.
- Design and verify a full-state feedback controller.
- Compare open-loop and closed-loop responses using MATLAB.
System model
The magnetic force is modeled as:
\[
F_{\mathrm{mag}}(x,i)=k_m\left(\frac{i}{x}\right)^2
\]
Using downward as the positive direction, Newton's second law gives:
\[
m\ddot{x}=mg-F_{\mathrm{mag}}(x,i)
\]
Therefore, the nonlinear equation is:
\[
\ddot{x}=g-\frac{k_m}{m}\frac{i^2}{x^2}
\]
The system is linearized around the equilibrium operating point:
\[
X_0=0.05\ \mathrm{m},\qquad I_0=1.0\ \mathrm{A}
\]
with:
\[
g=9.81\ \mathrm{m/s^2}
\]
Linearized state-space model
The states are:
\[
\delta x=
\begin{bmatrix}
\text{position deviation}\\
\text{velocity deviation}
\end{bmatrix}
\]
The linearized model is:
\[
\delta\dot{x}=A\delta x+B\delta u
\]
\[
\delta y=C\delta x+D\delta u
\]
For the specified operating point:
\[
A=
\begin{bmatrix}
0&1\\
392.4&0
\end{bmatrix},\qquad
B=
\begin{bmatrix}
0\\
-19.62
\end{bmatrix}
\]
\[
C=\begin{bmatrix}1&0\end{bmatrix},\qquad D=0
\]
The output sensor measures position deviation only.
Open-loop analysis
The open-loop eigenvalues are:
\[
\lambda(A)=\pm\sqrt{392.4}\approx\pm19.81
\]
Because one eigenvalue is positive, the open-loop MagLev system is unstable.

The controllability and observability matrices are:
\[
\mathcal{C}=\begin{bmatrix}B&AB\end{bmatrix}
\]
\[
\mathcal{O}=\begin{bmatrix}C\\CA\end{bmatrix}
\]
For this system:
rank(Controllability) = 2
rank(Observability)   = 2
Since the system has two states, it is completely controllable and completely observable.
State-feedback controller
The controller is:
\[
\delta u=-K\delta x
\]
where:
\[
K=\begin{bmatrix}k_1&k_2\end{bmatrix}
\]
The closed-loop matrix is:
\[
A_{cl}=A-BK
\]
For desired closed-loop poles \(\lambda_1\) and \(\lambda_2\), the analytical gains are:
\[
k_2=\frac{\lambda_1+\lambda_2}{19.62}
\]
\[
k_1=-\frac{392.4+\lambda_1\lambda_2}{19.62}
\]
The analytical result should be verified using MATLAB's place function after the manual derivation.
MATLAB usage
Run the main script from MATLAB:
EE210
The script should calculate:
- State-space matrices \(A\), \(B\), \(C\), and \(D\)
- Open-loop eigenvalues
- Controllability matrix and rank
- Observability matrix and rank
- Analytical feedback gains
- Closed-loop eigenvalues
- Open-loop and closed-loop response plots
Suggested repository structure
EE210-MagLev/
├── README.md
├── EE210.m
└── figures/
    ├── open_loop_response.png
    └── closed_loop_response.png
Requirements
- MATLAB
- Control System Toolbox for ss, tf, and place
Current status
- Nonlinear ODE derived
- Jacobian linearization completed
- State-space matrices calculated
- Open-loop stability analyzed
- Controllability and observability verified
- State-feedback controller ready for pole selection and simulation
Author
Henry Ngo

EE210 - Linear Systems Theory
