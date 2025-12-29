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
### Data Preparation
The dataset is placed in the `/data` directory.
```
·
├── data
·  
```
## Training
Use the following command to start training your BrailleTrans model:
```
python src/train.py \
--data_dir /path/to/your/data/ \          # Change to your data directory path
--bert_path /path/to/bert/model/ \        # Change to BERT model path
--epochs 10 \
--batch_size 32
```
## Result
<table>
  <tr>
   <td><strong>Model</strong></td>  <td><strong>Train Loss</strong></td>
   <td><strong>Validation Loss</strong></td>  <td><strong>BLEU</strong></td>
  </tr>
  <tr><td>Transformer(Baseline)</td><td>0.057</td><td>0.042</td><td>86.51%</td></tr>
  <tr><td>+ MoE</td><td>0.056</td><td>0.040</td><td>92.12%</td></tr>
  <tr><td>+ BERT</td><td>0.038</td><td>0.031</td><td>97.02%</td></tr>
  <tr><td>+ BERT + MoE</td><td>0.033</td><td>0.032</td><td>98.15%</td></tr>
</table>
