# ARIES-Reproduction

## Project Description

This project documents the reproduction of selected benchmark results of the paper:

**»Fast, accurate construction of multiple sequence alignments from protein language
embeddings«**, Minh Hoang, Isabel Armour-Garb and Mona Singh

Paper version as released on Oct. 1, 2026 in [Genome Reserach](https://genome.cshlp.org/content/early/2026/10/01/gr282254126).

ARIES is a Multi Sequence Alignment (MSA) algorithm. The authors combine embeddings technology from protein language models (PLM) to construct a windowed reciprocal-weighted embedding similarity metrics. ARIES seems to achieve higher accuracy than existing approaches. The paper claims improvement for datasets with low sequence identity, called the twilight-zone. It also claims to scale well for large numbers of sequences.


### Reproduction target

Focus of this reproduction project is the performance of the **ARIES** framework, as provided in the [ARIES GitHub](https://github.com/Singh-Lab/ARIES), against the **MUSCLE** MSA algorithm on the **BAliBASE 3.0** dataset. More on BAliBASE you can find [here](data.md). Primary evaluation metric as defined in the paper in Appendix C, is the Sum-of-Pairs (SP) score which is subject of this reproduction.

<br>![Fig. 3 - ARIES performance](<documentation/images/Screenshot 2026-Oct_paper_repro ARIES outperforms.jpg>)

*Source: Screenshot from Fig. 3 in the assigned paper (Hoang et al., 2026), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).*

**Numerical Reproduction:** Investigation of the paper's claim that ARIES outperforms the MUSCLE algorithm, the best performing algorithm on [BAliBASE 3.0](data.md) dataset in subset RV11 (low sequence identity). Primary target is to reproduce the SP score advantage of ARIES in subset RV11. Secondary target is to reproduce the SP score advantage in BAliBASE over all alignments.




   Numerical Reference Results (BAliBASE 3.0)

| Dataset | ARIES Mean SP | MUSCLE Mean SP | ARIES advantage (ΔSP) |
|---|---:|---:|---:|
| BAliBASE (all 218 alignments) | 0.88 | 0.87 | ≈ +0.01 |
| RV11 (38 alignments) | 0.790 | 0.685 | +0.105 |

*Source: Based on Hoang et al. (2026), Figure 3b and Appendix E, Table S2.*



<u>Numerical Criteria of Success:</u>

  - Primary Target: ARIES Advantage on BAliBASE RV11

    Numerical success is achieved if the reproduced mean SP scores differ by no more than ±0.03 absolute SP points.

  - Secondary Target: ARIES Advantage on Overall BAliBASE (Figure 3b)

    Numerical success is achieved if the reproduced mean SP scores differ by no more than ±0.03 absolute SP points.

  
<br>**Scientific Conclusion:**

Investigation whether the reproduction supports the paper's claim that ARIES outperforms MUSCLE in terms of SP score.
- Primary Hypothesis (BAliBASE RV11):

  H<sub>0</sub> : ARIES does not achieve a higher mean SP score than MUSCLE on the BAliBASE RV11 subset
  
  H<sub>1</sub> : ARIES achieves a higher mean SP score than MUSCLE on the BAliBASE RV11 subset.
  

- Secondary Hypothesis (Overall BAliBASE):

  H<sub>0</sub> : ARIES does not achieve a higher mean SP score than MUSCLE across all 218 BAliBASE alignments.

  
  H<sub>1</sub> : ARIES achieves a higher mean SP score than MUSCLE across all 218 BAliBASE alignments.

<u>Criteria of Scientific Support:</u>

The paper's claim is considered supported if ARIES achieves a higher reproduced mean SP score than MUSCLE (ΔSP > 0) and the advantage is statistically significant.

Statistical significance is assessed using a one-sided paired Wilcoxon signed-rank test, with a significance level of α = 0.05.


 ### ARIES Software Installation and Hardware Specifications

Installation intsructions and hardware requirements, ARIES python Scripts, datasets, CLI commands for running ARIES, default parameter settings and furhter information is available on the [ARIES GitHub](https://github.com/Singh-Lab/ARIES). 

<u>Reproduction Settings</u>:

For reproduction the **environment.yml** of the official ARIES GitHub is activated. It is also available on this repository. For running the ARIES software the parameter settings reported in the paper are used.


 **Main Parameter Settings for Reproduction**

| Parameter | Setting | Description |
|---|---|---|
| PLM | ESM-2 (650M parameters) | Pretrained transformer model |
| embedding layers | last ℓ = 9 layers  | Layers used for concatinating residue representations |
| window span (w) | 9 | Window size for alignment scoring |
|reciprocal weight (λ) | 400 | Gap penalty parameter |
| star alignment template | top ⌈ln N ⌉ medoids | Number of selected template sequences for N input sequences |
| ong-sequence handling | tiling for sequences > 1022 residues | Enables processing sequences exceeding the model's input limit |
| MUSCLE 5.1 settings | default parameters | Baseline alignment algorithm |
| benchmark dataset | BAliBASE 3.0 | 218 reference alignments |
| primary subset | RV11 | 38 reference alignments |
| evaluation metric | SP score | evaluated against reference data |

<br>A GitHub clone of the ARIES repository is used. The currently available scripts and datasets were the foundation for the scientific work of the assigned paper released on Oct. 1, 2026, as the authors confirmed.


<br>**Required Hardware Specification for Reproduction**

- Linux workstation
- CPU: Intel Xeon W3-2435 (16 logical cores)
- RAM: 64 GB
- GPU: NVIDIA RTX 4500 Ada (24 GB VRAM)
- Storage: Shared SSD (up to 400 GB, subject to availability and usage by other users)

<br>**Detailed quickstart instructions for installation and software running is available in [installation.md](installation.md).**


## References

**Assigned paper:** Hoang et al. (2026) – Fast, accurate construction of multiple sequence alignments from protein language embeddings. (https://doi.org/10.1101/gr.282254.126)

**Official ARIES Repository:** Singh-Lab/ARIES on GitHub. (https://github.com/Singh-Lab/ARIES)

**MUSCLE Paper:** Edgar, R. C. (2022). *Muscle5: High-accuracy alignment ensembles enable unbiased assessments of sequence homology and phylogeny.* Nature Communications, 13, 6968. [DOI: 10.1038/s41467-022-34630-w](https://doi.org/10.1038/s41467-022-34630-w)

**MUSCLE Repository:** [https://github.com/rcedgar/muscle/releases/tag/v5.1](https://github.com/rcedgar/muscle/releases/tag/v5.1)





