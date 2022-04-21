# SNP Analysis #3: Day 4 Assignment
## Processing multiple samples
### Background
In tutorials 1 and 2, we walked through the QC, trimming, reference mapping, and identification/filtering of variants for a single sample.  What if we needed to process more than one sample...how would we do that?

We could repeat the process separately for each of the individual samples...however that could become very time consuming and introduces the possibility of a mistake (e.g. putting the wrong sample name with a set of sequence read files.). To simplify this process we can introduce a _loop_ into each of our two scripts that will execute the analyses on multiple smaples at once.

### QC and trimming
1. The first thing we will need to do is to __collect the samples__ we want to run.  During day 3, you explored the SRA repository and discussed a paper that analyzed SNPs from ~8500 _M. tuberculosis_ isolates from 17 studies.  We have downloaded many of the raw data files from those studies and they are available in `/work/fair_workshop/project/sra_data/`.  You may notice that some are missing; we did some quality control and removed many (maybe not all) of the samples that were likely to fail.  We also subsampled the data, so that it will reduce the amount of time it takes to run an analysis...

2. Choose five samples with at least 3 samples from a single project.  If you would like some background on the studies before choosing samples, check out the `study_accessions_citations.pdf` file on the [GitHub](https://github.com/udel-cbcb/FAIR_Omics-Workshop/tree/main/Day_4).  Cross-reference this with the 

3. Make a tab-delimited FOFN (file of file names) text file.  To create this file, all you have to do is use `nano` to open a filename that doesn't already exist.  You may name the file whatever you like...but it is a good idea to make the file extension is ".fofn.tsv", so that it is obvious what type of file this is.

4. The file will have three columns that are separated by a tab:
	* 1st column: sample name
	* 2nd column: path to read 1 (R1) fastq file
	* 3rd column: path to read 2 (R2) fastq file
	* You should **NOT** include a header row

5. Use the `realpath` command to find the file path for the R1 and R2 files for each of your sample and fill the values for all five samples into the file.

	__TIP:__ So that you can edit the file and use the `realpath` command to find the correct paths at the same time...you may want to open a second ssh session to Biomix.  Otherwise you will be opening and closing the file repeatedly to compelte the task...

6. Once you finish filling out your fofn.tsv file.  Take the time to double-check.  Make sure that the sample name, R1, and R2 paths on each line are all from the same sample!

7. Now you are ready to edit the script.  You probably noticed earlier that there is a second version of the trim script in the `scripts` folder named `A-trim-batch.slurm`.  __Open this script for editting__.

8. Examine the script, we will go over how it works before you leave on Day 4.  You should only need to make a single edit in the script: enter the full path of your fofn.txt file for the `IN_FOFN` variable.  If you'd like to use a different output directory you can, but this is not necessary.

9.  Submit the script to slurm and monitor that it runs correctly.  You might want to try opening your slurm output script while the job is still running to make sure everything seems to be going smoothly.  

10.  Once the script completes, check for errors.  You will have similar output for each sample that was produced in the tutorials - review it and see if there are any problems with your data.  While you may identify some issues with individual sample, each of the samples should produce sufficient output for you to proceed to the next step of analysis, so no need to rerun if you have questionable samples.  Just make a note of them for discussion.

11. The run will also produce one additional file...in your `2-trim` directory you should have a new `fofn.tsv` file.  The script produced this for you.  It has the same format as the one you used to run this script...but it has the paths to the trimmed versions of the reads.

### Variant Identification and filtering
12. Your next step will be to run variant analysis with snippy.  Once again you will find a "batch" version of the variant calling script in you `scripts` directory called `B-variant-batch.slurm`.

13. Modify `B-variant-batch.slurm` to accept your new fofn.tsv file (step 11 above) in the `IN_FOFN` variable.

14.  Run your script.  Once it completes review the output and resulting files.  If everything seems in order, then you are ready for part 4 of the anlaysis on Day 5!