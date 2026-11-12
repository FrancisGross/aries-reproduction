# Benchmark dataset for ARIES reproduction

This work evaluates ARIES on BAliBASE 3.0 dataset as reported in the paper. BAliBASE is a curated benchmark dataset for evaluation of MSA (Multi Sequence Alignment) algorithm. It provides structurally derived reference alignments of protein sequences. The dataset is organized into six reference versions (RV11, RV12, RV20, RV30, RV40, RV50). RV11 is a subset of lowest sequence identity ("twilight zone"). This subset is of high interest for this reproduction work.

The dataset is available on the ARIES github repository: [BAliBASE dataset](https://github.com/Singh-Lab/ARIES/tree/main/datasets/BAliBASE)

There are input data for computing the ARIES algorithm, reference data for evaluation and calculating scores and xml data with core blocks for special scoring.

The input data are stored in BBxxnnn.fasta files where each file represents a protein family. All proteins in one family, one file, are homologous. Every file consists of several proteins. The xx in the filename corresponds to the reference version (RV). The nnn in the filename is a numerical identifier for an alignment family within the subset.

Additional information on the dataset structure you can find on the ARIES github [here](https://github.com/Singh-Lab/ARIES/blob/main/datasets/README.md).


## Dataset Version for Reproduction

BAliBASE as provided in the ARIES github at the following Git commit:

1036dec7db273bd66a95688fd03dde983bc7867b

There are provided 218 input files in datasets/BAliBASE/inputs/ , 218 reference alignment files in datasets/BAliBASE/reference_outputs/ and 386 XML files in datasets/BAliBASE/xml/ .

The 218 input famalies correspond in number to the BAliBASE benchmark reported in the paper. After filtering maxlen <= 1022, 172 famalies remain and 46 families are excluded when running ARIES on default. 


## Access Instructions

1. It is recommended to clone the ARIES repository:

```bash
   git clone https://github.com/Singh-Lab/ARIES.git
```

```bash
   cd ARIES
```

2. Check out the exact repository version used in this reproduction project with commit hash:

```bash
   git checkout 1036dec7db273bd66a95688fd03dde983bc7867b

```
3. The BAliBASE data are available in:

```bash
   cd datasets/BAliBASE/
```

















