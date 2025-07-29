# Quantum Simulation of the Schwinger Model with VQE

This project represents my research exploration during my first days of my stay at **DESY** – the **Deutsches Elektronen-Synchrotron** – within the **Center for Quantum Technologies and Applications (CQTA)**. It reflects an early-stage, hands-on implementation aimed at investigating how modern quantum algorithms, specifically the **Variational Quantum Eigensolver (VQE)**, can be used to simulate quantum field theories such as the **Schwinger Model**.

This simulation serves both as a learning foundation and as a stepping stone toward more complex quantum simulations of gauge theories and lattice field models. While the implementation remains a numerical and exploratory prototype, it illustrates how hybrid quantum-classical approaches can be leveraged for strongly interacting systems, even on today's limited quantum hardware.

**The Cauchy-Schwarz Inequality**

```math
\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
```

---

## 📚 Theoretical Background

The **Schwinger Model** describes quantum electrodynamics in one spatial and one temporal dimension, involving a single Dirac fermion interacting via a U(1) gauge field. Despite its simplicity, the model shares key features with quantum chromodynamics (QCD), such as:

- **Confinement**
- **Chiral symmetry breaking**
- **Topological effects**, including a **θ-term** inducing rich phase structure

In particular, at θ = π and large fermion mass \( m/g \), the model exhibits a **first-order quantum phase transition**, where the electric field and particle number observables change discontinuously. This makes the Schwinger model an ideal benchmark for studying the potential of quantum simulation methods in addressing strongly correlated field theories.

---

## 🧮 Discretization and Mapping to Qubits

To simulate the Schwinger model on a quantum computer, the continuum theory is discretized on a 1D lattice using either:

- **Wilson fermions**: Break chiral symmetry explicitly to avoid fermion doubling; mapped to 2 qubits per site.
- **Staggered fermions**: Distribute Dirac components across alternating sites; mapped to 1 qubit per site.

Gauge fields are integrated out using Gauss’s law, resulting in a **purely fermionic Hamiltonian**. Fermionic degrees of freedom are then mapped to qubits using the **Jordan-Wigner transformation**, producing a spin model that encodes the gauge-invariant dynamics of the Schwinger theory.

---

## 🧠 Variational Quantum Eigensolver (VQE) Approach

### Objective
The VQE is used to approximate the ground state of the lattice Schwinger Hamiltonian by minimizing the energy expectation value over a parameterized quantum circuit.

### Ansatz Circuits
Two types of ansätze are explored, inspired by the paper:
- **Brick and ladder architectures** with configurable layer depth
- **Parametric gates**:  
  - **SO(4)** gates (more expressive, but do not conserve charge)  
  - **RXX + RYY** gates (charge-conserving, less expressive)

Penalty terms are used when needed to enforce Gauss’s law and charge neutrality.

### Optimization Strategy
- Classical simulation of VQE with **L-BFGS-B** optimizer
- Warm-start phases and layer-wise parameter updates
- Fidelity checks against exact diagonalization

---

## 🧪 Observables

The following quantities are computed to characterize the ground state and identify phase transitions:
- **Electric field density** \( \langle L \rangle \)
- **Particle number** \( \langle P \rangle \) (related to chiral condensate)
- Both are used to detect discontinuities across the θ = π line, indicative of a **first-order phase transition**

---

## 🧰 Technologies and Tools

- Python 3.8+
- Qiskit / PennyLane (choose as applicable)
- NumPy, SciPy, Matplotlib
- Jupyter Notebooks
- [Optional] IBM Q or local simulator backend

---

## 🛠️ Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/your-username/schwinger-vqe-simulation.git
cd schwinger-vqe-simulation
pip install -r requirements.txt



