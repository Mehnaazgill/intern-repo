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

## Task 2 Write PBS script from reference quast script

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

## Task 3 Running the written PBS script on hpc
1. Transferring file from local computer to remote computer using command line
Setup a command line sftp sesssion first

sftp>
sftp> lls
sftp> lcd Documents
sftp>



2.
[user@login4 ~]$                        (user-in hpc ls not in project directory)
cp script.rtf /project/devs/test    
cd /project/devs
cd  test
ls
mv script.rtf script.pbs

## Task 4  Practice bash, bash script and vim

## Task 5 Following computational genomics Protocol

reference:https://genomics.sschmeier.com/ngs-annotation/index.html

1. Installing and setting up Miniconda3 on local computer using command line interface
conda update --yes conda                    (yes )
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
conda create -n ngs python=3                (setting up environmet)

2.
## Running fastp for adapter trimming steps
conda create --yes -n qc fastp fastqc multiqc
conda activate qc                           (activating conda qc environmentfor running fastp)
mkdir trimmed
ls  
cp *fastq.gz trimmed                            
ls trimmed
cd trimmed
fastp --detect_adapter_for_pe --overrepresentation_analysis --correction --cut_right --html /Users/mg/Desktop/analysis/data/trimmed/evol2.fastp.html --json /Users/mg/Desktop/analysis/data/trimmed/evol2.fastp.json --thread 2 -i /Users/mg/Desktop/analysis/data/evol2_R1.fastq.gz -I /Users/mg/Desktop/analysis/data/evol2_R2.fastq.gz -o /Users/mg/Desktop/analysis/data/trimmed/evol2_R1.fastq.gz -O /Users/mg/Desktop/analysis/data/trimmed/evol2_R2.fastq.gz

ls trimmed
cp trimmed/evol2.fastp.html /Users/mg/Desktop/internship/             (for opening html file in a browser)

fastp --detect_adapter_for_pe --overrepresentation_analysis --correction --cut_right --html /Users/mg/Desktop/analysis/data/trimmed/evol1.fastp.html --json /Users/mg/Desktop/analysis/data/trimmed/evol1.fastp.json --thread 2 -i /Users/mg/Desktop/analysis/data/evol1_R1.fastq.gz -I /Users/mg/Desktop/analysis/data/evol1_R2.fastq.gz -o /Users/mg/Desktop/analysis/data/trimmed/evol1_R1.fastq.gz -O /Users/mg/Desktop/analysis/data/trimmed/evol1_R2.fastq.gz
ls trimmed
cp trimmed/evol1.fastp.html /Users/mg/Desktop/internship/
conda deactivate

## Task 6 Running Fastqc and Multiqc for quality assesment
1. Running fastqc

fastqc -o /Users/mg/Desktop/  evol1_R1.fastq.gz
fastqc -o /Users/mg/Desktop/  evol1_R2.fastq.gz
fastqc -o /Users/mg/Desktop/  evol2_R1.fastq.gz
fastqc -o /Users/mg/Desktop/ evol2_R2.fastq.gz
mkdir multiqc                                        (create a new directory multiqc inside data directory)
cp *fastqc.html /Users/mg/Desktop/analysis/data/multiqc   (because outputwas printern on desktop; so pwd was desktop and transferred to multiqc in data )

 2. Generating multi qc report
  (make sure all fastqc. and fastp files including in json format are in same directory so as to generate multiqc report in .html)
 multiqc /Users/mg/Desktop/analysis/data/multiqc/
## Task 7 Running SPAdes
## Task 8 Solving BUG in script  and  running QUAST
## Task 9 Alignment using BWA to map reads
## Task 10 Variant calling














