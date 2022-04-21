# SNP Analysis: Tutorial 1
## QC and Trimming
### Purpose
Illumina sequence data has an average quality >Q30 (99.9% accuracy). However, with billions of bases in a run this still leaves room for a significant number of lower quality base calls.  Additionally, artifactual adapter sequences may be present in some Illumina reads and should be removed.  In this workflow you will learn to run analyses that will assess the quality of Illumina sequence data, and trim/filter low quality, adapter sequence, and short reads.  These steps will increase the accuracy of the downstream analyses that are performed with the data.

### Running the analysis
1. You will perform this analysis on the Biomix cluster, so use the `ssh` command to login to Biomix as you learned previously.

2. You will want to run this analysis in a new subdirectory on the `/work` partition.  Create a new subdirectory and change directory to that location. (substitute your own username for USERNAME)

```biomix
mkdir -p /work/USERNAME/fair_omics_proj
cd /work/USERNAME/fair_omics_proj
```

3. There is a directory of scripts located in `/work/fair-omics/project/scripts`.  You will want to be able to edit these scripts, so you should make a new copy in your directory. 

```biomix
cp -R /work/fair_workshop/project/scripts/ ./
```

4. The first script you will want to use is called `A-trim.slurm`.  Use `nano` to open this script.  (Remember the script is located in the `scripts` sub-directory, so you will need to include that in your command)

```biomix
nano scripts/A-trim.slurm
```

5. The script may look complicated, but it is fairly straightforward once you understand what is going on.  We will go over this script in detail in class so that you understand what it is doing.  You will only need to make a couple of changes to make the script run for you.  All are in the *### SCRIPT SETTINGS* section under *## SAMPLE INFORMATION*.  We will all use the same sample for this tutorial, so you will want to modify the three lines below to match what follows:

```nano
## SAMPLE INFORMATION
SAMPLE_NAME=ERR551167
READ1=/work/fair_workshop/project/sra_data/merker-PRJEB7281/ERR551167_1.fastq.gz
READ2=/work/fair_workshop/project/sra_data/merker-PRJEB7281/ERR551167_2.fastq.gz
```

There will also be an `OUTDIR` variable in this section, you should not need to change it unless you want to save to a different location.  (NOTE: If you change it, you will need to remember to make the same change in all future steps and scripts...)

> __TIP__: An error in a file path is the most common error when running slurm scripts.  A good practice is to confirm each file path is correct at the command line.  You can do this by copying the file path from your script and using the `realpath` or `ls` command to confirm it exists, like this:

```biomix
ls /work/fair_workshop/project/sra_data/merker-PRJEB7281/ERR551167_1.fastq.gz

realpath /work/fair_workshop/project/sra_data/merker-PRJEB7281/ERR551167_2.fastq.gz
```

6. You should now be ready to run this script using the `sbatch` command.  Remember you can check on the status of your job with the `squeue` command

```biomix
sbatch scripts/A-trim.slurm
```

### Examining the results
7. Once your job is completed, you will want to __examine the slurm output file__ with the `less` command.  Your file will be named something like this: slurm####-trim-biomix##.out.  The main reason you are examining the file is to make sure there were not any errors.  Scroll through the file looking for anything out of the ordinary.  It is a good idea to __search for the terms "error" and "warning"__ as they usually occur any time there is trouble...  

> __TIP__:	To search while `less` is open, you would type `/error` to search for the term "error" in the "down" direction or `?error` to search "upward" in the document.  Note: by default the searches are case sensitive, so this would not find "Error" or "ERROR".  To make searches case insensitive, type `-i` followed by the <enter/return> key.  You only have to do this once per `less` session (i.e. this will make all future searches case-insensitive until the next time you close `less`).

8. If everything looks good in the slurm output, you are now ready to examine the results.  __Change your directory__ to the OUTDIR location that was specified in your script (probably `/work/USERNAME/fair_omics_proj`) and __list the contents__.  You should see three numbered subfolders.  Try examining the contents of each in order.  
	* The first and third directories will have FastQC output before and after trimming and should have .html files that you will need to __transfer to your computer__ (using a file transfer client like filezilla) and then view in a web browser.
	* The second should have a .txt file that you can __view with `less`__.
	* We will walk through the output together once everyone's analyses are completed. 