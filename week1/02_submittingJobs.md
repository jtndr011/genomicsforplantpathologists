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
