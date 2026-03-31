# RNA-seq Data Download Workflow

## Step 1: Identify Dataset in GEO

- Search using Disease, Organism, Experiment Type, Accession No.
- Review study design and samples
- Identify relevant samples

---

## Step 2: Locate Raw Data (SRA/ENA)

- GEO provides links to SRA
- Extract SRR or project ID (SRP)

---

## Step 3: Download FASTQ Files

### Option 1: Using SRA Toolkit

Install:
conda create -n sra_env -c bioconda -c conda-forge sra-tools
conda activate sra_env

Download:
fasterq-dump SRRXXXXXXX

---

### Option 2: Using ENA (Recommended)

- Search SRP/GSE ID in ENA
- Copy FASTQ FTP/HTTP links
- Replace ftp with https

Download using aria2:

aria2c -i links.txt -c -x 2 -s 2 -j 2

---

## Step 4: Resume Interrupted Downloads

If download fails:

aria2c -i links.txt -c

---

## Step 5: Validate Files

- Check file size
- Ensure paired-end files (_1 and _2)

---

## Notes

- ENA is faster and easier for bulk downloads
- SRA Toolkit can be slower and sometimes error-prone
