# SNP Analysis #2: Tutorial 2
## Mapping, Variant Calling, and Filtering
### Purpose
Traditionally you would need to run at least three separate steps to map reads to the reference genome, identify variants, and filter out low quality variants.  The `snippy` software package wraps these three steps together and simplifies the process.  Note that `snippy` works well for bacterial genomes like we are analyzing, but is not well-suited for identifying variants in more complex eurkaryotic genomes.

### Reduced guidance ahead!
At this point you should be learning many of the commands in BASH.  In this tutorial, we will not be providing as many explicit commands and will expect you to lean back on the skills you built in the earlier exercises to come up with the commands yourself.  We have tried to bold many of the actions you need to take to make sure you do not miss anything.  If you get stuck ask for help!

### Running the analysis
1. You will perform this analysis on the Biomix cluster, so use the `ssh` command to login to Biomix as you learned previously.

2. The analysis will be run in a new sub-directory of the same OUTDIR location we setup in _Tutorial 1_.  __Change directory__ to that location.

3. You will need to collect a few file paths to start the analysis.  
	* Find the trimmed read 1 and read 2 fastq files (fq.gz) that were produced by TrimGalore! in the previous analysis.
	* Use the `realpath` command to get the complete file path to each (you will use this in step 4.)

4. There is a script provided in the `scripts` folder called `B-variant.slurm`.  **Open this file for editing**.  Examine the script and try to understand what it is doing.  You will notice it has a very similar strucutre to the trmming script, but with some differences near the end.   We will go over the script together in the workshop.  __Make edits__ to the `SAMPLE_NAME`, `READ1`, and `READ2` variables in the `##SAMPLE INFORMATION` section.  
	* `SAMPLE_NAME` should match what was in your A-trim.slurm script (i.e. the first part of the read filenames)
	* `READ1` and `READ2` should be the paths to the trimmed fastq files (fq.gz) which you recorded the paths of in #3 above. 

5. You are now ready to __submit your script__ to slurm.

6. Monitor the queue and make sure your job is running.

### Examining the Results
 7. When your job completes.  Check the slurm output file and make sure there were not any errors during the run.

8. __Examine the new files that are produced__.  They should be in a subdirectory (named after the sample) of a new directory called `4-snippy`.   __Change to that directory and list the contents__.  Snippy does several steps, so it produces a lot of output files...  Some are useful to you and others are just intermediate steps that you might not need.  We will explore these together in the workshop, but in the meantime try to explore the files and see which ones may be useful...  NOTE: all files except for the `.bam` file can be opened with the `less` command.