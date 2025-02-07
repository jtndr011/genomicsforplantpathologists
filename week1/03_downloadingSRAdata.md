## Downloading NCBI SRA data

### Installing SRAtoolkit
1) Download SRAtoolkit tar file
```bash
wget --output-document sratoolkit.tar.gz https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-ubuntu64.tar.gz
```

2) Extract the tar file
```bash
tar -vxzf sratoolkit.tar.gz
```

3) Add the `path` to bashrc file
```bash
echo "export PATH=\$PATH:$(pwd)/sratoolkit.3.2.0-ubuntu64/bin/" >> ~/.bashrc
```

4) Exit your CCAST account by closing it
```bash
exit
```

5) Sign in the CCAST account again
```bash
ssh prime.ccast.ndsu.edu -l firstname.lastname
```
> enter your password.

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