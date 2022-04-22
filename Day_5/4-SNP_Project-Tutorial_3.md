# SNP Analysis #4: Tutorial 3
## Comparing Variants Across Samples
### Purpose
By now you should have run all the analyses to identify variants in each of five samples.  However, as the data is currently organized, it is not easy to compare results across the samples.  In this tutorial we will run a few commands that will help format the results for comparison. 

### Running the Analysis
1. Open the `C-compare_vars.slurm` script from your `scripts` directory for editing.

2. By now you should be getting familiar with how these scripts are setup, so you will probably notice that several commands are being executed in this script.  We will go over the details of this script and what is happening in the workshop.

3. In the script, you will again only have to edit the `IN_FOFN` variable.  This time you will want to point it to the `fofn.txt` file that was created by the `B-variant-batch.slurm` script.  (You will notice that this fofn file ends in `fofn.txt` instead of `fofn.tsv`, this is because this fofn file contains only a single file path per line, rather than the tab-delimited `fofn.tsv` files that we had in previous steps.)

4.  You can now submit your script to slurm and monitor its execution.  When it completes, make sure to check for errors in the slurm output file.

### Examining the Results
5. In the `5-compare_vars` folder you should have several different files.  The ones of most interest are:
	* `core.ann.vcf` - This is an annotated vcf file of variants across your samples
	* `core.ann.tab` - This is an annotated tab-delimited file of variants across samples.  This file contains some information that the vcf lacks, including the identity of genes where variants occur
	*  `core.nwk` - This is the data for a phylogenetic tree built to display the relationship of your samples to each other.

6. Open the `core.ann.tab` file with `less`.  Try to identify a variant that:
	* occurs in at least 2 of your samples
	* occurs in a gene that seems interesting 
	* causes a potentially deleterious modification to the protein

	__TIP__: Unfortuantely this file will look a bit jagged when opened in `less` because the tabs are not lining up correctly.  You may want to use FileZilla to copy this file to your computer, so you can import it into excel for easier viewing.  Another option to is to use a BASH command called `column`.  You will need a couple of options on the ocmmand line to make it display correctly, but if you use a command like below you should get a better organized version of the file opened in `less`.
	
	```biomix
		column --table -s $'\t' core.ann.tab | less
	```

7. Once you have identified the variant of interest...make notes about the gene it occurs in, its potential for deleteriousness, and which samples have the mutation.  We will use this information in the next tutorial when we view and decorate your tree in Iroki.