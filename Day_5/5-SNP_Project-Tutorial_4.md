# SNP Analysis #5: Tutorial 4
## Viewing and Annotating a Phylogenetic Tree
### Purpose
In your last tutorial you produced the data for a phylogenetic tree and you identified a potential mutation of interest.  In this tutorial we will take these information and incorporate them into a phylogenetic tree using Iroki.

### Running the Analysis
1. The first thing you will want to do is make a mapping file for Iroki.  You just had a brief lecture on Iroki, so you should have a good idea what the mapping file will do.  We want to make a mapping file that will decorate the tree in two ways:
	* Color the sample name (leaf label) based on which study the sample came from
	* Add a colored shape next to the sample labe (leaf dot) indicating whether it contains the mutation of interest

2. Navigate to your `5-compare_vars` directory and open a new file in nano called `core.iroki_map.txt`.
 
3. In the first row enter these column headers separated by a tab.
	* name
	* leaf_label_color
	* leaf_dot_color

4. In subsequent rows you will need to fill in the information for each of your samples.
	* The __name__ must exactly match the sample_name that was used in your scripts (fofn files)
	* For __leaf_label_color__ select a different color for each study from https://www.iroki.net/wiki#Available%20Colors (also note the visual charts at https://www.iroki.net/wiki#Color%20Palettes).  It can be from a palette (e.g. k_1, pthc_1) or from the list of common colors near the bottom (e.g. black, red, salmon)
	* For __leaf_dot_color__ select a color to represent the sequences with your variant and enter it in the appropriate rows...  You can leave this field blank if there isn't a variant.

5. You should now have a file that looks something like:

```
name       leaf_label_color   leaf_dot_color
ERRxxxxxx  k_1                red
ERRyyyyyy  k_1                
ERRzzzzzz  k_1                
ERRaaaaaa  k_2                red
ERRbbbbbb  k_2                red
```

Make sure you have three columns on each line, even if the leaf_dot_color is blank

6. Now use FileZilla to transfer `core.nwk` and `core.iroki_map.txt` to your computer.

7. Go to https://www.iroki.net/viewer and upload your newick and mapping files.  And click submit.

8. Explore the options for displaying your tree.  

### Questions to Consider

* Did one of the tree layout shapes do a better job of showing the phylogentic relationships?

* What happened with the leaf_dot for samples where you left the color value blank?

* Did either of your mapping values align with the branching of your tree?
