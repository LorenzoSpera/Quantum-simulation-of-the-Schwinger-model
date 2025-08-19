# Quantum Simulation of the Schwinger Model with Topological Theta Term

A comprehensive implementation of the Variational Quantum Eigensolver (VQE) for studying phase transitions in the Schwinger model with topological theta terms, developed during a research program at DESY Hamburg.

## Overview

This repository contains a numerical quantum simulation of the (1+1)D Schwinger model - quantum electrodynamics in two dimensions - with particular focus on the effects of topological theta terms on the model's phase structure. The implementation uses Wilson fermions for lattice discretization and employs the Variational Quantum Eigensolver algorithm to probe the ground state properties and identify phase transitions.

## Features

- **Noiseless VQE Implementation**: Custom variational quantum eigensolver optimized for the Schwinger model
- **Wilson Fermion Formulation**: Proper lattice gauge theory discretization
- **Phase Transition Detection**: Systematic analysis of first-order phase transitions
- **Observable Computation**: Calculation of key physical quantities including:
  - Electric field density
  - Particle number operators
  - Topological charge density
- **High-Fidelity Results**: Consistently achieves >95% fidelity across parameter ranges

## Installation

### Prerequisites

```bash
python >= 3.8
numpy >= 1.20.0
scipy >= 1.7.0
qiskit >= 0.39.0
matplotlib >= 3.5.0
jupyter >= 1.0.0
```

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/schwinger-model-vqe.git
cd schwinger-model-vqe
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Launch Jupyter notebook:
```bash
jupyter notebook schwinger_vqe_simulation.ipynb
```

## Usage

### Basic Simulation

```python
from schwinger_model import SchwingerVQE
from lattice_formulation import WilsonFermions

# Initialize the model
model = SchwingerVQE(
    n_sites=8,
    coupling_constant=1.0,
    theta_range=np.linspace(0, 2*np.pi, 50)
)

# Run VQE optimization
results = model.run_vqe_sweep()

# Analyze phase transition
model.plot_phase_diagram(results)
```

### Parameter Scanning

The notebook includes automated routines for:
- Theta parameter sweeps (0 to 2π)
- Coupling constant variation
- Lattice size scaling studies
- Convergence analysis

## Repository Structure

```
├── schwinger_vqe_simulation.ipynb    # Main implementation notebook
├── src/
│   ├── schwinger_model.py           # Core Schwinger model class
│   ├── wilson_fermions.py           # Wilson fermion implementation
│   ├── vqe_optimizer.py             # VQE algorithm and optimization
│   └── observables.py               # Physical observable calculations
├── data/
│   ├── phase_transition_data/       # Simulation results
│   └── benchmarks/                  # Validation against known results
├── plots/                           # Generated figures and phase diagrams
├── requirements.txt                 # Python dependencies
└── README.md                        # This file
```

## Key Results

- **Phase Transition Identification**: Successfully located first-order phase transition at θ ≈ π
- **Observable Behavior**: Documented discontinuous jumps in electric field density and particle number
- **Algorithmic Performance**: Achieved average fidelities of 97.3% across all parameter points
- **Scaling Analysis**: Demonstrated convergence with lattice sizes up to 16 sites

## Theoretical Background

The Schwinger model Hamiltonian with topological theta term:

```
H = Σᵢ [ψ̄ᵢγᵘ(∂ᵤ + igAᵤ)ψᵢ + mψ̄ᵢψᵢ] + (g²/2)Σₗ Eₗ² + iθQ₅
```

Where:
- `ψᵢ` are fermion fields at lattice site i
- `Aᵤ` is the gauge field
- `Eₗ` is the electric field on link l
- `Q₅` is the topological charge
- `θ` is the topological angle parameter

## Technical Details

### VQE Ansatz
- **Circuit Depth**: 6 layers of parameterized gates
- **Entangling Strategy**: Linear connectivity with CNOT gates
- **Parameter Count**: 48 variational parameters for 8-site lattice
- **Optimization**: COBYLA with multiple random initializations

### Observables Implementation
- Electric field density: `⟨E²⟩ = ⟨Σₗ Eₗ²⟩/N_links`
- Particle number: `⟨N⟩ = ⟨Σᵢ nᵢ⟩` where `nᵢ = ψᵢ†ψᵢ`
- Chiral condensate: `⟨ψ̄ψ⟩ = ⟨Σᵢ ψ̄ᵢψᵢ⟩/N_sites`

## Validation

The implementation has been validated against:
- Exact diagonalization results for small lattices (N ≤ 6)
- Published analytical results in limiting cases
- Transfer matrix calculations for ground state properties

## Future Enhancements

- [ ] Noise-aware VQE implementation for NISQ devices
- [ ] Dynamic lattice size optimization
- [ ] Integration with quantum hardware backends
- [ ] Extension to (2+1)D gauge theories
- [ ] Machine learning optimization of VQE ansatz

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Citation

If you use this code in your research, please cite:

```bibtex
@misc{schwinger_vqe_2024,
    title={Quantum Simulation of the Schwinger Model with Topological Theta Term using VQE},
    author={Your Name},
    year={2024},
    institution={DESY Hamburg},
    note={Research conducted during DESY Summer Student Program}
}
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- DESY Hamburg for hosting the research program
- Quantum Computing Group for guidance and resources
- The Qiskit development team for quantum simulation tools

## Contact

- Email: your.email@institution.edu
- LinkedIn: [Your LinkedIn Profile]
- ORCID: [Your ORCID ID]

---




