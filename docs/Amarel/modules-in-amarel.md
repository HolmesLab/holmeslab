---
title: Modules in Amarel
nav_order: 2 
nav_enabled: true 
parent: Amarel Computing
---

# Modules in Amarel (2024)
Date: December 22, 2023 3:01 PM

---
**Table of Contents**
1. TOC
{:toc}
---


## Tutorial: How to use Modules:

Example: Loading`fsl/6.0.0-gc563.lua`

To use the command-line functions from the FSL (FMRIB Software Library) module that you've downloaded onto your system, you need to load the module first. Here's how you can do it:

### Step 1: Load the Module

Modules in many Unix-based systems are managed using `Environment Modules` or `Lmod`. These tools allow you to dynamically modify your shell environment to use different software packages. Given that you have the path to the module file (`/projects/community/modulefiles/fsl/6.0.0-gc563.lua`), you can load the module using the `module` command.

```bash
module use /projects/community/modulefiles
module load fsl/6.0.0-gc563
```

### Step 2: Verify the Module is Loaded

After loading the module, you can verify that the environment has been set up correctly by checking the paths or using `module list` to see if the module is active.

This should show `fsl/6.0.0-gc563` as one of the loaded modules.

### Step 3: Use FSL Commands

Once the module is loaded, you can use FSL commands like `fslinfo`, `fsleyes`, or any other FSL tools directly from the command line:

```bash
fslinfo <your_image.nii>
fsleyes <your_image.nii>
```

Replace `<your_image.nii>` with the actual file you want to work with.

### Step 4: Unload the Module (Optional)

If you're done with FSL and want to unload the module, you can do so with:

```bash
module unload fsl/6.0.0-gc563
```

This will remove the FSL-related paths and variables from your environment.

### Notes:

- **Environment Variables**: When the FSL module is loaded, it will typically set environment variables like `FSLDIR`, `PATH`, and `FSLOUTPUTTYPE`, which are necessary for the tools to function correctly.
- **Modules**: If `module` or `ml` commands are not available, your system might not use `Environment Modules` or `Lmod`. In that case, you might need to source the FSL environment script manually.

### Alternative: Source FSL Directly

If you prefer not to use modules, or if your environment doesn't support it, you can source the FSL setup script directly:

```bash
source /path/to/fsl/etc/fslconf/fsl.sh
```

Replace `/path/to/fsl/` with the actual FSL installation directory.

This approach directly modifies your shell environment to include FSL tools.

## Amarel Modules

These lists were updated 10/24/23, of the programs currently available on Amarel general cluster. Most of the programs are available as modules that need to be loaded before use. There are two locations where programs are installed: CORE and COMMUNITY. CORE modules are always visible. To make COMMUNITY installed programs visible, their location needs to be added to LMOD (module manager) path (see tutorial)

```bash
# View currently loaded modules
module list
```

```bash
# Load a module
module use /projects/community/modulefiles
module load name/version.lua # ie 'fsl/6.0.0-gc563'
```

For the current list of available modules and their versions use

```bash
# See modules ready to load (cd into folders to see version/loadable file)
module avail
```

To search for a specific program use 'module spider <program_name>', e.g.

```bash
# Search for modules
module use /projects/community/modulefiles
module spider name #ie 'matlab'
```

## Amarel Software Modules

- **** SCIENTIFIC SOFTWARE

*** Genomics

bamtools, blast, bowtie, bwa, canu, cufflinks, GATK, HISAT2, IGV, RSeQC, seqtk, sratoolkit, samtools, trinityrnaseq, RSEM

*** Mathematics

maple, Mathematica, MATLAB, SAS, stata, pspp

*** Modeling, simulations

* CryoEM

cryosparc, motioncor, scipion, relion

* Data Science, AI and ML

py-bigdata [keras, tensorflow], py-data-science-stack [pytorch, tensorflow], py-image

* Molecular modeling / Molecular dynamics

autodock, autodock_vina, chimera, gaussian, MGLTools, modeller, moe, openbabel, orca, packmol, vmd / amber, charmm, gromacs, lammps, namd

* Protein folding

alphafold, [RoseTTAFold via 'ai-fold' module]

- **** SOFTWARE DEVELOPMENT

*** Compilers/ Programing environment/ Debuggers

gcc, intel, pgi / anaconda, eclipse, jupiter notebook, tk / gdb, valgrind

*** Libraries

boost, cuda, eigen, gmp, hdf5, mkl, mvapich2, openmpi, tbb, zlib

*** Programming languages

c/c++, fortran, cuda, java, openjdk, perl, python, tcl

- **** UTILITIES

*** Archiving/compressing software [no module needed]

bzip2, gzip, tar, xz, 7za

*** Container managers

singularity

*** Encrypting software

veracrypt

*** File transfer utilities

curl, git, NcFTP, rclone, rsync

*** Image manipulation and plotting

gnuplot, imagemagic

*** Screen multiplexers

screen, tmux

*** Text editors / pdf viewers

emacs, jedit, nano, softmaker, sublime, vim / xpdf

## Amarel Load-able Modules

From output of:

```bash
module avail
```

or 

```bash
ls /projects/community/modulefiles 
```

ADFRsuite/1.0-kholodvl

ActiveTcl/8.6-kholodvl

BWA/bwa-0.7.17-yc759

CREST/2.12/wpk25/2.12-wpk25

DATASCIENCE/git/2.9.5-gc563

DATASCIENCE/nextflow/0.30.2-bd387

EMBOSS/6.6.0-kholodvl

FastQC/fastqc_v0.11.7-yc759

FastQC/fastqc_v0.11.9-yc759                                     (D)

FreeSurfer/7.4.1-ez82

GATK/4.1.4.1-yc759

GATK/4.1.7.0-yc759

GATK/4.2.2.0-yc759

GATK/Past_versions/4.0.4.0-yc759

GATK/Past_versions/4.1.0.0-yc759

GATK/Past_versions/4.1.3.0-yc759                                (D)

HISAT2/2.2.1-ez82

IGV/IGV_2.8.2-yc759

IGV/IGV_2.11.0-yc759                                            (D)

LIFESCIENCE/eclipse/4.8.0rc2-kholodvl

LIFESCIENCE/knime/3.7.1-kp807

MGLTools/1.5.6-kholodvl

MGLTools/1.5.7-kholodvl                                         (D)

Minimap2/minimap2-2.14

MotionCor2/MotionCor2_1.4.0

MrBayes/3.2.7a-zz109

NBO/nbo7-yc759

NcFTP/3.2.6-bd387

ORCA/4.2.1-shared-jv346

PyMol/2.5.2-bd387

QE/6.4.1_intel19.0.3-kholodvl

R/3.6.1-gc563

R/3.6.3-gc563

R/4.0.0-gc563

R/4.0.2-gc563

R/4.1.0-gc563                                                   (D)

RASPA2/2.0-yc759

RSEM/1.2.12-yc759

RSEM/1.3.3-yc759                                                (D)

RSeQC/3.0.1-yc759

SOAPdenovo2/2.04-r241-yc759

VCFtools/vcftools-v0.1.16-13-yc759

VSEARCH/2.15.0-yc759

afni/19.0.17-gc563

ai-fold/2021-bd387

alphafold/vs2.3.2-pgarias

alphafold/2022.03-pgarias

alphafold/2023.10-pgarias                                       (D)

amber/18_gcc_cuda-kholodvl

anaconda/2022.10-bd387

anaconda/2023.07-ts840

anaconda/2023.10-bd387                                          (D)

augustus/3.3.2-yc759

autodock_vina/1.1.2-kholodvl

autodock_vina/1.2.3-bd387                                       (D)

aws-cli/v2-bd387

bamtofastq/1.4.1-ez82

bamtools/2.5.1-gc563

bcftools/1.13-gc563

bcl2fastq/2.20-bd387

blast/2.10.1-zz109

boost/1.66.0-gc563

boost/1.70.0-bd387

boost/1.71.0-gc563                                              (D)

bowtie/1.2.2-gc563

bzip2/1.0.6-bd387

canu/canu-1.8

cctools/6.2.10-bd387

cctools/7.0.1-bd387

cctools/7.3.5-bd387                                             (D)

cdo/1.9.8-bkr22

cellranger-arc/2.0.1-bd387

cellranger/2.1.1-bd387

cellranger/3.0.1-bd387

cellranger/3.1.0-bd387

cellranger/6.0.2-bd387                                          (D)

charm++/6.9.0-verbs-gc563

charmm/c45b2-gc563

chimera/1.15-kholodvl

cliquer/1.21-gc563

clustalW/2.1-zz109

cmake/3.19.5-bz186

cmake/3.24.3-sw1088                                             (D)

compgen203/2018-kp807

connectome_wb/1.3.2-kholodvl

connectome_wb/1.4-test

connectome_wb/1.4.1-bd387                                       (D)

cudnn/8.1.3-jlb638

curl/7.64.0-kholodvl

eclipse/4.8.0rc2-kholodvl

eigen/3.3.4-gc563

fastx/0.0.6-bd387

fsl/6.0.0-gc563

fuse/3.9.1-gc563

gatk/4.4.0-bd387

gcc/10.2.0-bz186

gcc/10.2.0/openmpi/4.0.5-bz186

gcc/10.3.0-pgarias

gcc/11.2/openmpi/4.1.3-kholodvl

gcc/5.4/gdb/8.1-kholodvl

gcc/5.4/mvapich2/2.2/CUDA/7.5/gromacs/5.1.2/rl487/gromacs-5.1.2

gcc/5.4/mvapich2/2.2/MrBayes/3.2.7a-kholodvl

gcc/5.4/openmpi/3.1.2-kholodvl

gcc/7.3.0-gc563

gcc/8.1.0-sp1779

gcc/8.2/gnuplot/5.5-kholodvl

gcc/9.2.0-gc563

gcc/9.2.0/openmpi/4.0.5-bz186

gdal/3.1.4-sw1088

gdb/9.2-gc563

geant4/10.06.p01-gc563

gffcompare/v0.11.6-yc759

git/2.9.5-gc563

git/2.28.0-gc563

git/2.35.1-ez82                                                 (D)

gmp/6.1.2-gc563

gmp/6.2.0-gc563                                                 (D)

gnuplot/gnuplot-5.4.2-yc759

go/1.13.5-gc563

gold/5.8-kholodvl

grom/1.0.3-jz713

gromacs/2016.3-tesla

gromacs/2016.3

gromacs/2019.4-dp-gc563

gromacs/2019.4-sp-gc563

gromacs/2021.6                                                  (D)

gsl/2.5-bd387

gurobi/9.0.2-kholodvl

hdf5/1.8.20-gc563

hdf5/1.8.20-sw1088

hdf5/1.12.0-gc563-mvapich

hdf5/1.12.0-gc563-openmpi

hdf5/1.13.3-mpi-oneapi_2022-sw1088                              (D)

hmmer/3.3.1-zz109

humann2/0.11-bd387

imagemagick/7.0.8-kp807

intel/17.0.4/cuda/9.0/relion/2.1.0-kholodvl

intel/17.0.4/gamess/2019.06.30-jv346

intel/17.0.4/zlib/1.2.11-gc563

intel/oneapi_2022.3.1-sw1088

interproscan/5.31-70.0-zz109

isl/0.18-gc563

jedit/5.5.0-kholodvl

julia/1.9-bd387

king/2.2.8-pja77

knime/3.7.1-kp807

knime/4.5.2-kholodvl                                            (D)

kpLogo/1.0-yc759

lammps/16Mar18-intel-gc563

lapack/3.8.0-sw1088

lapack/3.9.0-bd387

lapack/3.9.0-bz186

lapack/3.11.0-sw1088                                            (D)

libXmu/1.1.3-gc563

libaec/1.0.6-oneapi_2022-sw1088

libfabric/1.9.0-gc563

libffi/3.3-gc563

libffi/3.4.2-gc563                                              (D)

mafft/7.471-zz109

make/4.2-kholodvl

manta/1.6.0-bd387

mc/4.8.22-kholodvl

metis/5.1.0_intel16.0.3

metis/5.1.0-sw1088                                              (D)

miniconda/2023.11-bd387

moe/2020.0901-kholodvl

moe/2022.02-kholodvl                                            (D)

mpc/1.1.0-gc563

mpc/1.2.0-bz186                                                 (D)

mpfr/4.0.1-gc563

mpfr/4.1.0-bz186                                                (D)

mpich2/3.1.4_intel_16.0.3

mummer/mummer-4.0.0rc1-yc759

namd/2.13-sp-gcc-mkl-mpi-gc563                                  (D)

namd/2022-07-21-pgarias

nano/5.3-ts840

nanopolish/0.13.2-yc759

nco/4.9.5-bkr22

netcdf-c/4.6.1-gc563

netcdf-cxx/4.3.0-gc563

netcdf-fortran/4.4.4-gc563

netcdf/v4.6.1_v4.4.0_intel_16.0.3

netcdf/4.8.1-sw1088

netcdf/4.9.0-sw1088                                             (D)

nextflow/0.30.2-bd387

nextflow/20.04.1-kholodvl

nextflow/22.04.0-bd387

nextflow/23.04.2                                                (D)

openbabel/2.4.1-kholodvl

openblas/0.2.20-gc563

openblas/0.3.4-gc563                                            (D)

orca/4.0.1.2-gc563

orca/4.2.1-gc563

orca/5.0.3-kholodvl                                             (D)

packmol/18.169-kholodvl

patchelf/0.17.0-sw1088

pcre2/10.35-gc563

perl/5.26.1-gc563

perl/5.36.0-pgarias                                             (D)

petsc/3.4.0_intel16.0.3_mpich_3.1.4

petsc/3.9.3-sw1088                                              (D)

pgi/19.10-bd387

plink/1.9-zz109

pnetcdf/1.9.0-gc563

pnetcdf/1.12.1-gc563                                            (D)

pnetcdf2/1.12.3-sw1088

prest/4.09-pja77

proj/5.2.0_intel16.0.3

plink/1.9-zz109

pnetcdf/1.9.0-gc563

pnetcdf/1.12.1-gc563                                            (D)

pnetcdf2/1.12.3-sw1088

prest/4.09-pja77

proj/5.2.0_intel16.0.3

proj/6.3.1-sw1088                                               (D)

protobuf/2.5.0-ez82

pspp/1.0.1-kp807

py-bigdata/2020-bd387                                           (D)

py-bigdata/2021-bd387

py-data-science-stack/5.1.0-kp807

py-image/2020-bd387

py-machine-learning/intel18/cuda12/pgarias                      (**L**)

py-machine-learning/2023-pgarias                                (D)

python/2.7.17-gc563

python/3.9.5-gc563

python/3.9.6-gc563                                              (D)

qualimap/v2.2.1-yc759

rclone/1.51.0-gc563

rclone/1.52.2-gc563

rclone/1.57.0-kholodvl                                          (D)

relion/3.0.6-gc563-cpu

relion/3.0.6-gc563-gpu

relion/3.1-beta

relion/3.1.1                                                    (D)

relion/4.0

rmate/1.0-jl2791

salmon/1.5.1-yc759

samtools/1.13-gc563

scipion/1.2.1-kholodvl

seqtk/seqtk-yc759

sequence_alignment_programs/clustalo-sp1779

sequence_alignment_programs/hhsuite-sp1779                      (D)

shapelib/1.4.1_intel16.0.3

shapelib/1.4.1-sw1088                                           (D)

snpEff/snpEff_4.3T-yc759

softmaker/2018-kholodvl

spark-notebook/2.2.0-kp807

spark/2.3.0-kp807

sqlite/3.40.0-sw1088

sqlite/3.43.2-ez82                                              (D)

sratoolkit/2.10.7-yc759

sratoolkit/2.11.3-yc759

sratoolkit/3.0.1-ez82                                           (D)

stata/mp2-18-ts840

strelka2/2.9.9-bd387

stringtie/v2.1.3b-yc759

sublime/3.1.1-kholodvl

tbb/2018_U3-gc563

tcl/8.6.10-gc563

texinfo/6.6-gc563

texlive/2018-bd387

tk/8.6.10-gc563

tmux/3.1-kholodvl

togl/2.0-gc563

trento/1.5.1-kholodvl

trinityrnaseq/2.12.0-yc759

unicycler/0.30.2-bd387

upc/2020.3-bd387

valgrind/3.15.0-gc563

velvet/1.2.10-yc759

veracrypt/1.24-gc563

vim/9.0/mp1009/9.0-mp1009

vmd/1.9.4-kholodvl

xpdf/4.00.01-kholodvl

xtb/6.5.1/wpk25/6.5.1-wpk25

yasm/1.3.0-gc563

zlib/1.2.11-gc563

zlib/1.2.13-oneapi_2022-sw1088                                  (D)

- ------------------------------ /opt/sw/modulefiles/Core -------------------------------

ARACNE/20200620         cuda/10.0                  java/11.0.18        (D)

FastQC/0.11.9           cuda/11.7.1                maple/2021

HISAT2/2.2.0            cuda/12.1.0       (**L**,D)    modeller/9.16

MATLAB/R2022a           cudnn/7.0.3                moe/2020.0901

MATLAB/R2023a    (D)    cufflinks/2.2.1            moe/2022.02

Mathematica/12.3        delly/0.7.6                mvapich2/2.1

Mathematica/13.1 (D)    gaussian/09revD01          mvapich2/2.2        (D)

OpenCV/2.3.1            gaussian/16revA03 (D)      openjdk/1.8.0_362

Q-Chem/5.4              gcc/4.9.3                  openjdk/11.0.18     (D)

RSEM/1.3.3              gcc/4.9.4                  openmpi/2.1.1

SAS/9.4M6               gcc/5.3                    pgi/19.4

STAR/2.7.5a             gcc/5.4           (D)      python/2.7.12

Trinotate/2.0.2         hdf5/1.8.16                python/3.5.2

bamtools/2.4.0          intel/16.0.3      (D)      python/3.8.2

bcftools/1.2            intel/17.0.2               samtools/1.3.1

bedtools2/2.25.0        intel/18.0.5      (**L**)      seqtk/1.3

blast/2.6.0             intel_mkl/16.0.3  (D)      singularity/3.1.0

blat/35                 intel_mkl/17.0.2           spss/26

bowtie2/2.4.1           intel_mkl/18.0.5           trinityrnaseq/2.1.1

bwa/0.7.17              java/1.8.0_362