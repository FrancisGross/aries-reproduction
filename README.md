# ARIES-Reproduction

## Project Description

This project documents the reproduction of selected benchmark results of the paper:<br>   

**»Fast, accurate construction of multiple sequence alignments from protein language embeddings«** <br>

The focus is on investigating the paper's claim that the ARIES-Algorithm, developed by the authors, achieves higher alignment accuracy, particularly in the "twilight zone" of very low sequence identity, where traditional methods struggle and degrade.

The reproduction target is to reproduce the results for BAliBASE with ARIES vs. ClustalO as shown in
Appendix D, Figure 8 and Figure 9.

Figure 8 reports the Sum-of-Pairs (SP) score as defined in Appendix C equation (6) and
Benjamini-Hochberg-corrected p-value of one-sided Wilcoxon signed-rank test.

Figure 9 reports the Total-Column (TC) score as defined in Appendix C equation (7) and
Benjamini-Hochberg-corrected p-value of one-sided Wilcoxon signed-rank test.

The BAliBASE dataset was selected because the paper reports in section 2.5 that BAliBASE is
a challenging benchmark that also includes protein families with low sequence identity. Additionally, the paper reports in section 3.2 that ARIES outperforms state-of-the-art MSA methods
on the BAliBASE benchmark and the authors state that "ARIES performs particularly well in
this “twilight zone” of very low sequence identity" (section 3.2).

The ClustalO (Clustal Omega) MSA algorithm was selected due to its integration as a baseline
in the ARIES framework. It is also an established MSA method.

SP and TC scores indicate whether ARIES achieves higher alignment accuracy than ClustalO.

The data points in the volcano plots (Fig. 8 and Fig. 9) are colored by mean sequence identity.
This allows an investigation of whether ARIES performs better than ClustalO on protein fami-
lies with low sequence identity.

The PLM ESM-2 with 650M parameter was selected for generating sequence embeddings. This
follows the configuration used for the main ARIES benchmark results in the paper, reported in
section 2.5.

## References

**Assigned paper:** Hoang et al. (2026) - Fast, accurate construction of multiple sequence alignments from protein language embeddings. (https://doi.org/10.64898/2026.01.02.697423) 

**Official ARIES Repository:** Singh-Lab/ARIES on GitHub. (https://github.com/Singh-Lab/ARIES)





