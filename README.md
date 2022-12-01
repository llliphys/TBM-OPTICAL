# Optical conductivity of phosphorene

Here we show how to calculate the optical conductivity of phosphorene numerically using the tight-binding model and the Kubo formula. We use Python to implement the numerical algorithm, in particular we use highly efficient `Numpy` and `Scipy` for vectorization and built-in `Multiprocessing` for parallelization.

## Theoretical approach

- **Tight-binding Hamiltonian for phosphorene**

The tight-binding Hamiltonian for phosphorene is given by \cite{rudenko2015}

$$H=\sum_{i}\varepsilon_ic_i^{\dagger}c_i+\sum_{i\neq j}t_{ij}c_i^{\dagger}c_j,$$

where the summation runs over all lattice sites, $\varepsilon_i$ is the on-site energy at site $i$, $t_{ij}$ is the hopping energy between sites $i$ and $j$, and $c_i^{\dagger}$ ($c_j$) is the creation (annihilation) operator of an electron at site $i$ ($j$). Because all phosphorus atoms in the lattice are identical, for simplicity we set the on-site energy $\varepsilon_i$ to zero for all lattice sites. The Hamiltonian Eq. (S1) is constructed on the basis of the $p_z$ orbital of the phosphorus atom. It was shown in Ref. \cite{rudenko2015} that (i) the $p_z$ orbital gives the predominant contribution to the band structure of phosphorene in the low-energy region and (ii) with five hopping parameters, this TB Hamiltonian can reproduce the band structure of phosphorene in the low-energy region as obtained by DFT-GW calculations. The five hopping parameters (in units of eV) are $t_{1}=-1.486$, $t_{2}=+3.729$, $t_{3}=-0.252$, $t_{4}=-0.071$, and $t_{5}=+0.019$ \cite{rudenko2015}.

- **Kubo formula for optical calculation**


The optical conductivity tensor of phosphorene can readily be calculated by using the Kubo formula, which is given by \cite{li2019}


$$\sigma_{\alpha\beta}(\omega) = \frac{e^2\hbar}{2\pi^2i}\sum_{m, n}\int d\textbf{k} \frac{f[E_m(\textbf{k})] - f[E_n(\textbf{k})]}{E_m(\textbf{k}) - E_n(\textbf{k})} \frac{\bra{m\textbf{k}}{\textbf{v}_{\alpha}}\ket{n\textbf{k}}
\bra{n\textbf{k}}{\textbf{v}_{\beta}}\ket{m\textbf{k}}}{E_m(\textbf{k}) - E_n(\textbf{k}) + \hbar\omega + i\eta},$$

where $\alpha=x, y$ is the tensor index, $\omega$ is the optical frequency, $m$ is the band index, $\textbf{k}=(k_x, k_y)$ is the 2D wave vector, $f(E)$ is the Fermi-Dirac function, $E_{m}(\textbf{k})$ is the eigenenergy, $\ket{m\textbf{k}}$ is the eigenstate, $\textbf{v}_{\alpha}$ is the $\alpha$ component of the velocity operator $\textbf{v}=\hbar^{-1}\partial H/\partial \textbf{k}$, and $\eta$ is a finite broadening. There are four components in the optical conductivity tensor: $\sigma_{xx}$ and $\sigma_{yy}$ for the longitudinal optical conductivities and $\sigma_{xy}$ and $\sigma_{yx}$ for the transverse optical conductivities (or the optical Hall conductivities). For the longitudinal components we have $\sigma_{xx}=\sigma_{yy}$ ($\sigma_{xx}\neq\sigma_{yy}$) for an isotropic (anisotropic) system. 

## Numerical implementation

- Extensive utilization of Numpy and Scipy to speed up numerical calculation

- K-point (2D wavevector) parallelization for electronic bandstructure calculation

- E-point (photon energy) parallelization for optical conductivity calculation

## Functional scripts
- `sigma.py`: The script to first calculate the electronic band structure of phosphorene and on top of that to calculate the optical conductivity of phosphorene

- `plot.py`: The script to post-process (visualize) the numerical results obtained by `sigma.py`