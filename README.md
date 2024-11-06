# gitm_default
Default version of the Global Ionosphere/Thermosphere Model used by the Upper Atmosphere Group at University of Texas at Arlington.

GITM has been developed in fortran-90. Original code and copyright by University of Michigan. Please refer to the paper by Ridley, Deng & Tóth (2006) at https://doi.org/10.1016/j.jastp.2006.01.008. 

Other useful links:

TACC LS6 User Guide: https://docs.tacc.utexas.edu/hpc/lonestar6/

## HPC Environments & Dependencies:

1. GITM runs on TACC machine. 
2. GITM needs MPI to work.

## Quick Start:

1\. Clone the repository and cd into the repo folder

```shell
git clone https://github.com/yuho-yuho/gitm_default.git
```

2\. Go into the repo directory

```shell
cd GITM
```

3\. Configure the Fortran compiler (version 10)

```shell
./Config.pl -install -earth -compiler=gfortran10
```
