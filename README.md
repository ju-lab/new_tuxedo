# new_tuxedo
Snakemake pipeline for the 'new tuxedo' suite of RNA-seq analysis pipeline. 


Slightly modified from https://gist.github.com/ccwang002/2659b19439b6205284c0ae68ca06345d


Mostly following Pertea et al (2016) Nature protocol workflow


# Configure Environment
To run this pipeline you need to have `hisat2`, `stringtie`, `ballgown`, and `samtools` in your PATH environment. You can create a `conda` environment with the following command for an isolated environment. 


```bash
$ conda create -n new_tuxedo python=3.6 snakemake hisat2 stringtie samtools bioconductor-ballgown
```

# Usage
Activate your `new_tuxedo` conda environment before running the pipeline. 
```bash
$ source activate new_tuxedo; snakemake -p -s new_tuxedo.sm -j 24
 
# Preparation step 
FASTQ files should be in the `fastq` folder in the same level as `new_tuxedo.sm`. FASTQ files can be directly placed inside the `fastq` folder or can simply be a soft link. Relative path from the Snakefile should be `./fastq/[0-9A-Za-z_]+_R1.fastq.gz` and `./fastq/[0-9A-Za-z_]+_R2.fastq.gz`. 

Example folder structure is shown below: 
```bash
.
├── ~
├── fastq
│   ├── 2685_pos_R1.fastq.gz -> /home/users/cjyoon/Projects/myeloma/rnafastq/2685_pos_R1.fastq.gz
│   └── 2685_pos_R2.fastq.gz -> /home/users/cjyoon/Projects/myeloma/rnafastq/2685_pos_R2.fastq.gz
├── new_tuxedo.sm
├── README.md
```

