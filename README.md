#Interactive session

# Week 1

!!! Note: change firstname.lastname with your names

### Basic things first

!!! Skip step I if you signed in through the CCAST website

1) Sign in your CCAST account
```bash
ssh prime.ccast.ndsu.edu -l firstname.lastname
```
> enter your password.

2) Go to `scratch` in your account
```bash
cd /mmfs1/scratch/firstname.lastname/
```
> **cd:**  change directory (used to navigate the folders).

3) Check the full path of the current directory
```bash
pwd
```
> **pwd:** print working directory

4) Check what folders and files are in your `scratch` directory
```bash
ls
```
> **ls:**  list the items in the current folder.

5) Explore more information for the folders and files in your `scratch` directory
```bash
ls -alh
```
> **ls -alh:** provide the info about hidden files, size of the files, and other features

---

### Creating folders/files

6) Let's create a new folder named `workshop` 
```bash
mkdir workshop
```
> **mkdir:** make directory creates a new folder in current path

7) Move into this newly created `workshop` folder
> **Give it a try before seeing the answer**

<details>
<summary> <b>Answer</b> </summary>
  cd workshop
</details>

8) Create a new folders named `week1 week2 week3 week4`
> **Give it a try before seeing the answer**

<details>
<summary> <b>Answer</b> </summary>
  mkdir week1 week2 week3 week4
</details>

9) Move into the week1 folder
> **Give it a try before seeing the answer**

<details>
<summary> <b>Answer</b> </summary>
  cd week1
</details>

10) Let's create a new file with name `ThisIsMyFirstFile.txt`
```bash
touch ThisIsMyFirstFile.txt
```
> **touch:** this is used to create a new file

11) List all the files now
> **Give it a try before seeing the answer**

<details>
<summary> <b>Answer</b> </summary>
  ls
</details>

---

### Renaming and moving files

12) Don't like the name, let's rename the file
```bash
mv ThisIsMyFirstFile.txt pathogens.txt
```

13) Now create another folder named `folder1`
> **Give it a try before seeing the answer**

<details>
<summary> <b>Answer</b> </summary>
  mkdir folder1
</details>

14) Move `pathogens.txt` in `folder1`
```bash
mv pathogens.txt folder1
```
> **Note:** mv is used for renaming as well as moving the files

15) Go in the `folder1`
> **Give it a try before seeing the answer**

<details>
<summary> <b>Answer</b> </summary>
  cd folder1
</details>

---

### Editing the files

16) Now let's edit the `pathogens.txt`
```bash
vim pathogens.txt
```
> **vim:** vim a text editor like notepad, but for command line.

Steps to edit a file:
- `vim pathogens.txt` and hit enter
- Hit `i` to turn on the editing mode
- Type `This is a list of pathogens:`
- Add 5 pathogen names such as 
```bash
Fusarium
Puccinia
Alternaria
Uromyces
Bacteria
```
- To save the file and get out of editing mode, hit `esc`, then `:wq`

> **Congratulations!!!** You successfully created, edited and saved the file in command line. Yay!!! 

---

### Copying the files

17) Now copy this file `pathogens.txt` with new name `pathogensAndPlants.txt`
```bash
cp pathogens.txt pathogensAndPlants.txt
```
> **cp:** This is used to copy a file in the present directory.

18) Edit `pathogensAndPlants.txt` file to add the plant species on which these pathogens cause diseases

For example
```bash
Fusarium (Barley)
Puccinia (Wheat)
... and so on
```
> **Give it a try before seeing the answer**

<details>
<summary> <b>Answer</b> </summary>
  
  vim pathogensAndPlants.txt

  Hit i

  Type the plants in the brackets

  Hit esc, then :wq to save the file

</details>

---

### Searching `patterns` in the files

19) Let's find `Alternaria` in `pathogens.txt`
```bash
grep "Alternaria" pathogens.txt
```
> **grep:** This is used to find patterns in the files.

20) Let's find `Alternaria` in `pathogensAndPlants.txt`
> **Give it a try before seeing the answer**

<details>
<summary> <b>Answer</b> </summary>
  grep "Alternaria" pathogensAndPlants.txt
</details>

21) Now count how many times a word `Bacteria` came in the file `pathogens.txt`
```bash
grep -c "Bacteria" pathogens.txt
```

---

### Deleting or removing the file/folders

22) Removing `pathogensAndPlants.txt` file
```bash
rm pathogensAndPlants.txt
```
> **rm:** This will remove/delete the file.

23) Now come out of the directory `folder1`
```bash
cd ..
```
> **cd ..:** The two dots means going back one directory. If you have to go two directories back do `cd ../..`

24) Now, let's delete the directory `folder1`
```bash
rm -r folder1
```
> **-r:** The will delete the folder and all the files inside the folder. Alternatively, you can use `rmdir folder1` to delete the directory.

---
### Uploading and downloading files into your CCAST account

25) Upload two files `genes.fasta` and `protein.fasta` using CCAST website.


---
### Explore the contents of these files

26) Viewing the `genes.fasta` file's contents
```bash
cat genes.fasta
```

```bash
less genes.fasta
```

27) Counting the number of genes in `genes.fasta` file
```bash
grep -c ">" genes.fasta
```

---
# Week 2

### Submitting jobs on CCAST
**Step I:** Create and edit a PBS job file using `vim job.pbs`

**Step II:** Hit `i` to turn on the writing mode. Now, copy and paste the following:
```bash
#!/bin/bash
#PBS -N MyFirstJob
#PBS -q training
#PBS -l select=1:ncpus=1:mem=1gb
#PBS -l walltime=05:00
#PBS -W group_list=x-ccast-prj-training

cd $PBS_O_WORKDIR

echo "Welcome $USER"
echo "Hello from $HOSTNAME"
echo "I am running on $NCPUS CPU cores"
sleep 60

exit 0
```

**Step III:** Hit `esc`, then `:wq` to save the file and come out of editing mode

**Step IV:** Submit the job using `qsub job.pbs`

**Step V:** Check the status of the job using `qstat -u $USER`

### Checking the result files
There will be two files starting with `MyFirstJob`
```bash
ls
```

Use `less` or `cat` commands to check the contents of `MyFirstJob.o#####` Note: ##### will be the job id numbers.
```
less MyFirstJob.o91091
```

---


## Installing Flye assembler

1) Go the workshop directory
```bash
cd /mmfs1/scratch/jatinder.singh/workshop/
```

2) Create a folder called `softwares`
```bash
mkdir softwares
```

3) Go to this folder
```bash
cd softwares/
```

4) Load git software
```bash
module load git
```

5) Download flye assembler from the github
```bash
git clone https://github.com/fenderglass/Flye
```

6) Go in to the `Flye` folder
```bash
cd Flye
```

7) use the following command to install it
```bash
make
```

8) Add the software to the path
```bash
echo "export PATH=\$PATH:$(pwd)/bin/" >> ~/.bashrc
```

9) Exit the CCAST and Sign In again
```bash
exit
```

---

## Downloading NCBI SRA data

### Installing SRAtoolkit
1) Go the workshop softwares directory
```bash
cd /mmfs1/scratch/jatinder.singh/workshop/softwares
```

2) Download SRAtoolkit tar file
```bash
wget --output-document sratoolkit.tar.gz https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-ubuntu64.tar.gz
```

3) Extract the tar file
```bash
tar -vxzf sratoolkit.tar.gz
```

4) Add the `path` to bashrc file
```bash
echo "export PATH=\$PATH:$(pwd)/sratoolkit.3.2.0-ubuntu64/bin/" >> ~/.bashrc
```

5) Exit your CCAST account by closing it and sign in again
```bash
exit
```

6) Test the functioning of SRAtoolkit
```bash
fastq-dump --stdout -X 2 SRR390728
```

You will get the following output printed on your screen, which means everything is working 
```bash
Read 2 spots for SRR390728
Written 2 spots for SRR390728
@SRR390728.1 1 length=72
CATTCTTCACGTAGTTCTCGAGCCTTGGTTTTCAGCGATGGAGAATGACTTTGACAAGCTGAGAGAAGNTNC
+SRR390728.1 1 length=72
;;;;;;;;;;;;;;;;;;;;;;;;;;;9;;665142;;;;;;;;;;;;;;;;;;;;;;;;;;;;;96&&&&(
@SRR390728.2 2 length=72
AAGTAGGTCTCGTCTGTGTTTTCTACGAGCTTGTGTTCCAGCTGACCCACTCCCTGGGTGGGGGGACTGGGT
+SRR390728.2 2 length=72
;;;;;;;;;;;;;;;;;4;;;;3;393.1+4&&5&&;;;;;;;;;;;;;;;;;;;;;<9;<;;;;;464262
```

---

## Downloading data from SRA using job script in CCAST

```bash
#!/bin/bash
#PBS -N downloading
#PBS -q default
#PBS -l select=1:ncpus=1:mem=1gb
#PBS -l walltime=01:0:00
##change "x-ccast-prj" to "x-ccast-prj-[your project group name]"
#PBS -W group_list=x-ccast-prj-ugill

cd $PBS_O_WORKDIR

fastq-dump SRR24827173

exit 0
```

---

## Genome assembly of Trichoderma using Flye

```bash
#!/bin/bash
#PBS -N downloading
#PBS -q default
#PBS -l select=1:ncpus=8:mem=32gb
#PBS -l walltime=24:0:00
##change "x-ccast-prj" to "x-ccast-prj-[your project group name]"
#PBS -W group_list=x-ccast-prj-ugill

cd $PBS_O_WORKDIR

flye --nano-hq SRR24827173.fastq --threads $NCPUS --out-dir trichoderma_asm

exit 0
```

# Week 3

## Running the Bulk2SNPs pipeline

### Step I: Load the required module
```bash
module load git
module load singularity
```

### Step II: Clone the Bulk2SNPs repo
```bash
git clone https://github.com/NDSUrustlab/Bulk2SNPs.git
```

### Step III: Go the folder called `Bulk2SNPs`

### Step IV: Now let's download the F2 bulk data from NCBI SRA to study the nematode resistance in rice

> Important: Create a folder called `data` and then go into the `data` folder and run the following job to download the data.

```bash
#!/bin/bash
#PBS -N downloading
#PBS -q default
#PBS -l select=1:ncpus=1:mem=1gb
#PBS -l walltime=01:0:00
##change "x-ccast-prj" to "x-ccast-prj-[your project group name]"
#PBS -W group_list=x-ccast-prj-ugill

cd $PBS_O_WORKDIR

fastq-dump --split-files ERR2696321
fastq-dump --split-files ERR2696322

exit 0
```

### Step V: We also need to download the rice genome

> Come out of the data folder !!!

> Important: Create a folder called `genome` and then go into the `genome` folder and use the following code to download the rice genome.

```bash
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/034/140/825/GCF_034140825.1_ASM3414082v1/GCF_034140825.1_ASM3414082v1_genomic.fna.gz
gunzip -c GCF_034140825.1_ASM3414082v1_genomic.fna.gz > genome.fasta
```

#### Step : annotation file (not required), but you can explore it if you want
```bash
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/034/140/825/GCF_034140825.1_ASM3414082v1/GCF_034140825.1_ASM3414082v1_genomic.gff.gz
gunzip -c GCF_034140825.1_ASM3414082v1_genomic.gff.gz > annotation.gff
 ```

> Come out of the genome folder !!!

### Step VI: Now let's download the singularity file containing all the required softwares
```bash
singularity pull bulk2snps.sif docker://jtndr/bulk2snps:latest
```

### Step VII: Giving the executable permission to `nextflow` file
```bash
chmod +x nextflow
```

### Step VIII: Finally, submitting the job to run the `Bulk2SNPs` pipeline

> Create a job file called `pipeline.pbs` and paste the following code

```bash
#!/bin/bash
#PBS -N nf
#PBS -q bigmem
#PBS -l select=1:ncpus=16:mem=128gb
#PBS -l walltime=24:00:00
##change "x-ccast-prj" to "x-ccast-prj-[your project group name]"
#PBS -W group_list=x-ccast-prj-ugill

cd $PBS_O_WORKDIR

module load singularity

./nextflow run main.nf -with-singularity bulk2snps.sif \
  --bulk1 ERR2696321 \
  --bulk2 ERR2696322 \
  --genome genome/genome.fasta

exit 0
```

> Submit the job and check the status of the job.

## QTL mapping using QTLseqr

### Step I: Come out of `Bulk2SNPs` folder and create new folder called `QTLmapping` and go inside that folder

### Step II: Copy the `Bulks_SNPs.table` file in current folder
```bash
cp ../Bulk2SNPs/results/final_SNPs/Bulks_SNPs.table .
```

### Step III: Go to the ondemand CCAST website and open `interactive apps` -> Rstudio

### Step IV: Setwd to `QTLmapping` folder

### Step V: Installing QTLseqr
```R
install.packages("devtools")
devtools::install_github("bmansfeld/QTLseqr")
```

### Step VI: Create a new R script file called `QTLmapping.R`

### Step VII: Copy paste the following R code 
```R
#load the package
library("QTLseqr")

#Set sample and file names
HighBulk <- "ERR2696321"
LowBulk <- "ERR2696322"
file <- "Bulks_SNPs.table"

#Choose which chromosomes will be included in the analysis (i.e. exclude smaller contigs)
# Correctly generate chromosome names with leading zeros
Chroms <- paste0("NC_0890", 35:46, ".1")

# Print the chromosome names
print(Chroms)

#Import SNP data from file
df <-
  importFromGATK(
    file = file,
    highBulk = HighBulk,
    lowBulk = LowBulk,
    chromList = Chroms
  )
head(df)
#Filter SNPs based on some criteria
df_filt <-
  filterSNPs(
    SNPset = df,
    refAlleleFreq = 0.05,
    minTotalDepth = 20,
    maxTotalDepth = 400
  )

#Run G' analysis
df_filt <- runGprimeAnalysis(
  SNPset = df_filt,
  windowSize = 1000000,
  outlierFilter = "deltaSNP")

#Run QTLseq analysis
df_filt <- runQTLseqAnalysis(
  SNPset = df_filt,
  windowSize = 1000000,
  popStruc = "F2",
  bulkSize = c(23, 23),
  replications = 10000,
  intervals = c(95, 99)
)

#Plot
plotQTLStats(SNPset = df_filt, var = "nSNPs")
plotQTLStats(SNPset = df_filt, var = "Gprime", plotThreshold = TRUE, q = 0.01)
plotQTLStats(SNPset = df_filt, var = "deltaSNP", plotIntervals = TRUE)
plotQTLStats(SNPset = df_filt, var = "negLog10Pval", plotThreshold = TRUE, q = 0.01)

#export summary CSV
getQTLTable(SNPset = df_filt, alpha = 0.01, export = TRUE, fileName = "Bulk_rice_nematode_QTL_0.01.csv")
QTL <- getSigRegions(SNPset = df_filt, alpha = 0.01)
head(QTL[[2]])


# Open a graphical device to save the plot (e.g., PNG)
png(filename = "QTLStats_plot_Gprime.png", width = 5000, height = 800, res = 300)

# Generate the plot and save it to the file
plotQTLStats(SNPset = df_filt, var = "Gprime", plotThreshold = TRUE, q = 0.01)

# Close the graphical device
dev.off()
```
# Week 4

## Running GWAS analysis using GAPIT3

### Step I: Upload the data to CCAST - week4 folder

### Step II: Open R studio on CCAST

### Step III: 
```bash
###########################################################
########## STEP 1: Install the necessary packages #########
###########################################################

source("http://zzlab.net/GAPIT/GAPIT.library.R")
source("https://zzlab.net/GAPIT/gapit_functions.txt")
install.packages("devtools") # you need to install once
devtools::install_github("jiabowang/GAPIT3",force=TRUE)
library(GAPIT3) 
 

########################################################
########## STEP 2: Read all the data needed #########
########################################################

# Set working directory: a location in your computer where to put all datasets and output files
list.files() # display available data within the folder

# Read phenotype data
pheno <- read.csv('ricePheno.csv')
dim(pheno)
# Run some summary statistics and figures
summary(pheno)
hist(pheno[,2])
hist(pheno[,3]) 
head(pheno)
tail(pheno)

# Read SNP data.Missing data in SNP is imputed with mean values (naive imputation). # SNP data format: Major=2; Minor =0; Hets=1;
snp <- read.csv('riceSnp.csv')
dim(snp)
snp[1:10, 1:10] #first 10 rows and first 10 columns
snp[1:10, 1:5] #first 10 rows and first 5 columns
table(snp[,2])
colnames(snp)[1] <- 'Taxa' # change name of column 1 

# Read genetic map
map <- read.csv('riceMap.csv') 
dim(map)
head(map)

########################################################
########## STEP 3: Run GWAS ############################
########################################################

# The analysis should be completed within couple minutes. In your current R working directory, you should
# find multiples files with three types of extensions: pdf, csv, and txt. The pdf files include the Manhattan
# plot and the QQ plot displayed above. 

# Running model one at a time (e.g., GLM only). 
# My suggestion is to create a folder for each model

# General Linear model: Y= SNP + PCA + error
dir.create('./GLM') # create a folder for all results from GLM analysis
setwd('./GLM') # change folder where to put output files
myGLM <- GAPIT(Y=pheno,GD=snp,GM=map,PCA.total=3, model="GLM")

# Mixed Linear model: Y= SNP + Kinship + PCA + error (also known as Q+K); Q is replaced by PCA; 
dir.create('./../MLM')
setwd('./../MLM') # .. means one back in directory 
myMLM <- GAPIT(Y=pheno,GD=snp,GM=map,PCA.total=3, model="MLM")

#  Models for enhancing statistical power by improving model fit and reducing kinship matrix rank;
# Options: 1. Compressed Mixed Linear Model (CMLM): 2.	Enriched Compressed Mixed Linear Model (ECMLM); 3. Settlement of MLM under Progressively Exclusive Relationship (SUPER);
# 4. Settlement of MLM under Progressively Exclusive Relationship (SUPER): 
dir.create('./../SUPER')
setwd('./../SUPER')
mySUPER <- GAPIT(Y=pheno,GD=snp,GM=map,PCA.total=3, model="SUPER")

# Models to increase statistical power using multi-locus models
# Options: 1. Multi-locus mixed model (MLMM); 2. 2.	Fixed and random model circulating probability unification (FarmCPU); 3. Bayesian Information and LD Iteratively Nested Keyway (BLINK):  
dir.create('./../FarmCPU')
setwd('./../FarmCPU')
myFarmCPU <- GAPIT(Y=pheno,GD=snp,GM=map,PCA.total=3, model="FarmCPU")

dir.create('./../MLMM')
setwd('./../MLMM')
myMLMM <- GAPIT(Y=pheno,GD=snp,GM=map,PCA.total=3, model="MLMM") 


# Running multiple models in one line of code.
# Notes: Results for different traits may vary depending on trait complexity
dir.create('./MODELS')
setwd('./../MODELS')
myModels <- GAPIT(Y=pheno,GD=snp,GM=map,PCA.total=3, model=c("GLM", "MLM", "SUPER", "MLMM", "FarmCPU"), Multiple_analysis=TRUE) # c is used in R for combining different arguments;

#########################################################################
########### Determine the p-value threshold for publication  ############
#########################################################################
##
##
# STEP 1: Perform singular value decomposition; a method similar to PCA. 
# You can use other function like princomp or svd in R, which should give the same results.


# Step 1: Read numerically coded SNP data.
X <- read.csv('riceSnp.csv', row.names=1)

# Center and scale SNP data
Xcs <- scale(as.matrix(X), center=TRUE, scale = TRUE)  
	
#   Perform singular value decomposition, similar to PCA 
eigSnp <- svd(Xcs) 
eigVals <- (eigSnp$d)^2 / ((dim(X)[1])-1) 

	 
# STEP 2: Calculate the p-value threshold using Li and Ji (2015) methods. Run the equation 5 in Li and Ji (2005).
# Some SNPs are in LD due to physical distance (e.g., linkage) or other factor. So some SNPs are not really independent. 
# The goal of this method is to calculate effective number of test (Meff), and use Meff to calculate p-value threshold.
	
Meff=0
		
for (i in 1:length(eigVals))	{		
	if (abs(eigVals[i]) >= 1) I=1 else I=0			
	fx = I + (abs(eigVals[i]) - floor(abs(eigVals[i])))			
	Meff = Meff + fx  
			
}

# Type Meff to verify effective number of test 

Meff # Out of 34K SNP, only 557 are effective for testing SNP-trait association; 


# STEP 3: Calculate the p-value threshold

alpha_E <- 0.05   # Experiment-wise error rate.
alpha_P <- 1 - (1 - alpha_E)^(1/Meff)   # Comparison-wise error rate.
	

# Translate the calculated p-value threshold into -log10(P-value);

log10_P <- -log10(alpha_P) # This is the threshold that you can report in your paper. Any SNP that passes this threshold will be declared significant; 


######################## END #################################
```
