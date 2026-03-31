# SRA (Sequence Read Archive)

## What is SRA?

The Sequence Read Archive (SRA) is a public repository maintained by the National Center for Biotechnology Information (NCBI) that stores **raw sequencing data**.

In simple terms, SRA is where you download the **actual sequencing reads (FASTQ files)** used in genomics studies.

---

## What kind of data does SRA store?

SRA stores:
- Raw sequencing reads (in `.sra` format)
- Single-end and paired-end reads
- Data from platforms such as:
  - Illumina
  - PacBio
  - Oxford Nanopore

These raw reads are later converted into FASTQ format for analysis.

This data is used to:
- Perform quality control (QC)
- Align reads to reference genomes
- Perform transcriptomics or metagenomics analysis

---

## SRA Data Structure

Understanding SRA structure is very important.

### 1. SRR (Run)
- Represents a single sequencing run
- Contains raw sequencing reads
- Accession format: `SRR123456`

👉 Think: the file you download

---

### 2. SRX (Experiment)
- Describes sequencing setup (library, instrument)
- Links runs to samples
- Accession format: `SRX123456`

👉 Think: how sequencing was performed

---

### 3. SRS (Sample)
- Biological sample information
- Example: tissue, condition
- Accession format: `SRS123456`

👉 Think: what was sequenced (similar to GSM in GEO)

---

### 4. SRP (Project / Study)
- Represents the complete study
- Contains multiple experiments and runs
- Accession format: `SRP123456`

👉 Think: entire project (similar to GSE in GEO)

---

## Relationship between GEO and SRA

- GEO contains study description and processed data
- SRA contains raw sequencing data

Typical workflow:

GSE (GEO study) → SRA link → SRR (run) → FASTQ

---

## How to Use SRA (Step-by-Step)

### Step 1: Open SRA
Go to: https://www.ncbi.nlm.nih.gov/sra

---

### Step 2: Access data using SRA Run Selector

1. Go to the **SRA Run Selector**    (Under Tools and Software)
2. Enter a **BioProject ID** or **GSE ID (from GEO)**

---

### Step 4: Use Run Selector

This is the most important step.

You will see:
- List of all SRR runs
- Metadata (layout, size, platform)

👉 Actions:
- Click **Select All**
- Click **Download Accession List**

This gives a file like:

SRR123456
SRR123457
SRR123458

---

### Step 5: Download data using SRA Toolkit

#### Install SRA Toolkit              (Instruction to download and install in the end)

Then run:

# Download .sra file
prefetch SRR123456

# Convert to FASTQ
1. Go to the Directory with .sra files  (e.g. /home/username/tmp/sra_cache)
2. fasterq-dump SRR123456.sra --split-files -e 8 -p --temp /home/username/tmp/sra_tmp/ -O /home/username/Documents/transcriptomics/    (# If the data is paired-end)

* --split-files: Split paired-end reads into two separate files
* -e 8: Uses 8 CPU threads (Speeds up processing)
* -p: Shows progress bar (Useful for monitoring large downloads/conversions)
* --temp: Specifies a temporary directory
          fasterq-dump needs a lot of temporary space
* -O: Output directory (Final fastq files will be saved here)

## How SRA is Used in Analysis

SRA is the starting point for most sequencing analyses:

- RNA-seq analysis
- Metagenomics
- Variant calling
- Genome assembly


## Important Notes for Beginners

- SRA stores data in `.sra` format → must be converted to FASTQ  
- Always check:
  - Single-end vs paired-end  
  - File size (can be large)
  - **Try to download one sra file at a time** (If working on a personal laptop)
- Metadata is critical for correct analysis  

---

## Tips for Working with SRA Data

### Look for:
- Paired-end sequencing (better for analysis)  
- Good read depth  
- Clear metadata  

### Be careful about:
- Large file sizes (plan storage)  
- Slow downloads  

---

## Common Mistakes

- Not using `--split-files` for paired-end data  
- Ignoring metadata  
- Downloading all runs without checking relevance  

---

## Summary

- **SRA** = raw sequencing data  
- **GEO** = study + processed data  

- Use GEO to understand the experiment  
- Use SRA to download raw data for analysis  

## 📦 Installing and Setting Up SRA Toolkit (Conda)

**Step 1: Create a Conda Environment**

conda create -n sra_env -c bioconda -c conda-forge sra-tools

**Step 2: Activate the Environment**

conda activate sra_env

**Step 3: Verify Installation**

fasterq-dump --version   (If installed correctly, this will display the installed version of fasterq-dump)

**Step 4: Configure SRA Toolkit (Important)**

Run the configuration interface:
vdb-config --interactive

Inside the configuration menu:
- Navigate to Main
  - Enable remote access
- Navigate to Cache
  - Set a cache directory (e.g. /home/username/tmp/sra_cache)   **All the sra files will be saved in this directory**
- Save and exit
