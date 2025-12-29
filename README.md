#  <p align="center">Chinese-to-Braille Translation Model Based on Pretrained Language Models and Mixture of Experts Networks</p>

<p align="center">Dapeng Chen*</p>
<p align="center">Nanjing University of Information Science and Technology</p>

## <p align="center">ABSTRACT</p>
Braille is the primary medium through which people with visual impairments access information, and accurate conversion between Braille and Chinese text is a key technological component in advancing information accessibility. However, traditional translation methods exhibit significant limitations in handling polyphonic character disambiguation and complex word segmentation rules in Chinese, making it difficult to meet the requirements for high accuracy and robustness in real-world applications. To address this challenge, this paper proposes a Chinese-to-Braille translation architecture that integrates a pretrained language model with a Mixture of Experts (MoE) network. The proposed approach adopts an end-to-end encoder–decoder framework, in which the encoder leverages BERT to obtain rich deep semantic representations and incorporates a MoE mechanism to enable specialized modeling of diverse linguistic phenomena, thereby enhancing the model’s adaptability in complex semantic scenarios.To evaluate the performance of the proposed model, we construct a large-scale Chinese–Braille parallel corpus covering multiple domains, including news, literature, and daily communication. Experimental results demonstrate that the proposed Chinese-to-Braille translation model integrating a pretrained language model and a MoE achieves a BLEU score of 98.15\% on the test set, significantly outperforming traditional rule-based methods as well as various neural network baseline models. Further ablation studies indicate that both the BERT-based semantic representations and the MoE mechanism play critical roles in improving translation performance. In addition, qualitative feedback obtained through user studies suggests that the proposed approach effectively enhances reading fluency and content comprehension for users with visual impairments.

## Introduction
BrailleTrans is an innovative Chinese-to-Braille translation system that integrates pre-trained language models with a mixture of experts network to achieve high-precision Chinese Braille conversion.

The model framework is shown in the figure:

<img src="./asserts/OverallFramework.jpg" alt="图片描述" width="700">

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
