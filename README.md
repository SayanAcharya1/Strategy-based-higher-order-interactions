# Strategy-Based Higher-Order Interactions

## Overview

This repository studies the coevolution of collective synchronization and cooperation in a population of coupled phase oscillators interacting through pairwise and higher-order interactions.

Pairwise interactions are represented by an Erdős–Rényi (ER) network, while higher-order interactions are represented by a random 3-uniform hypergraph. Cooperation evolves independently in the pairwise and higher-order interaction channels, allowing us to investigate how group interactions affect cooperation and synchronization.

The main objectives are to understand:

- How higher-order interactions influence the evolution of cooperation.
- How pairwise and higher-order cooperation respond to the cost of changing oscillator dynamics.
- How higher-order coupling and connectivity affect collective synchronization.
- Whether bistability and dependence on initial conditions occur.
- Whether higher-order interactions can sustain synchronization and cooperation under repulsive pairwise coupling.

## Model

### 1. Network structure

The population consists of \(N\) phase oscillators. Pairwise interactions are encoded by an adjacency matrix \(A_{ij}\), and higher-order interactions are encoded by a tensor \(B_{ijk}\), representing three-oscillator interactions.

The pairwise network is generated as an Erdős–Rényi random graph. The higher-order structure is a random 3-uniform hypergraph.

### 2. Phase dynamics

The phase \(\theta_i\) of oscillator \(i\) evolves according to a Kuramoto-type model with pairwise and higher-order coupling:

\[
\frac{d\theta_i}{dt}
=
\omega_i
+\lambda_1 s_i^p\sum_j A_{ij}
\sin(\theta_j-\theta_i)
+\lambda_2 s_i^h\sum_{j,k}B_{ijk}
\sin(2\theta_j-\theta_k-\theta_i).
\]

Here, \(\omega_i\) is the natural frequency, \(\lambda_1\) and \(\lambda_2\) are the pairwise and higher-order coupling strengths, and \(s_i^p,s_i^h\) denote the strategies associated with the two interaction channels.

**Note:** The precise normalization of the interaction sums, tensor convention, and strategy values should match the simulation code.

### 3. Evolutionary strategies

Each oscillator maintains separate strategies for pairwise and higher-order interactions. The two strategies can evolve independently, enabling the population to exhibit different levels of cooperation in the two channels.

The payoff associated with interaction channel \(q\), where \(q\in\{p,h\}\), is written as

\[
\Pi_i^q=r_i^q-\frac{\alpha c_i^q}{2\pi}.
\]

Here, \(r_i^q\) represents the synchronization-related benefit, \(c_i^q\) represents the cost associated with the oscillator's dynamical adjustment, and \(\alpha\) controls the cost strength.

Strategy updates use a Fermi-type rule:

\[
P(i\leftarrow j)
=
\frac{1}{1+\exp[-\beta(\Pi_j^q-\Pi_i^q)]},
\]

where \(\beta\) controls the sensitivity of strategy adoption to payoff differences.

The exact definitions of \(r_i^q\), \(c_i^q\), and the update procedure should be read together with the implementation.

## Observables

### Synchronization

Collective phase synchronization is measured by the Kuramoto order parameter:

\[
R(t)=\left|\frac{1}{N}\sum_{j=1}^{N}e^{i\theta_j(t)}\right|.
\]

Values of \(R\) close to zero indicate a largely incoherent state, whereas values close to one indicate strong phase synchronization.

### Cooperation

The cooperation levels in the pairwise and higher-order channels can be measured by the fractions of cooperative strategies:

\[
\rho_p=\frac{1}{N}\sum_{i=1}^{N}s_i^p,
\qquad
\rho_h=\frac{1}{N}\sum_{i=1}^{N}s_i^h,
\]

provided the strategy variables are encoded as zero or one, with one representing cooperation.

These observables allow synchronization and cooperation to be examined separately and jointly.

## Main Research Questions

The model is designed to investigate the following questions:

1. Can higher-order cooperation persist when pairwise cooperation declines?
2. How does the cost of dynamical adjustment affect cooperation in each interaction channel?
3. Can higher-order coupling expand the parameter region supporting synchronization?
4. Can the system exhibit bistability, with different long-term outcomes depending on initial conditions?
5. Can higher-order interactions support synchronization and cooperation even when pairwise coupling is repulsive?

## Simulation Parameters

The parameter values used in the study include the following explored ranges:

| Parameter | Values or range |
|---|---|
| Pairwise mean degree | 12 |
| Higher-order connectivity | \(h=0,6,8,12\) |
| Pairwise coupling | \(\lambda_1=0,1,5,10,15,25\) where specified in the parameter sweep |
| Cost strength | \(\alpha=10^{-3.5},10^{-2},10^{-1.5}\) |
| Fermi selection intensity | \(\beta=1\) |

The exact meaning of each parameter and the applicable parameter combinations should be verified against the simulation scripts. Other numerical settings, including population size, integration time step, transient duration, number of realizations, and random seeds, should be documented for reproducibility.

## Repository Contents

The repository will contain the source code, simulation scripts, and plotting routines used to reproduce the numerical results.

Suggested organization:

```text
Strategy-based-higher-order-interactions/
├── README.md
├── src/
│   └── simulation scripts
├── results/
│   └── numerical data
├── figures/
│   └── generated plots
└── LICENSE
```

This is a suggested structure; the actual directory names should reflect the files present in the repository.

## Running the Simulations

The simulations are implemented using Julia.

1. Install Julia from https://julialang.org/downloads/.
2. Clone the repository:

   ```bash
   git clone https://github.com/SayanAcharya1/Strategy-based-higher-order-interactions.git
   cd Strategy-based-higher-order-interactions
   ```

3. Open the appropriate Julia simulation script.
4. Install or activate the required packages, if necessary.
5. Run the script using the command documented for that script.

For example, once the correct script filename is known:

```bash
julia your_simulation_script.jl
```

Replace `your_simulation_script.jl` with the actual filename. Detailed commands and dependencies will be added after the source files are available.

## Reproducibility

For reproducible numerical results, the final documentation should specify:

- Julia version and required packages.
- Network and hypergraph construction procedures.
- Random-number seeds.
- Numerical integration method and time step.
- Transient removal and averaging windows.
- Parameter sweep ranges and number of realizations.
- Definitions of all reported observables.

## Citation

If you use this code in academic work, please cite the associated research article once its bibliographic details are available.

## Author

**Sayan Acharya**  
Physics and Applied Mathematics Unit  
Indian Statistical Institute, Kolkata, India

## License

A license has not yet been specified. Please add an appropriate `LICENSE` file before explicitly granting reuse or redistribution permissions.
