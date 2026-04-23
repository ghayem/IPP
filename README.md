# IPP

MATLAB implementation related to **IPP (Iterative Proximal Projection)** for sparse signal recovery from noisy underdetermined measurements.

This repository is based on the paper:

**Fateme Ghayem, Mostafa Sadeghi, Massoud Babaie-Zadeh, Saikat Chatterjee, Mikael Skoglund, Christian Jutten**  
**“Sparse Signal Recovery Using Iterative Proximal Projection”**  
IEEE Transactions on Signal Processing, 2017

Paper: [IPP_TSP_2017.pdf](https://ghayem.github.io/files/IPP_TSP_2017.pdf)

---

## Overview

This project studies sparse recovery from noisy linear measurements of the form

**y = A x + w**

where:
- `x` is an unknown sparse signal,
- `A` is the sensing matrix,
- `y` is the measurement vector,
- and `w` is noise.

The paper considers constrained sparse recovery problems of the form

**minimize** `J(x)` **subject to** `||y - A x||_2 <= epsilon`

where `J(x)` is a sparsity-promoting penalty, potentially non-smooth and non-convex.

The main contribution is an efficient algorithm based on:
- an alternating minimization penalty method,
- proximal updates,
- projection onto the data-fidelity constraint,
- and an extrapolation step to accelerate convergence.

The repository also includes code for comparing IPP-related methods against several other sparse recovery solvers.

---

## Repository contents

- `Algorithms/` — implementations of IPP-related methods and comparison solvers
- `Test_OurNormalization.m` — main experiment script for comparing sparse recovery algorithms
- `README.md` — repository description

Inside `Algorithms/`, the repository includes subfolders such as:

- `IPP_and_ISP`
- `EM_GM_AMP`
- `EPIHT`
- `GOMP`
- `IMAT`
- `SCAD`
- `SCSA`
- `Other Solvers`
- `YALL1_v1.4`

This makes the repository useful both for running the proposed method and for benchmarking it against alternative algorithms.

---

## Method summary

The paper focuses on sparse signal recovery using a non-convex sparsity-promoting objective under an error constraint.

The proposed IPP framework is built around two key ingredients:

1. **Proximal step**  
   A sparsity-promoting subproblem is handled through a proximal update.

2. **Projection step**  
   The iterate is projected back toward the feasible set defined by the measurement constraint.

These steps are repeated iteratively, which leads to an **iterative proximal-projection** strategy.

In addition, the paper introduces an **extrapolation step** inspired by accelerated gradient methods to improve practical performance.

The paper reports that the resulting algorithm performs strongly on both synthetic sparse recovery tasks and real-data experiments, and compares favorably with several well-known baselines.

---

## What is included in this repository

This repository is not only a minimal implementation of one single solver. It also contains an experimental framework for comparing IPP-related methods with several alternatives.

From the main test script, the compared methods include examples such as:

- IPP/ISP-based variants
- EM-GM-AMP
- SCSA-FIT
- GOMP
- SCAD-based recovery

The script computes metrics such as:
- reconstruction SNR,
- squared error,
- support recovery rate,
- and runtime.

