# QAOA for Max-Cut in Qiskit

A Python implementation of the **Quantum Approximate Optimization Algorithm (QAOA)** to solve the **Max-Cut** problem on a class of random graphs using Qiskit.

## Overview

This notebook uses QAOA to find the maximum cut of an undirected graph $G$, and checks the result by a brute-force classical method. Namely:

1. Generate a random graph $G=G(n, p)$ on $n$ vertices where each edge is included independently with probability $p$ (configurable by the user). For simplicity, each edge is taken to have weight 1. This can be easily changed by the user if desired (and the remainder of the process will take that into account).
2. Express the Max-Cut objective function as a Hamiltonian, written as a sum of Pauli strings.
3. Construct the parameterized variational quantum circuit using Qiskit's `QAOAAnsatz`.
4. Evaluate the expectation of the Hamiltonian via `qiskit.primitives` (`StatevectorEstimator`) and optimize the circuit parameters using `scipy.optimize.minimize`. This gives an initial estimate for the max-cut value.
5. Sample bitstrings from the optimized state via `StatevectorSampler`, extract the candidate vertex partition, and calculate and plot the resulting graph cut.
6. Compute the true maximum cut value via brute-force search (suitable for small $n$) to verify and compare.

## Dependencies

The notebook uses the following packages:

* `qiskit`
* `numpy`
* `scipy`
* `rustworkx`
* `matplotlib`
* `pylatexenc` (for circuit drawing)


