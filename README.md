# Schwinger Model Simulation with VQE

This repository contains a Jupyter Notebook, **`Simulation.ipynb`**, implementing a numerical simulation of the Schwinger model using the Variational Quantum Eigensolver (VQE) algorithm. The implementation follows and extends the methodology presented in [1].

## Scientific Overview

The Schwinger model is a (1+1)-dimensional version of quantum electrodynamics (QED) describing massive Dirac fermions interacting via a U(1) gauge field. Despite its lower dimensionality, it exhibits non-trivial quantum field theoretic features such as confinement and chiral symmetry breaking, making it a paradigmatic testbed for quantum simulation.

This project focuses on approximating the ground state energy and associated observables of the discretized Hamiltonian using a quantum–classical hybrid approach.  

The workflow includes:
- Derivation of the discretized Hamiltonian using Wilson’s formulation.  
- Mapping fermionic operators to Pauli operators via the Jordan–Wigner transformation.  
- Construction of variational ansatz circuits.  
- Application of the VQE algorithm to estimate the ground state.  
- Reliability assessment through:
  - Exact diagonalization of the Hamiltonian for small system sizes.  
  - Fidelity comparison between the exact lowest-energy eigenstate and the variational state obtained from the optimized ansatz.  

## Algorithmic Approach

The Variational Quantum Eigensolver (VQE) algorithm is employed with two ansatz choices:
- SO(4) circuit  
- R_{XX+YY} circuit  

The cost function is the expectation value of the Hamiltonian with respect to the parameterized state. Optimization is performed classically, while expectation values are computed using quantum circuits.

Key observables analyzed:
- Ground state energy  
- Electric field operator  
- Particle number operator  

The obtained variational states are benchmarked against exact solutions to validate the accuracy of the method.

## Features

- Formulation of the Schwinger model on a lattice via Wilson discretization.  
- Explicit construction of the Hamiltonian in terms of Pauli operators.  
- Implementation of multiple variational ansatzes.  
- Hybrid quantum–classical optimization loop.  
- Reliability validation via exact diagonalization and fidelity analysis.  
- Visualization of convergence and physical observables.  

## Repository Structure

```
├── Simulation.ipynb   # Main notebook containing the implementation
├── requirements.txt   # Dependencies for running the notebook
└── README.md          # Project documentation
```

## Requirements

Dependencies are listed in `requirements.txt`. Install them with:  
```bash
pip install -r requirements.txt
```

## Usage

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Launch the notebook:
   ```bash
   jupyter notebook Simulation.ipynb
   ```

## Results

The notebook produces:
- Energy convergence plots for different ansatzes.  
- Comparison of VQE energies with exact diagonalization results.  
- Fidelity between the optimized ansatz state and the exact ground state.  
- Expectation values of observables (electric field, particle number).  

These results validate the capability of VQE to capture the non-trivial physics of the Schwinger model.

## Future Directions

- Scaling to larger lattice sizes beyond exact diagonalization feasibility.  
- Exploration of alternative ansatz families.  
- Benchmarking against other quantum algorithms (e.g., QAOA, QITE).  
- Extension to higher-dimensional or non-Abelian lattice gauge theories.  

## References

[1] Takis Angelides, Pranay Naredi, Arianna Crippa, Karl Jansen, Stefan Kühn, Ivano Tavernelli, Derek S. Wang, *First-Order Phase Transition of the Schwinger Model with a Quantum Computer*. arXiv:2312.12831 (2023). https://arxiv.org/abs/2312.12831




