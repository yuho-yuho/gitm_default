# gitm_default
Default version of the Global Ionosphere/Thermosphere Model used by the Upper Atmosphere Group at University of Texas at Arlington.

GITM has been developed in Fortran-90. Original code and copyright by University of Michigan. Please refer to the paper by Ridley, Deng & Tóth (2006) at https://doi.org/10.1016/j.jastp.2006.01.008 and the GITM user manual at https://drive.google.com/file/d/14eLZuaxlNwpKO4sl0Ig7FmygDQa83Cvf/view?usp=sharing

Other useful links:

TACC LS6 User Guide: https://docs.tacc.utexas.edu/hpc/lonestar6/

## HPC Environments & Dependencies:

1. GITM runs on TACC machine (you can use different shells, e.g., bash, csh. I use bash myself). 
2. GITM needs MPI to work.
3. Choose one editor: emacs vs vim
4. Two ways to run GITM: batch job vs idev
5. What is Makefile and how it works?

## Quick Start:

1\. Clone the repository on your TACC Home directory

```shell
git clone https://github.com/yuho-yuho/gitm_default.git
```

2\. Go into the folder (You can change to whatever you want)

```shell
cd gitm_default
```

3\. Configure the Fortran compiler with ifort (By default)

```shell
./Config.pl -install -compiler=ifortmpif90 -earth
```

4\. Compile your GITM codes

```shell
gmake
cd src
```

Open the ModSize.f90 file and modify the 'nLons' and 'nlats' from x to 12:

```shell
integer, parameter :: nLons = 12
integer, parameter :: nLats = 12
```

Then return to the previous directory:

```shell
cd ..
```

5\. Create your run directory

```shell
make rundir
```

6\. Apply idev with 4 nodes & 144 mpi tasks

```shell
cd run
idev -m 10 -N 4 -n 144
```

Open the UAM.in file and modify the 'lons' and 'lats' from 2 to 12:

```shell
#GRID
12              lons
12              lats
```

7\. Run your GITM on idev (I use ibrun instead of mpirun)

```shell
ibrun ./GITM.exe
```

7\. Add these to .bashrc to run IDL everywhere

```shell
module load idl
export IDL_PATH='/scratch/tacc/apps/idl/8.4.0/idl/lib'
for d in $(find $IDL_PATH -type d); do
    IDL_PATH="$IDL_PATH:$d"
done

export IDL_PATH="$IDL_PATH:/home1/06793/hongyu_5/IDL_lib/srcIDL/"
export IDL_PATH="$IDL_PATH:/home1/06793/hongyu_5/IDL_lib/IDL_GITM/"
export IDL_STARTUP="/home1/06793/hongyu_5/IDL_lib/srcIDL/startup"
```

Please remember to modify the corresponding path, i.e., /home1/06793/hongyu_5/, with your own numbers and username.
















