### Interactive session

!!! Note: change firstname.lastname with your names

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

