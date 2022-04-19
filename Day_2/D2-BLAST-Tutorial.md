# Biomix BLAST Tutorial
## Purpose
This exercise is meant to familiarize you with the Biomix High Performance Computing environment (HPC).  During the exercise you will learn how to submit jobs to Biomix's slurm scheduling system, while performing BLASTp on a set of sequences.

### Getting Started
1. Log into biomix.  This will vary based on your operating system/ssh software.  If you are using ssh at the command line on your computer then it shoudl look simething like this:

```your_computer
ssh USERNAME@biomix.dbi.udel.edu
```

2. Now that you are logged in you should be in your "home" directory.  You can confirm this location by entering the `pwd` command.  Your home directory is a location where you can store files for longer term access.  You have a storage quota (limit) for this folder (usually about 200GB).  This storage is backed up regularly, but since its limited in scale, you will want to be careful about what data you chose to store in this location.

3. Biomix has a storage location that is meant for temporary storage of running analyses `/work`.  __NOTE__: Files older than 3 weeks old get removed from this location on a regular basis...so after you run an analysis you will want to copy any files you want to keep to your `/home/USERNAME` directory.

5. Let's change to `/work` location, so we can setup an analysis to run:

```biomix
cd /work
```

6. You will want to setup your own folder in the /work directory to hold your files (substitute your own username for "USERNAME" below):

```biomix
mkdir USERNAME
cd USERNAME
```

7. Now that you have a folder in `/work` you will probably want to make a subdirectory for different projects you are executing.  So let's do this now:

```biomix
mkdir fair-omics-blast
cd fair-omics-blast
```

8. Let's confirm our full file path with `pwd`.

9. Now let's get started on setting up for BLAST.  We have stored files you will need in `/work/fair_workshop/day-2_BLAST/`, so let's make our own copy of those files in this directory.

```biomix
cp /work/fair_workshop/day-2_BLAST/* ./
```

This command is telling BASH to copy all files (denoted by an asterisk) from that directory to our current location (denoted by: "./").

10. Now let's list the files using the `ls` command.

	__Tip__: If we want a more detailed listing we can type:
		 `ls -l`
	 
	 To see what other options `ls` has you can use the `man` command:
		 `man ls`

### Retrieving the query and subject sequences
11. For this exercise we will use a protein sequence as the query sequence.  One of the protein sequences you should have come across doing last night's assignment was "A0A679I946".  Go to uniprot and copy this sequence.  

12.  Now use `nano` to create and edit a new fasta file:

```biomix
nano tutorial_query.fasta
```

Now paste the header line (line that starts with ">" and sequence into the file).  Save by typing <__ctrl-x__>, respond "__y__" to the question if you wish to save the file, and then <__enter__> to accept the filename.

13. We will also need the fasta file you downloaded during last night's assignment containing all the proteins in _E. saigonensis_.  Use Filezilla to transfer this file to this folder.

### Formatting a BLAST database
14. The commands we are going to use in this exercise are from the NCBI BLAST+ package.  This is one of the software packages already installed on biomix.  The list of software can be viewed at: https://bioit.dbi.udel.edu/BIOMIX/BIOMIX-software.html.  The first command we will want to use is called `makeblastdb`.  Let's see what options this software has...

```biomix
makeblastdb -help
```

15. In the demo, you may be shown how to run `makeblastdb` in interactive mode.  You do not have to recreate these steps as we will be running this in batch mode in the next steps.

16. Let's find the file path for the fasta file contianing the _E. saigonensis_ proteins.  The `realpath` command is useful for this:

```biomix
realpath FILENAME
```

Copy the path, you will need it in step 18

17. To run `makeblastdb` in batch mode we will need a slurm submission script.  We have provided one for you named `makeblastdb.slurm`.  Let's open this file with `nano`.

18. We will walkthough what this script is doing in the workshop.  You will only need to edit two lines: the ones contianing "INFILE=" and "OUTFILEBASE=".  For "INFILE=" you will paste the path to your _E. saigonensis_ fasta file (that you copied in step 16).  The command will produce multiple files.  OUTFILEBASE is the file path and prefix they will all start with.  In many cases it will be the same as your INFILE...but with the ".fasta" extension removed.  Once these settings are correct.  Save your file (<__ctrl-x__> as described above).

19. Now we can submit this file to slurm using the `sbatch` command:

```biomix
sbatch makeblastdb.slurm
```

20. This command will run very quickly!  If you quickly type `squeue` you might catch a glimpse of it before it executes... but it may run before you even get a chance to see it...

21. To make sure the job ran correctly, we will examine the slurm output file using the `less` command.

```biomix
less slurm#####-makeblastdb-biomix##.out
```

Try to locate any errors or warnings in this file.  If all looks good, type "q" to quit.

### Running BLASTp
22.  Now that our blast database is formatted we can perform our BLASTp.  Again we have provided a slurm script for this command: `blastp.slurm`.  We will go over this file in class and discuss what is going on.  

		Again you will only have to edit a few of lines in this file (those beginning with "INFILE="; "OUTFILE="; and "DB=").  We will discuss how to fill these out in the workshop...

23. Once you have edited this script you can submit it to slurm using `sbatch`.

24.  Monitor the job using `squeue` and examine the slurm out file when it completes, to ensure there are no errors.

25. If everything ran successfully you can examine the OUTFILE that you defined in the script to see your results.

### Assignment
26. There is a file called `assignment_query.fasta`.   Run BLASTp on this file in two different ways: 1) using the custom database you just built; 2) using the nr database.  We will talk in class about how to BLAST against nr.  Remember to change your output filenames so that you can tell the difference!  Once both jobs have completed examine the results and be ready to discuss your interpretation tomorrow.  Make sure to use your electronic lab notebook skills to record the process!

