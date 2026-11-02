# Strategy-based-higher-order-interactions

**Project home:**  
https://github.com/SayanAcharya1/Strategy-based-higher-order-interactions

Codes for numerical simulations in the work:

**“Coevolution of Synchronization and Cooperation with Pairwise and Higher-Order Interactions.”**


## Description

This repository contains simulation codes for studying the coevolution of cooperation and collective synchronization in populations of coupled phase oscillators with pairwise and higher-order interactions.

Pairwise interactions are represented by an Erdős–Rényi (ER) network, while higher-order interactions are modeled using a random 3-uniform hypergraph.

The model investigates how cooperation evolves independently across pairwise and higher-order interaction channels, and how higher-order interactions influence synchronization, cooperation, bistability, and collective behavior.

In particular, the simulations explore how higher-order cooperation can persist even when pairwise cooperation declines, and how group interactions can sustain collective synchronization over a broader range of pairwise coupling strengths, including under repulsive pairwise coupling.



## Model

The oscillator dynamics are governed by

$$\frac{d\theta_i}{dt} =
\omega_i
+\lambda_1 s_i^p\sum_j A_{ij}
\sin(\theta_j-\theta_i)
+\lambda_2s_i^h\sum_{j,k}B_{ijk}
\sin(2\theta_j-\theta_k-\theta_i).
$$

Here, $$A_{ij}$$ represents pairwise network connections, $$B_{ijk}$$ represents higher-order interactions, and $$s_i^p$$ and $$s_i^h$$ denote the pairwise and higher-order strategies, respectively.

Cooperation evolves through payoff-based strategy updates with a cost associated with dynamical adjustment.

---

## Files

The repository will contain:

- Simulation scripts for the evolutionary Kuramoto model.
- Network and hypergraph construction routines.
- Numerical data analysis and plotting codes.
- Scripts for exploring synchronization and cooperation across parameter spaces.

The exact filenames and descriptions will be updated as the simulation codes are uploaded.



## Requirements

- Julia
- Required Julia packages used in the simulation scripts.
- Standard numerical and scientific computing libraries.

The exact package dependencies and Julia version will be specified alongside the simulation codes.


## Author

**Sayan Acharya**  
Senior Research Fellow (SRF)  
Physics and Applied Mathematics Unit (PAMU)  
Indian Statistical Institute, Kolkata, India


## Citation

If you use the codes in this repository, please cite the associated research article when it becomes available.

Repository:  
https://github.com/SayanAcharya1/Strategy-based-higher-order-interactions

