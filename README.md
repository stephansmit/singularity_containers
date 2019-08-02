# Singularity containers for SU2

Containers to run [SU2](https://su2code.github.io/) with [Open MPI](https://www.open-mpi.org/) version 1.10.2.

## Pull a container
~~~~
singularity pull shub://stephansmit/su2_containers:master
~~~~

## Run Local
~~~~
mpirun -np 6 singularity exec su2_containers_master.sif /SU2/bin/SU2_CFD SU2.cfg > log.txt
~~~~


## Run SurfSara
~~~~
#!/bin/bash
#SBATCH -N 2
#SBATCH -p normal
#SBATCH -n 40

module load mpi/openmpi/1.10.2
mpirun --hostfile hostfile.txt -np 40 singularity exec su2_containers_master.sif /SU2/bin/SU2_CFD SU2.cfg > log.txt
~~~~
