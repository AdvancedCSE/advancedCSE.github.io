# Python Constitutive Model Driver

This is a Python code to test constitutive stress updates and associated computational plasticity algorithms. 

## Material Models

Model | Elementary | Intermediate | Difficult | Research-Grade
:------------ | :-------------: | :-------------: | :-------------: | :-------------:
von Mises (isotropic hardening)    								| 🗸 |                    |                    | 
von Mises (isotropic hardening), variational update <sup>[a](#myfootnote1)</sup>         |                    |                    |   				   | 🗸
Drucker-Prager 													|                    | 🗸 |                    |
Mohr-Coulomb                                                    |                    | 🗸 |					   |
Extended Mohr-Coulomb model<sup>[b](#myfootnote1)</sup>         |                    |                    |   				   | 🗸
Hardening soil model<sup>[b](#myfootnote1)</sup>                |                    |                    |   				   | 🗸
Concrete damage plasticity (Feenstra and De Borst)<sup>[c](#myfootnote2)</sup>               |                    |                    |   				   | 🗸
Concrete damage plasticity (Lee and Fenves)<sup>[c](#myfootnote2)</sup>                      |                    |                    | 				   | 🗸
[Burgers model](https://en.wikipedia.org/wiki/Burgers_material)<sup>[c](#myfootnote2)</sup>  |                    | 				      | 🗸 | 
[Glen power law model](https://en.wikipedia.org/wiki/Ice-sheet_dynamics)<sup>[c](#myfootnote2)</sup>  |           | 			          | 🗸 | 

---
<a name="myfootnote1">a</a>) Based on the following papers:

* Ortiz, M. and Stainier, L. "The variational formulation of viscoplastic constitutive updates." Computer Methods in Applied Mechanics and Engineering Volume 171, Issues 3–4, 9 April 1999, Pages 419-444.

* Miehe, Christian, Apel, Nikolas and Lambrecht, Matthias. "Anisotropic additive plasticity in the logarithmic strain space: modular kinematic formulation and implementation based on incremental minimization principles for standard materials." Computer Methods in Applied Mechanics and Engineering 191.47-48 (2002): 5383-5425.

<a name="myfootnote1">b</a>) Simplified version with only shear hardening mechanism; no pressure dependency, no Lode angle dependency

<a name="myfootnote2">c</a>) Not yet available; planned for inclusion in the near future

## Robust algorithms

* Complementarity smoothing of the loading-unloading (or Karush-Kuhn-Tucker) condition to avoid use of active set search in models with multiple-surfaces. 

* Global equilibrium solvers: pseudo-inverse, least-squares to handle rank-deficient consistent tangents (e.g., due to non-smooth or multiple yield surfaces).

## Ease of use

* Adaptive time stepping - time step cuts back when there is no convergence, increases when there is convergence.

* Abaqus-like input file:

	- overloaded keywords *CLOAD and *BOUNDARY to specify stress and strain boundary conditions, respectively
	- *AMPLITUDE keyword to specify time-varying amplitude functions
	- *PARAMETER keyword to specify variables and math expressions using these variables
    - *CONTROLS keyword to specify global equilibrium convergence parameters: maximum number of iterations and error tolerance

## Full documentation

* Line-by-line derivations of all equations (derivatives of yield functions, plastic potentials and residual equations) necessary for implementation are documented.

## Disclaimer

* The implemented models are for educational purposes to explore advanced solution algorithms and study yield and hardening mechanisms. 

* Certain assumptions have been invoked to simplify implementations of certain models. 

* Due to the advanced algorithms considered, certain models may not interface with the solvers in commercial finite element programs.



<!--- von Mises (metal) plasticity

* [Hosford model](https://en.wikipedia.org/wiki/Hosford_yield_criterion)

* Drucker-Prager

* Mohr-Coulomb

* Extended Mohr-Coulomb model<sup>[a](#myfootnote1)</sup> 

* Hardening soil model<sup>[a](#myfootnote1)</sup>


The following models are planned for inclusion in the near future:

* Concrete damage plasticity (Feenstra and De Borst)

* Concrete damage plasticity (Lee and Fenves)

* [Burgers model](https://en.wikipedia.org/wiki/Burgers_material)

* 
--->