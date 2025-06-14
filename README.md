# Counterexamles-to-a-conjecture-of-Faudree-and-Schelp
A repository to maintain the code used to find new counterexamples to a conjecture by Faudree and Schelp.

The latest version of this program can be obtained from <https://github.com/AGT-Kulak/Counterexamples-Faudree-Schelp.git>.

This codebase filters graphs that are hamiltonian-connected and satisfy ${\mathfrak P}_k$ for every $2\leq k \leq n$. It makes use of datastructures and methods from [`nauty`](https://pallini.di.uniroma1.it/), [`plantri`](https://users.cecs.anu.edu.au/~bdm/plantri/), [`snarkhunter`](https://caagt.ugent.be/cubic/)  and [`K2-Hamiltonian Graphs`](https://github.com/JarneRenders/K2-Hamiltonian-Graphs). The verification implementation is derived from [`hamiltonian_cycles`](https://github.com/JorikJooken/hamiltonian_cycles).

## Installation

This requires a working shell and `make`.

- Download, extract, configure and compile [`nauty`](https://pallini.di.uniroma1.it/) in /nauty.
- Download, extract, configure and compile [`plantri`](https://users.cecs.anu.edu.au/~bdm/plantri/) in /plantri.
- Compile the code in this package using: 
	* `make all` to create a binary

## Usage

To allow easy usage the binaries are packaged in shellscripts that automatically set nessecary compliant settings.

### Usage of faudreeSchelp

Usage: `bash faudreeSchelp.sh n plantri-args`

Generates a category of graphs with plantri and filters those that are hamiltonian-connected and dont't satisfy ${\mathfrak P}_k$ for every $n/2+1\leq k \leq n$

The order of the arguments here is important.
```
  n                         the order of the graphs to check
  plantri-args              the arguments passed on to plantri. Insert quotes if multiple argument must be given (eg. '-p -c4')
```

### Usage of faudreeSchelp_all

Usage: `bash faudreeSchelp_all.sh n plantri-args`

Generates a category of graphs with plantri and filters those are hamiltonian-connected

The order of the arguments here is important.
```
  n                         the order of the graphs to check
  plantri-args              the arguments passed on to plantri. Insert quotes if multiple argument must be given (eg. '-p -c4')
```

### Usage of faudreeSchelp_any

Usage: `bash faudreeSchelp_any.sh n plantri-args`

Generates a category of graphs with plantri and filters those are hamiltonian-connected and do not satisfy ${\mathfrak P}_k$ for every $2\leq k \leq n$

The order of the arguments here is important.
```
  n                         the order of the graphs to check
  plantri-args              the arguments passed on to plantri. Insert quotes if multiple argument must be given (eg. '-p -c4')
```

### Usage of faudreeSchelp_full

Usage: `bash faudreeSchelp_full.sh n plantri-args`

Generates a category of graphs with plantri and filters those are hamiltonian-connected and satisfy ${\mathfrak P}_k$ for every $2\leq k \leq n$

The order of the arguments here is important.
```
  n                         the order of the graphs to check
  plantri-args              the arguments passed on to plantri. Insert quotes if multiple argument must be given (eg. '-p -c4')
```

### Usage of faudreeSchelp_non_planar

Usage: `bash faudreeSchelp_non_planar.sh n geng-args`

Generates a category of graphs with geng and filters those that are hamiltonian-connected and do not satisfy ${\mathfrak P}_k$ for every $n/2+1\leq k \leq n$

The order of the arguments here is important.
```
  n                         the order of the graphs to check
  geng-args                 the arguments passed on to geng. Insert quotes if multiple argument must be given (eg. '-C -m4')
```

### Usage of faudreeSchelp_non_planar_all

Usage: `bash faudreeSchelp_non_planar_all.sh n geng-args`

Generates a category of graphs with geng and filters those that are hamiltonian-connected

The order of the arguments here is important.
```
  n                         the order of the graphs to check
  geng-args                 the arguments passed on to geng. Insert quotes if multiple argument must be given (eg. '-C -m4')
```

### Usage of faudreeSchelp_non_planar_any

Usage: `bash faudreeSchelp_non_planar_any.sh n geng-args`

Generates a category of graphs with geng and filters those that are hamiltonian-connected and do not satisfy ${\mathfrak P}_k$ for every $2\leq k \leq n$

The order of the arguments here is important.
```
  n                         the order of the graphs to check
  geng-args                 the arguments passed on to geng. Insert quotes if multiple argument must be given (eg. '-C -m4')
```

### Usage of faudreeSchelp_non_planar_full

Usage: `bash faudreeSchelp_non_planar_full.sh n geng-args`

Generates a category of graphs with geng and filters those that are hamiltonian-connected and satisfy ${\mathfrak P}_k$ for every $2\leq k \leq n$
The order of the arguments here is important.
```
  n                         the order of the graphs to check
  geng-args                 the arguments passed on to geng. Insert quotes if multiple argument must be given (eg. '-C -m4')
```

### Examples

`bash faudreeSchelp.sh 16d '-d'`
Generates all planar cubic three-connected graphs on 16 vertices that are hamiltonian-connected but do not satisfy ${\mathfrak P}_k$ for every $n/2+1\leq k \leq n$

`bash faudreeSchelp.sh 17 '-p -m5'`
Generates all planar simple three-connected graphs on 17 vertices with minimum degree 5 that are hamiltonian-connected but do not satisfy ${\mathfrak P}_k$ for every $n/2+1\leq k \leq n$

`bash faudreeSchelp.sh 17 '-p -m5'`
Generates all planar simple three-connected graphs on 17 vertices with minimum degree 5 that are hamiltonian-connected but do not satisfy ${\mathfrak P}_k$ for every $n/2+1\leq k \leq n$

`bash faudreeSchelp_non_planar.sh 8 '-C'`
Generates all simple two-connected graphs on 8 vertices that are hamiltonian-connected but do not satisfy ${\mathfrak P}_k$ for every $n/2+1\leq k \leq n$

`bash faudreeSchelp_non_planar_all.sh 7 '-C'`
Generates all simple two-connected graphs on 7 vertices that are hamiltonian-connected

`bash faudreeSchelp_full.sh 12 '-p'`
Generates all planar simple three-connected graphs on 12 vertices that are hamiltonian-connected andsatisfy ${\mathfrak P}_k$ for every $2\leq k \leq n$

## Verification

An alternative (slower) implementation can be found in the subfolder "alternative-implementation"

This code can be compile using g++ using 

`g++ filterHasLargeGapInPariwisePathSpectrum.cpp -o filterHasLargeGapInPariwisePathSpectrumExecutable`

and

`g++ filterIsHamiltonianConnected.cpp -o filterIsHamiltonianConnectedExecutable`

Running the code to verify the number of graphs is done as follows (for example for order 8):

`../plantri/plantri -p -g 8 | ./filterIsHamiltonianConnectedExecutable | ./filterHasLargeGapInPariwisePathSpectrumExecutable | ../nauty/countg --n`
