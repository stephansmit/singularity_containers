# Singularity containers for SU2

Containers to run SU2 with openmpi 1.10.2.

To pull a container

~~~~
singularity pull shub://stephansmit/su2_containers:master
~~~~

## Local
~~~~
mpirun -np 6 singularity exec su2_containers_master.sif /SU2/bin/SU2_CFD SU2.cfg > log.txt
~~~~


## SurfSara
~~~~
#!/bin/bash
#SBATCH -N 2
#SBATCH -p normal
#SBATCH -n 40

module load mpi/openmpi/1.10.2
mpirun --hostfile hostfile.txt -np 40 singularity exec su2_containers_master.sif /SU2/bin/SU2_CFD SU2.cfg > log.txt
~~~~
