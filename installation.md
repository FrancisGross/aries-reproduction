# Quickstart guide

This guide describes to run ARIES reproduction on a FIDS remote workstation at the University of Regensburg. 

## Available workstation hardware on FIDS

- Linux workstation
- CPU: Intel Xeon W3-2435 (16 logical cores)
- RAM: 64 GB
- GPU: NVIDIA RTX 4500 Ada (24 GB VRAM)

## Installation instructions

1. Open your VPN tunnel to the university network, Campus IT will support you if necessary, make sure the VPN connection is active before continuing
2. Conntect to a FIDS remote workstation via SSH
   - open a terminal on your local machine
   - connect to one of the available FIDS workstations, further information [FIDS](https://fids-admin.git-pages.uni-regensburg.de/fids-it-info/fids-services/cip-pools.html), choose one of the workstation names for SSH, enter your password if required
     
```bash
    ssh <your_username>@<workstation_name>.ur.de 
``` 

4. Change directory to /loctmp, since storage is low on /home/$USER and check if there is a minimum of 40 GB free to use

```bash
    cd /loctmp 
``` 


```bash
    df -h  /loctmp 
``` 
5. Change workstation if available storage is too low, check out storage on the other workstations, enter password when required and change workstation 

```bash
    ssh <workstation_name>.ur.de 'df -h /loctmp'
``` 

```bash
    exit
    ssh <your_username>@<workstation_name>.ur.de 
``` 

6. Create your own directory on the local SSD, $USER contains your username in bash, change directory to user

```bash
    mkdir -p /loctmp/$USER
    cd /loctmp/$USER
``` 

7. Prepare temp storage, due to limited storage on system /tmp or the /home directory and set environment variables for software installation 

```bash
    mkdir -p /loctmp/$USER/tmp
    export TMPDIR=/loctmp/$USER/tmp
    export PIP_CACHE_DIR=/loctmp/$USER/pip_cache
``` 

8. Download and install miniforge

```bash
    wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
``` 
   
```bash
   bash Miniforge3-Linux-x86_64.sh -b -p /loctmp/$USER/miniforge3
``` 

9. Initalize conda

```bash
   cd /loctmp/$USER/miniforge3/bin
   ./conda init
   source ~/.bashrc
``` 

10. Clone ARIES from GitHub

```bash
   cd /loctmp/$USER
   git clone https://github.com/Singh-Lab/ARIES.git
   cd ARIES
``` 

- to use the same ARIES version as in this reproduction run, use the the git hash

```bash
   git checkout 891571bd9d2e435d25c98d7694511f954b6866f7
``` 
      
- check the current commit, the output hash should be the same

```bash
   git rev-parse HEAD
``` 

11. Create the ARIES environment and activate

```bash
   mamba env create -f environment.yml
``` 

- activate (ARIES)

```bash
   conda activate ARIES
``` 

12. Install the ARIES package into the python environment

```bash
   pip install .
``` 

13. Check PyTorch and CUDA - nvidia GPU available

```bash
   python -c "import torch; print(torch.__version__); print(torch.cuda.is_available()); print(torch.cuda.get_device_name(0))"
``` 
- the output for the reproduction installation was:

    - 2.6.0+cu124
    - True
    - NVIDIA RTX 4500 Ada Generation


14. Prepare the Hugging Face cache for the PLM ESM-2 650M as recommended in the Hugging Face documentation for the /facebook/esm2_t33_650M_UR50D model

```bash
    export HF_HOME=/loctmp/$USER/huggingface
```    

15. Run ARIES for a first test with default parameter settings on BAliBASE dataset

```bash
    aries --input ./datasets/BAliBASE/inputs --output-dir ./outputs/BAliBASE
```  

16. Check your first results, in dir /loctmp/username/ARIES/outputs/BAliBASE

```bash
   cd /loctmp/$USER/ARIES/outputs/BAliBASE
   ls -lh
```  

- count the generated files, result should 172 files

```bash
   find . -type f | wc -l
```  

- have a look at the first aligned dataset BB11001.fasta

```bash
    cat BB11001.fasta
``` 

