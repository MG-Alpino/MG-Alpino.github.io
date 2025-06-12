---
layout: post
title: "Classifying Quantum Phase Transitions via Machine Learning in the XXZ-1/2 Model"
subtitle: "Poster presented at the III Workshop on Quantum Information and Thermodynamics – CBPF"
date: 2025-06-12
author: Marcos Gabriel Alpino
tags: [quantum information, machine learning, XXZ model, tensor networks]
---

## Motivation

- Investigate quantum correlations and the entanglement spectrum in the XXZ-1/2 spin chain model.
- Employ tensor network techniques, specifically the Variational Uniform Matrix Product State (VUMPS) algorithm, to determine the ground state.
- Use supervised machine learning methods (MLP and k-NN) to classify quantum phases and detect phase transitions based on entanglement data.
- Demonstrate that ML techniques can effectively classify phases in many-body quantum systems, achieving accuracies of 90% (MLP) and 98% (k-NN).

---

## VUMPS for the XXZ-1/2 Model

The Hamiltonian of the system is given by:

\[
H(\Delta) = -\sum_i \left(S^x_i S^x_{i+1} + S^y_i S^y_{i+1} + \Delta S^z_i S^z_{i+1} \right)
\]

The ground state is computed using the VUMPS algorithm, which represents the infinite system as a uniform MPS. The energy is variationally minimized under a canonical form, updating tensors until convergence is reached.

Key steps include:
- Decomposing the wavefunction via SVD into MPS format.
- Using variational principles to update tensors \( A_L, A_R, A_c \).
- Solving non-homogeneous linear equations for energy contributions.
- Employing convergence criteria: \( \|A_L C - A_c\| < \epsilon \), etc.

---

## Entanglement and Input Features

From the converged VUMPS state:
- The **entanglement spectrum** is extracted by Schmidt decomposition across bipartitions.
- The **von Neumann entropy** is computed for reduced states of up to six contiguous sites.
- These quantities form the **input features** for machine learning classification.

---

## Supervised Learning Methods

Two algorithms were used:

### 1. Multi-Layer Perceptron (MLP)
- Architecture: 32 → 128 → 64 → 2 neurons
- Activation: ReLU + Softmax
- Optimizer: ADAM via Flux.jl
- Dataset split: 70% training, 15% validation, 15% test

### 2. k-Nearest Neighbors (k-NN)
- Uses a kd-tree to classify new data points based on their entanglement features
- Achieved best performance in phase classification near criticality

---

## Results

- **MLP accuracy**: ~90%
- **k-NN accuracy**: ~98%
- Smooth learning and accuracy curves demonstrate effective training.
- The k-NN prediction probability as a function of \(\Delta\) maps out the phase diagram.

---

## Perspectives

- Extend to **unsupervised learning** techniques to identify phases without prior labels.
- Analyze other quantum correlation measures, such as **multipartite entanglement**.
- Apply the methodology to more complex systems like the **Hubbard** and **Extended Hubbard** models.

---

## References

ZAUNER-STAUBER, V. *et al*. Variational optimization algorithms for uniform matrix product states. *Physical Review B*, v. 97, n. 4, 2018. DOI: [10.1103/PhysRevB.97.045145](https://doi.org/10.1103/PhysRevB.97.045145)

---

## Acknowledgments

Financial support was provided by **CNPq**, under process number 131985/2023-0. We also thank the Physics Department at UFMG and the **Quantum Information Group (InfoQ)** for their support.

📧 marcosgabrielfisica@gmail.com  
🔬 Presented at the III Workshop on Quantum Information and Thermodynamics, CBPF – 2025
