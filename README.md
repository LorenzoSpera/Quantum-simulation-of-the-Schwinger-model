# Quantum simulation of the Scwhinger model 
This project represents my first research exploration during my first days of my stay at **DESY** – the **Deutsches Elektronen-Synchrotron** – within the **Center for Quantum Technologies and Applications (CQTA)**. It reflects an early-stage, hands-on implementation aimed at investigating how modern quantum algorithms, specifically the **Variational Quantum Eigensolver (VQE)**, can be used to simulate non-trivial quantum field theories such as the **Schwinger Model**.

This simulation serves both as a learning foundation and as a stepping stone toward more complex quantum simulations of gauge theories and lattice field models. While the implementation remains a numerical and exploratory prototype, it illustrates how hybrid quantum-classical approaches can be leveraged for strongly interacting systems, even on today's limited quantum hardware.

## 🧾 Theoretical Background: The Schwinger Model

The **Schwinger Model** is a (1+1)-dimensional quantum electrodynamics (QED) theory that describes the interaction of a single Dirac fermion field with a U(1) gauge field. Proposed by **Julian Schwinger** in the 1960s, it serves as a minimalistic yet rich toy model for studying several non-perturbative phenomena typically found in more complex quantum field theories, such as:

- **Confinement**: Even though it’s an Abelian theory, the Schwinger model exhibits confinement of electric charge, a feature usually associated with non-Abelian gauge theories like QCD.
- **Chiral Symmetry Breaking**: The model breaks chiral symmetry dynamically, another trait shared with QCD.
- **Anomaly Phenomena**: It demonstrates the axial anomaly, where classical symmetries are broken at the quantum level.

Due to its low dimensionality and exact solvability in the continuum, the Schwinger model is often used as a benchmark for testing non-perturbative methods such as lattice field theory and, more recently, **quantum simulations**.

### Discretization and Lattice Formulation

To make the Schwinger model suitable for quantum simulation, the theory is discretized on a one-dimensional spatial lattice using techniques from **lattice gauge theory**. The Hamiltonian can then be written in terms of **spin** and **bosonic** operators, often using:

- **Staggered fermions** to represent the Dirac field,
- **Kogut-Susskind formulation** for the lattice gauge field,
- **Gauss’s law** to eliminate the gauge degrees of freedom and obtain a purely fermionic/qubit Hamiltonian.

The resulting lattice Hamiltonian is:

\[
H = x \sum_n \left( \psi_n^\dagger e^{i \theta_n} \psi_{n+1} + \text{h.c.} \right)
+ \mu \sum_n (-1)^n \psi_n^\dagger \psi_n
+ \frac{g^2}{2} \sum_n L_n^2
\]

Where:
- \( \psi_n \) are fermionic annihilation operators,
- \( \theta_n \), \( L_n \) are the link variables and corresponding electric field operators,
- \( x \), \( \mu \), \( g \) are parameters related to the lattice spacing and physical constants.

Through a series of transformations (e.g., Jordan-Wigner), this Hamiltonian can be mapped onto a qubit representation suitable for execution on quantum devices or simulators.

### Relevance for Quantum Computing

The Schwinger model is a canonical example of how **quantum computers** can tackle problems that are classically intractable due to **exponential scaling** in Hilbert space. As a simple yet nontrivial gauge theory, it’s an ideal test case for **variational quantum algorithms** like VQE, where one seeks to approximate the ground state of a complex Hamiltonian using a parameterized quantum circuit.

By successfully simulating the Schwinger model, we build foundational knowledge for simulating more realistic high-energy physics models on quantum devices in the near future.


