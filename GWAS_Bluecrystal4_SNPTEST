#Bash script template for a GWAS on Bluecrystal 4, using SNPTEST. Options are set for a continuous phenotype, details: https://www.well.ox.ac.uk/~gav/snptest/#frequentist_tests

#!/bin/sh

#SBATCH --job-name  [jobname]
#SBATCH --error file-error
#SBATCH  -o [logfile name]
#SBATCH --cpus-per-task=1
#SBATCH --nodes=1 --tasks-per-node=2 --time=72:00:00

set -e

#SBATCH --mail-type=FAIL
echo "Running on ${HOSTNAME}"
echo Slurm job ID is $SLURM_JOBID
echo $SLURM_JOB_NODELIST

module add apps/snptest/2.5.2

samplefile="/mnt/storage/home/[username]/[.sample file]"

genfile="[ALSPAC BGEN file]"
outfile="/mnt/storage/home/[username]/results_chr_01"

snptest \
	-data ${genfile} ${samplefile} \
	-missing_code -9 \
	-pheno [Phenotype column name in .sample file] \
	-cov_names [Covariate column names seperated by spaces from .sample file] \
	-frequentist 1 \
	-method score \
	-use_raw_phenotypes \
	-o ${outfile}
