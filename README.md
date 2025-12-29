<div align="center">
  <img src="figure/LOGO2.png" width="70%" style="vertical-align:-7px;" />

[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org/)

</div>

## Introduction
BrailleTrans is an innovative Chinese-to-Braille translation system that integrates pre-trained language models with a mixture of experts network to achieve high-precision Chinese Braille conversion.

## Quick Start
### Conda Environment of BrailleTrans
```bash
# Create and activate conda environment
conda create -n BrailleTrans python=3.10.18 -y
conda activate BrailleTrans
```

### Clone Project
```bash
git clone https://github.com/CdpLab/BrailleTrans.git 
cd BrailleTrans
```

### Install Dependencies
```bash
pip install -r requirements.txt
pip install torch==2.8.0 torchaudio==2.1.0
```

We use the `bert-base-chinese` architecture. Since the file is large, please download it from [here](https://huggingface.co/google-bert/bert-base-chinese). Then put it in the `/down` folder. The file structure is:
```
·
├── down
·   ├── configs
    └── bert-base-chinese
```


```
python src/train.py \
--data_dir /path/to/your/data/ \          # Change to your data directory path
--bert_path /path/to/bert/model/ \        # Change to BERT model path
--epochs 10 \
--batch_size 32
```
