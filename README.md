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

