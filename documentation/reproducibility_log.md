# reproducibility log

## 18\. Oct 2026
- downloaded the paper to reproduce
- skimmed through the content to get an overview

## 20\. - 25\. Oct 2026
- read and analysed assigned paper
- familiarized with protein multi sequence alignment
- investigated the ARIES pipeline based on PLM embeddings
- identified the main claims of the paper
  1. better performance in the "twilight zone", low sequence identity
  2. better performance on large datasets
- explored the authors' github repository, avaliable datasets and their use in the paper, python scripts and CLI commands for running
- considered focusing on the claim "better performance in twilight zone" as reporoduction target
- pre selected the BAliBASE 3.0 dataset because the paper reports it is a challenging benchmark that also includes protein families with low sequence identity (hint in the paper: BAliBASE subset RV11 with very low sequence identity, probably a reproduction focus)
- considered to run ARIES vs. ClustalO because the github CLI reference showed by the parameter --compare clustalo that ARIES already is able to run it as a balsine competitor
- checked hardware, macbook M1 git and conda already installed, z book workstation nvidia GPU limited by 8 GB VRAM, git and conda already installed, both machines have python and JupyterLab installed
- git clone of the paper's github repository in a new project directory, following the Quickstart instructions 1) to 3) on the ARIES github repository on macbook and z book
- additionally created a jupyter lab kernel for ARIES
- explored the [BAliBASE](https://github.com/Singh-Lab/ARIES/tree/main/datasets/BAliBASE) dataset on ARIES github, found input data (FASTA files), curated aligned reference output data (.aln files) and xml data, for more details on the data create a dataset.md (still to do!)
- checked out GPU hardware available and reviewed BB11001.fasta as an example of the BAliBASE dataset with jupyter lab notebook ESM2_BB11001_Experiment.ipynb. CUDA, tokenizing and embedding calculation works. Reviewing the BAliBASE dataset showed 218 alignements in total. After filtering maxlen <= 1022 the experiment showed that 172 alignments remained on the contrary to 168 alignemnts reported in the paper. This difference has to be investigated.

## 30\. - 31\. Oct 2026

- perparing the reproduction plan, deadline Nov. 1, 2026
-  reproduce the results for BAliBASE with ARIES vs. ClustalO as shown in
Appendix D, Figure 8 and Figure 9
- scores SP and TC as reported in the paper
- ARIES parameter settings should follow the reported parameter in the paper
- created a reproduction project repository on my github account
- uploaded the written reproduction plan to GRIPS

## 05\. - 11\. Nov 2026

- git push README.md and renamed the empty log file to reproducibility_log.md
- investigated ARIES github commits on BAliBASE dataset to identify whether changes were made to BAliBASE before the paper was released on Jan. 02, 2026. Probably a difference in the number of alignments (168 vs 172 vs 218) occurs.
  - "git log --format="%h : %ad : %s" --date=short -- datasets/BAliBASE/inputs/" showed the following commits on BAliBASE:
    -  5e4332f : 2026-02-06 : refactoring and adding package code
    -  68333cf : 2025-11-24 : adding reference datasets
    -  51e96b8 : 2025-11-24 : adding reference datasets
- found out changes were made on BAliBASE before paper release, latest commit-id before: 68333cf
  - "git ls-tree -r --name-only 68333cf -- datasets/BAliBASE/inputs | grep -c '\.fasta$'" showed 172 input alignments, already more than 168 reported in the paper ?? perhaps another filtering ??
- received feedback on reproduction plan
 - "check Benjamini correction, seems to name Holm Bonferroni instead; ...", but Benjamini is right for the assigned January paper!
 - checked other versions of the paper, found out moere releases:
   - release Jan. 02, 2026, reported 168 BAliBASE alignments, default parameter settings
   - release Mar. 13, 2026, reported 218 BAliBASE alignments, changed parameter settings
   - release Oct. 01, 2026, reported 218 BALiBASE alignments (172 untiled and 46 tiled), changed parameter settings
- checked use of FIDS workstation instead of HP Z book
  - University VPN works fine
  - SSH works fine, 4 workstations are available
  - checked storage space on each workstation, but SSD storage ist limited
  - chose the workstation with most free storage space available
  - tested  git clone ARIES, worked fine
  - tested miniforge conda / mamba installation, error: not enough system tmp, perhaps a greater problem also for python env install, pytorch, cuda and huggingface cache for esm2-650m model
  - used debianforum.de, google etc. to solve the problem, created an user /tmp dir on the /loctmp SSD, used the hugging face doc for model cache
  - set the environment variables TMPDIR, PIP_CACHE_DIR and HF_HOME and reloaded the ~/.bashrc
  - removed old installation files, installed new miniforge3, conda init, worked fine
  - new git clone ARIES, created and activated ARIES environment and pip install . for python version of ARIES, worked fine
  - tested an ARIES run, worked fine, calculation took about 10 minutes (for comparison on the Z book same calculation took 50 minutes)
  - a storage wipe for the available workstations was announced for Friday 13th of November 2026, further work on the stations was postponed 
- started to convert paper log to digital log
- git commit and push of digital log, version until Oct. 31, 2026
- git commit and push oft the experimantal jupyter lab notebook and the January paper release as a .pdf file
- mail to ARIES author Prof. Mona Singh, qustions on the project
  
## 12\. - 15\. Nov 2026

- received response from the authors, sent a full version of the Oct 1, 2026 release in GenomeResearch, the authors have recommended to use this version for reproduction, confirmed that the currently available datasets and scripts were the foundation for the latest release of their results
- final decision to reproduce Oct 1, 2026 released paper
- read and checked the paper differences, especially the parameter settings
- decision to reproduce ARIES vs. MUSCLE, the best competitor against ARIES in the low sequence identity dataset 
- refined and updated the reproducion plan (not the final version, to be discussed with the seminar supervisor)
- created a data.md and described the BAliBASE dataset 
- updated the reproduction github
- after SSD wipe of the FIDS workstation, reconnected and searched for a workstation with enough storage
- decided to use remote workstation 4, created an user dir on /loctmp with enough storage
- followed and updated the installation guide, refreshed Linux bash terminal commands on debianforum.de
- run ARIES test on default parameter settings, worked fine
- checked the ARIES generated output files, looked fine, .fasta files with gaps and aligned sequences
- updated installation.md
- git commit to reproduction github, readme.md, data.md, installation.md, environment.yml, reproducibility_log.md
- current setup status is: ARIES installed with all dependencies, test run done on default parameter settings (not the reproduction settings!), output files checked, ready to start with reproduction
- to do before deadline: create git tag deliverable-2 and submit on GRIPS the github url and the full commit hash corresponding to the tag 



