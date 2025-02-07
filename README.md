## Interactive session

!!! Note: change firstname.lastname with your names

### Basic things first

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
