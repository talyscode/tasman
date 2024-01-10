
# TASMAN
TASMAN is a statistical software package for the TALYS nuclear model code. The most important features are:
  - uncertainty distributions and covariance matrices for TALYS results, through Monte Carlo sampling of TALYS nuclear model parameters 
  - parameter sensitivity profiles for TALYS output
  - automatic optimization ('search') of TALYS nuclear model parameters to experimental nuclear reaction data and data from nuclear data libraries
  - Total Monte Carlo: generation of a statistical ensemble of complete nuclear data libraries for uncertainty propagation

## Documentation and reference
A description of the code and its options can be found in the [TASMAN Tutorial (pdf)](https://github.com/arjankoning1/tasman/blob/main/doc/tasman.pdf).
The reference to be used for TASMAN is

A.J. Koning, D. Rochman, J.-Ch. Sublet, N. Dzysiuk, M. Fleming, and S. van der Marck, *TENDL: Complete Nuclear Data Library for innovative Nuclear Science and Technology*, Nuclear Data Sheets 155,1 (2019).

## Installation

### Prerequisites:

The following are the prerequisites for compiling TASMAN:
  - git (only if the package is downloaded via Github)
  - a recent Fortran compiler such as gcc (gfortran)
  - a successful installation of the TALYS nuclear model code
  - for Total Monte Carlo: a successful installation of the TEFAL code for ENDF-6 formatting.

### Downloads:

To download TASMAN, you can use one of the following options:
#### 1. Download the entire tar file:
```
https://nds.iaea.org/talys/tasman.tar
tar zxf tasman.tar
```

#### 2. Using git:
```
git clone https://github.com/arjankoning1/tasman.git
```
The TASMAN parameter distribution database and sample cases do not fall under the git repository. Hence, to get a  working system you need to download
```
https://nds.iaea.org/talys/parameters.tar
https://nds.iaea.org/talys/tasmansamples.tar
```
and after
```
tar zxf parameters.tar
tar zxf tasmansamples.tar
```
you should move both *parameters/* and *samples/* to the *tasman/* directory.
### Installation instructions :

To install TASMAN, you can use one of the following options:
#### 1. Using make:
```
cd tasman/source
make
```
#### 2. Using the code_build script:
```
cd tasman
code_build tasman
```

The above will produce a *tasman* executable in the *tasman/bin* directory. 
The compiler and its flags can be set in either the *source/Makefile* or in *code_build*.

## The TASMAN package

The *tasman/* directory contains the following directories and files:

+ `README.md` this README file
+ `LICENSE` the License file
+ `code_build` and `path_change` installation scripts
+ `source/` the Fortran source code of TASMAN and the Makefile
+ `bin/` the executable after successful installation
+ `misc/` files with TASMAN input settings which can be used if needed
+ `doc/` the tutorial in pdf format
+ `samples/` the input and output files of the sample cases, and the *verify* script to run the sample cases

In total, you will need about 2.5 Gb of free disk space to install TASMAN.

### Often used databases

Depending on the particular use of TASMAN, a few other important directories may need to be linked, usually for the purpose of automatic optimization of TALYS nuclear model parameters:

+ `exfortables/` an experimental nuclear reaction database based on EXFOR, providing experimental nuclear reaction data sets in a directory-structured format.
+ `libraries/` a database with the most important nuclear reaction libraries in a directory-structured format.

### Miscellaneous options

The above is enough for the standard use of TASMAN. There are a few not often used features which require installation of an extra subdirectory in *tasman/*:

+ `parameters/` numerical probability distributions of TALYS nuclear model parameters on the basis of Bayesian Monte Carlo, see A.J. Koning, *Bayesian Monte Carlo method for nuclear data evaluation*, Eur. Phys. Journ. A51(12) 1 (2015). Download *parameters.tar* to *tasman/*, do *tar zxf parameters.tar* which will produce a *tasman/parameters/* directory
+ `PSF/` a database with experimental photon strength functions, for fitting of TALYS nuclear model parameters. Download *PSF.tar* to your home directory, do *tar zxf PSF.tar* which will produce a *PSF/* directory

## Sample cases

The sample cases serve to provide examples of the use of TASMAN and to verify a successful installation. The *samples/* directory contains various sample cases with a subdirectory *org/* with our results and a subdirectory *new/* with the results produced by the user. The entire sample set will take about 1 hour.
```
cd samples
./verify
```

You may create your own input file, e.g. *tasman.inp* after which TASMAN works as follows:
```
tasman < tasman.inp > tasman.out
```
assuming that *tasman* is linked to the *tasman/bin/tasman* executable.

## License and Copyright
This software is distributed and copyrighted according to the [LICENSE](LICENSE) file.
