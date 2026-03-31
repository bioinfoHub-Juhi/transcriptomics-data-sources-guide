# ENA (European Nucleotide Archive)

## What is ENA?

The European Nucleotide Archive (ENA) is a public repository maintained by the European Bioinformatics Institute (EMBL-EBI) that stores **raw and processed nucleotide sequencing data**.

In simple terms, ENA is another major database (like SRA) where you can access **raw sequencing data and assembled sequences**.

---

## What kind of data does ENA store?

ENA stores:
- Raw sequencing reads (FASTQ)
- Assembled sequences (FASTA)
- Genome assemblies
- Metadata related to sequencing experiments

It supports data from platforms such as:
- Illumina
- PacBio
- Oxford Nanopore

This data is used for:
- RNA-seq analysis
- Metagenomics
- Genome assembly
- Comparative genomics

---

## How to Use ENA (Step-by-Step)

### Step 1: Open ENA
Go to: https://www.ebi.ac.uk/ena/browser/home

---

### Step 2: Search for data

- In the search box, enter:
  - **BioProject ID (PRJNA / PRJEB)**
  - **SRP ID (from SRA)**
  - **GSE ID (from GEO)**

👉 This will retrieve the associated sequencing data

---

### Step 3: View FASTQ files

- Open the study page  
- You will see a list of runs with **FASTQ download links**

---

### Step 4: Download links

- Click **"Download All"**
- You will get a list of **FTP links**   (**Save this file as links.txt**)

Example: ftp://ftp.sra.ebi.ac.uk/vol1/fastq/XXX/XXX.fastq.gz

---

### Step 5: Convert FTP to HTTPS

- Replace `ftp` with `https` in the links

Example: https://ftp.sra.ebi.ac.uk/vol1/fastq/XXX/XXX.fastq.gz

---

### Step 6: Download FASTQ files

Use command line tools like: aria2c -i links.txt -c -x 2 -s 2 -j 2

* `aria2c`: A command-line download tool that supports multi-threaded downloads
* `-i`: input file
* `-c`: Continue downloading if the process is interrupted (resume support)
* `-x`: Maximum number of connections per server (per file = 2 connections) **Increase value with faster internet**
* `-s`: Split each file into 2 segments for parallel downloading  **Increase value with faster internet**
* `-j`: Download 2 files simultaneously  **Increase value with faster internet**


---

### Pro Tip

**Using aria2c is especially useful when downloading**:

- Large FASTQ files
- Multiple sequencing runs
- Data from ENA (faster than SRA in many cases)
