# gatk4-pathseq
### Purpose :
This repo contains workflows for computational pathogen discovery using PathSeq, 
a pipeline in the Genome Analysis Toolkit (GATK) for detecting microbial organisms 
in short-read deep sequencing samples taken from a host organism.

Addtional Resources:
[How to Run the Pathseq pipeline (manually)](https://software.broadinstitute.org/gatk/documentation/article?id=10913)

## pathseq-pipeline
Runs the PathSeq pipeline

### Requirements/expectations :
- BAM 
  - file must pass validation by ValidateSamFile
  - all reads must have an RG tag
  - one or more read groups all belong to a single sample (SM)
- Host and microbe references files available in the [GATK Resource Bundle](https://software.broadinstitute.org/gatk/download/bundle)

### Output :
- BAM file containing microbe-mapped reads and reads of unknown sequence
- Tab-separated value (.tsv) file of taxonomic abundance scores
- Picard-style metrics files for the filter and scoring phases of the pipeline

## pathseq-build-microbe-reference
Builds a microbe reference for use with PathSeq

### Requirements/expectations :
- FASTA file containing microbe sequences from NCBI RefSeq

### Output :
- FASTA index and dictionary files
- GATK BWA-MEM index image
- PathSeq taxonomy file

## pathseq-build-host-reference
Builds a host reference for use with PathSeq

### Requirements/expectations :
- FASTA file containing host sequences from NCBI RefSeq

### Output :
- FASTA index and dictionary files
- GATK BWA-MEM index image
- PathSeq Kmer file
---
### Software version notes 
- GATK 4 or later 
- Cromwell version support 
  - Successfully tested on v36 
  - Does not work on versions < v23 due to output syntax

### Important Note 
- Runtime parameters are optimized for Broad's Google Cloud Platform implementation.
- For help running workflows on the Google Cloud Platform or locally please
view the following tutorial [(How to) Execute Workflows from the gatk-workflows Git Organization](https://software.broadinstitute.org/gatk/documentation/article?id=12521).
- Please post questions to the [GATK forum](https://gatkforums.broadinstitute.org/gatk/categories/ask-the-team).
- Please visit the [User Guide](https://software.broadinstitute.org/gatk/documentation/) site for furthr documentation on our workflows and tools.

### LICENSING 
#### Copyright Broad Institute, 2018 | BSD-3
This script is released under the WDL source code license (BSD-3) (see LICENSE in
https://github.com/broadinstitute/wdl). Note however that the programs it calls may
be subject to different licenses. Users are responsible for checking that they are
authorized to run all programs before running this script.

