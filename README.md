# Optical conductivity of phosphorene

Here we show how to calculate the optical conductivity of phosphorene using the tight-binding model and the Kubo formula.

## Theoretical approach

- Tight-binding Hamiltonian for phosphorene

The tight-binding Hamiltonian for phosphorene is given by \cite{rudenko2015}
$$H=\sum_{i}\varepsilon_ic_i^{\dag}c_i+\sum_{i\neq j}t_{ij}c_i^{\dag}c_j,$$
where the summation runs over all lattice sites, $\varepsilon_i$ is the on-site energy at site $i$, $t_{ij}$ is the hopping energy between sites $i$ and $j$, and $c_i^{\dag}$ ($c_j$) is the creation (annihilation) operator of an electron at site $i$ ($j$). Because all phosphorus atoms in the lattice are identical, for simplicity we set the on-site energy $\varepsilon_i$ to zero for all lattice sites. The Hamiltonian Eq. (S1) is constructed on the basis of the $p_z$ orbital of the phosphorus atom. It was shown in Ref. \cite{rudenko2015} that (i) the $p_z$ orbital gives the predominant contribution to the band structure of few-layer phosphorene in the low-energy region and (ii) with ten intralayer and five interlayer hopping parameters, this TB Hamiltonian can reproduce the band structure of few-layer phosphorene in the low-energy region as obtained by DFT-GW calculations. The ten intralayer hopping parameters (in units of eV) are $t_{1}=-1.486$, $t_{2}=+3.729$, $t_{3}=-0.252$, $t_{4}=-0.071$, $t_{5}=+0.019$, $t_{6}^{\|}=+0.186$, $t_{7}=-0.063$, $t_{8}=+0.101$, $t_{9}=-0.042$, $t_{10}=+0.073$ \cite{rudenko2015}.

- Kubo formula for optical calculation

## Numerical implementation

- Extensive utilization of Numpy and Scipy to speed up numerical calculation

- K-point (2D wavevector) parallelization for electronic bandstructure calculation

- E-point (photon energy) parallelization for optical conductivity calculation