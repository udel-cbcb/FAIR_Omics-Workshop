# Assignment Day 1
## Exploring Web Resources
### NCBI BLAST
1. Navigate to https://blast.ncbi.nlm.nih.gov/Blast.cgi

2. Data:
```
ATGGCACAATTATTTTTTAAATATGGCGCAATGAACAGTGGGAAAACAATTGAAATTTTGAAAGTTGCCC
ACAATTATGAAGAGCAAGATAAACCTGTTGTGATTATGACAAGTGGTTTAGATACGCGTTCTGGAGTAGG
GCGAGTCTCAAGTCGAATCGGATTGGAAAGAGAAGCATTGCCGATTTTTGCTGAAACTAACGATTTTGAA
ACGATTGTAAATTTAGAATTAAAACCCTACTGTGTGCTAATCGACGAAGCACAATTTTTGCAAAAACAGC
ATGTTTTGGACTTTACTAGAATTGTAGATGAATTGAATATTCCAGTAATGGCCTTTGGCTTAAAAAATGA
TTTTCGCAATGAGTTATTTGAAGGATCTAAATATTTACTTTTATATGCTGACAAAATTGAAGAAATGAAA
ACAATCTGTTGGTTTTGTCATAAAAAAGCGATTATGAACCTTCATTATATTGATGGAAAACCAGTCTATG
AAGGAAACCAAGTCCAAATTGGGGGCAACGAAGCGTATTATCCTGTGTGCCGACACCATTATTTCCATCC
AGAAATATAA
```

3. For the sequence above, perform one or more "flavors" of BLAST (blastn, blastp, blastx, etc) as you think appropriate to:
	* Determine what __protein/gene__ the sequence has homology to. 
	* Identify the __organism__ the sequence is likely to have come from.
	* Determine the __taxonomic order__ of the organism.

Make a record of the evidence that has led you to each of these conclusions.  Make sure to record your search strategy/strategies, such that your process can be reproduced.

### Uniprot
4. Navigate to https://www.uniprot.org

5. Use the search function to find the entry for the protein (in the organism) you identified in #3.

6. Using the advanced search function: Build a query that will find this protein in all members of the taxonomic order that the organism belongs to.

7. Now filter your search to only display Reviewed (Swiss-Prot) entries.  View some of these entries.  What type of information can you learn about the protein through these entries that was not available on the original entry?

8. Start a new advanced search.  This time search for all proteins in the organism of interest.

9. Download a fasta file of the search (save this for use on Day 2).