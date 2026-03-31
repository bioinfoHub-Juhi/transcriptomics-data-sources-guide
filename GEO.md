## GEO (Gene Expression Omnibus)

### What is GEO?
The Gene Expression Omnibus (GEO) is a public repository maintained by the National Center for Biotechnology Information (NCBI) where researchers submit and share high-throughput functional genomics data.

It contains datasets generated from experiments such as:
- RNA sequencing (RNA-seq)
- Microarrays
- ChIP-seq
- ATAC-seq
- DNA methylation studies

In simple terms, GEO is a database where researchers upload gene expression data so others can reuse and analyze it.

## What kind of data does GEO store?

GEO stores both:
- **Processed data** (e.g., gene expression matrices)
- **Raw data links** (usually hosted in SRA as compressed .sra file format)

This data helps answer biological questions such as:
- Which genes are upregulated or downregulated?
- How does a disease affect gene expression?
- What differences exist between two cell types or conditions?

## GEO Data Structure

Understanding GEO structure is very important.

### 1. GSM (Sample)
- Represents a single sample
- Example: one RNA-seq experiment
- Accession format: `GSM123456`

👉 Think: one sample or replicate

### 2. GSE (Series)
- Represents a complete study or project
- Contains multiple GSM samples
- Accession format: `GSEXXXXX`

👉 Think: the full experiment

### 3. GPL (Platform)
- Describes the technology used
- Examples:
  - Illumina sequencing platform
  - Microarray chip
  - Accession format: `GPLXXXXX`

👉 Think: how the data was generated

## How to Use GEO (Step-by-Step)

### Step 1: Open GEO
Go to: https://www.ncbi.nlm.nih.gov/geo/

### Step 2: Search for datasets
Example: RNA-seq and cancer

You can search using:
- Disease (e.g., cancer)
- Organism (e.g., Homo sapiens)
- Experiment type (e.g., RNA-seq)
- Accession number (e.g., GSE12345)

### Step 3: Filter results
You will see:
- Series (GSE)
- Samples (GSM)
- Platforms (GPL)

👉 Always select **GSE (Series)** for analysis


### Step 4: Explore a GSE dataset

A typical GSE page contains:
- Study title
- Summary (important for understanding the experiment)
- Overall design
- Sample list (GSM IDs)


### Step 5: Explore samples (GSM)

Each sample includes:
- Metadata (condition, tissue, treatment)
- Data files (processed or raw)


### Step 6: Download data

#### Option A: Processed data
- Directly downloadable from GEO

#### Option B: Raw data
- Follow SRA links
- Download SRA files using tools like:
  - `prefetch`
  - `fasterq-dump` (# to convert into fastq format)


## How GEO is Used in Analysis

GEO is widely used for:
- RNA-seq data analysis
- Differential gene expression (DGE/DEG)
- Reproducing published studies
- Comparative analysis between conditions


## Important Notes for Beginners

- GEO does not always store raw data; check SRA links
- Always read the **metadata and study design carefully**
- Some studies reuse previously published datasets
- Metadata is essential for correct interpretation


## Tips for Choosing a Good Dataset

### Look for:
- Biological replicates
- Clear control vs treatment design
- Well-described metadata
- Paired-end sequencing (preferred)

### Avoid:
- Missing metadata
- No replicates
- Unclear experimental design


## GEO DataSets vs GEO Profiles

When browsing GEO, you will often see two different views:
- **GEO DataSets**
- **GEO Profiles**

Understanding the difference is important.

### GEO DataSets

GEO DataSets represent the **entire study (GSE level)**.

They include:
- Study description
- Experimental design
- All samples (GSMs)
- Links to raw data (SRA)
- Processed data files

👉 Think: **Complete experiment**

Use GEO DataSets (GSE) when you want to:
- Download data
- Perform RNA-seq or DEG analysis
- Understand the full study


### GEO Profiles

GEO Profiles show **gene-specific expression patterns** across samples.

Each profile represents:
- Expression of a single gene
- Across multiple samples in a dataset

👉 Think: **One gene across all samples**

Use GEO Profiles when you want to:
- Check expression of a specific gene
- Quickly visualize gene behavior
- Explore trends without downloading data


### Key Differences

| Feature            | GEO DataSets (GSE)        | GEO Profiles              |
|--------------------|--------------------------|---------------------------|
| Level              | Study-level              | Gene-level                |
| Content            | All samples + metadata   | Single gene expression    |
| Purpose            | Full data analysis       | Quick gene exploration    |
| Raw data access    | Yes (via SRA)            | No                        |
| Use case           | RNA-seq pipeline, DEG    | Gene-specific queries     |


### Summary

- **GEO DataSets** → Use for analysis  
- **GEO Profiles** → Use for quick gene lookup  

For most bioinformatics workflows, you will primarily work with **GEO DataSets (GSE)**.

