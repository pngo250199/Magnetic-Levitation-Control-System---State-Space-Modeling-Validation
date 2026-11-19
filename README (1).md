# EE210 Magnetic Levitation State-Space Control

This project applies linear systems and state-space control theory to a magnetic levitation (MagLev) ball system. The objective is to model the nonlinear dynamics, linearize the system around a hovering operating point, analyze its properties, and design a state-feedback controller that stabilizes the ball.

## Project objectives

- Derive the nonlinear equation of motion from a free-body diagram.
- Linearize the nonlinear model using Jacobian/Taylor-series linearization.
- Form the continuous-time state-space model.
- Analyze open-loop stability.
- Verify controllability and observability.
- Design and verify a full-state feedback controller.
- Compare open-loop and closed-loop responses using MATLAB.

## System model

The magnetic force is modeled as:

<img width="215" height="64" alt="image" src="https://github.com/user-attachments/assets/a8e39dbf-1190-418a-9239-4f7754922167" />


Using downward as the positive direction, Newton's second law gives:

<img width="159" height="33" alt="image" src="https://github.com/user-attachments/assets/02f15ebd-7e6b-4720-8b9b-417d221c41a9" />


Therefore, the nonlinear equation is:

<img width="131" height="57" alt="image" src="https://github.com/user-attachments/assets/5456c138-6419-40cc-aebd-2f51102eb728" />


The system is linearized around the equilibrium operating point:

<img width="194" height="43" alt="image" src="https://github.com/user-attachments/assets/c15596b1-70d6-45b7-a8e2-c976a238252a" />


with:

<img width="98" height="38" alt="image" src="https://github.com/user-attachments/assets/1ee25907-8c48-4cc8-bab3-8bc9bffa2dfa" />


## Linearized state-space model

The states are:

<img width="175" height="53" alt="image" src="https://github.com/user-attachments/assets/9ed09310-8bb3-4f7b-974b-ca4553249745" />


The linearized model is:

<img width="118" height="70" alt="image" src="https://github.com/user-attachments/assets/bf131aa2-388c-4444-88a8-09037936eb06" />


For the specified operating point:

<img width="254" height="97" alt="image" src="https://github.com/user-attachments/assets/5a1ad484-6545-48e4-be0e-2591587f2606" />


The output sensor measures position deviation only.

## Open-loop analysis

The open-loop eigenvalues are:

<img width="179" height="35" alt="image" src="https://github.com/user-attachments/assets/53d2ea6f-438a-4a89-a7ac-bd35b50541fc" />


Because one eigenvalue is positive, the open-loop MagLev system is unstable.

The controllability and observability matrices are:

<img width="110" height="96" alt="image" src="https://github.com/user-attachments/assets/805add02-2a9e-4dc7-8abf-e69fa3248364" />


For this system:

```text
rank(Controllability) = 2
rank(Observability)   = 2
```

Since the system has two states, it is completely controllable and completely observable.

## State-feedback controller

The controller is:

<img width="89" height="31" alt="image" src="https://github.com/user-attachments/assets/c5b0e448-6618-4da2-a07c-7b62eeed1432" />


where:

<img width="98" height="25" alt="image" src="https://github.com/user-attachments/assets/bb011edb-57a5-4cc0-9fce-13a486eff7ec" />


The closed-loop matrix is:

<img width="104" height="31" alt="image" src="https://github.com/user-attachments/assets/3cff796d-390a-4c80-b643-98a60f9e7462" />


For desired closed-loop poles \(\lambda_1\) and \(\lambda_2\), the analytical gains are:

<img width="182" height="104" alt="image" src="https://github.com/user-attachments/assets/7ba86dd9-643f-44b9-be5e-b4cb3b2228b2" />


The analytical result should be verified using MATLAB's `place` function after the manual derivation.

## MATLAB usage

Run the main script from MATLAB:

```matlab
EE210
```

The script should calculate:

- State-space matrices \(A\), \(B\), \(C\), and \(D\)
- Open-loop eigenvalues
- Controllability matrix and rank
- Observability matrix and rank
- Analytical feedback gains
- Closed-loop eigenvalues
- Open-loop and closed-loop response plots

## Suggested repository structure

```text
EE210-MagLev/
├── README.md
├── EE210.m
└── figures/
    ├── open_loop_response.png
    └── closed_loop_response.png
```

## Requirements

- MATLAB
- Control System Toolbox for `ss`, `tf`, and `place`

## Current status

- Nonlinear ODE derived
- Jacobian linearization completed
- State-space matrices calculated
- Open-loop stability analyzed
- Controllability and observability verified
- State-feedback controller ready for pole selection and simulation

## Author

Henry Ngo

EE210 - Linear Systems Theory
