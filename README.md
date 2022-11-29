# Project part 1

Bioinformatics 

## Task 1 Run FindTelomeres.py in interactive mode

cd /project/devs/
cd test
ls
module avail
qsub -I -P devs
cd /project/devs/test/
module load python/3.7.2
python FindTelomeres.py APSI_v2.hap1_masked.fasta

## Task 2 Write PBS script reference quast script

exit
cd /project/devs/
cd HPC_training
cd scripts            #use quast scripts
cat quast.pbs
 
#!/bin/bash
#PBS -P devs
#PBS -N FindTelomeres
#PBS -l select=1:ncpus=2:mem=1GB
#PBS -l walltime=00:15:00
#PBS -e findtelomeres_error.txt
#PBS -o telomeres_output.txt
#PBS -m abe

#Load modules
module load python/3.7.2
cd $PBS_O_WORKDIR
python FindTelomeres.py APSI_v2.hap1_masked.fasta > output1.txt

module unload python/3.7.2

