# reproducibility log

## 18\. Oct 2026
- downloaded paper to reproduce
- skimmed through the content to get an overview

## 20\. Oct 2026 - 25\. Oct 2026
- read and analysed assigned paper
- familiarized with protein multi sequence alignment
- investiaged the ARIES pipeline based on PLM embeddings
- identified the main claims of the paper
  1. better performance in the "twilight zone", low sequence identity
  2. better performance on large datasets
- Explored the authors' github repository, available datasets and their use in the paper,python scripts and CLI commands for running
- considered focusing on the claim "better performance in twilight zone" as reproduciton target
- pre selected the BAliBASE 3.0 dataset because the paper reports it is a challenging benchmark that also includes protein families with low sequence identity (hint in the paper: BAliBASE subset RV11 with very low sequence identity, probably a reproduction focus)
- considered to run ARIES vs. ClustalO because the github CLI reference showed by the parameter --compare clustalo that ARIES already is able to run it as a baseline competitor
- checked hardware, macbook M1 git and conda already installed, z book workstation nvidia GPU limited by 8 GB VRAM, git and conda already installed, both machines have python and JupyterLab installed
- git clone of the paper's github repository in a new project directory, following the Quickstart instructions 1) to 3) on the ARIES github repository on macbook and z book
- additionally created a jupyterlab kernel for ARIES
- explored the [BAliBASE](https://github.com/Singh-Lab/ARIES/tree/main/datasets/BAliBASE) dataset on ARIES github, found input data (FASTA files), curated aligned reference output data (.aln files) and xml data, for more details on the data create a dataset.md (still to do!)
- checked out GPU hardware available and reviewed BB1101.fasta as an example of the BAliBASE dataset with jupyter lab notebook ESM2_BB11001_Experiment.ipynb. CUDA, tokenizing and embedding calculation works.Reviewing the BAliBASE dataset showed 218 alignments in total. After filtering maxlen <= 1022 the experiment showed that 172 alignments remained on the contrary to 168 alignments reported in the paper. This difference has to be investigated

## 30\. Oct 2026 - 31\. Oct 2026
- preparing the reproduction plan, deadline Nov. 1, 2026
- reproduce the results for BAliBASE with ARIES vs. ClustalO as shown in Appendix D, Figure 8 and Figure 9
- scores SP and TC as reported in the paper
- ARIES parameter settings should follow the reported parameters in the paper
- created a reproduction project repository on my github account
- uploaded the written reproduction plan to GRIPS