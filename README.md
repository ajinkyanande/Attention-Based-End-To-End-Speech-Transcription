# Attention-Based End-To-End Speech Transcription

This project implements an end-to-end speech transcription system using an attention-based model. The system is designed to convert spoken language into written text.

## Table of Contents
- [Setup](#setup)
- [Usage](#usage)
- [Model Architecture](#model-architecture)
- [Experimentation](#experimentation)
- [Results](#results)
- [References](#references)

## Setup

To set up the project, follow these steps:

1. **Clone the repository:**
    ```bash
    git clone https://github.com/ajinkyanande/Attention-Based-End-To-End-Speech-Transcription.git
    cd Attention-Based-End-To-End-Speech-Transcription
    ```

2. **Run the setup script:**
    ```bash
    sh setup.sh
    ```

3. **Install the required Python packages:**
    ```bash
    pip3 install -r requirements.txt
    ```

## Usage

To run the entire pipeline, use the following command:
```bash
python main.py
```

## Model Architecture

The model architecture is based on the Listen, Attend and Spell (LAS) framework, which consists of three main components:

1. **Listener (Encoder):**
    - A stack of pyramidal Bidirectional LSTM (pBLSTM) layers that process the input speech features and reduce the sequence length.

2. **Attention Mechanism:**
    - Computes a context vector as a weighted sum of the encoder outputs, where the weights are determined by the similarity between the decoder state and the encoder outputs.

3. **Speller (Decoder):**
    - A stack of LSTM cells that generate the output sequence one character at a time, conditioned on the context vector from the attention mechanism.

## Experimentation

The following hyperparameters and configurations were used for experimentation:

1. **Epochs:** 50
2. **Batch Size:** 128
3. **Weight Decay:** 5e-6
4. **Learning Rate Scheduler:** Cosine annealing, starting at 1e-3 and decaying to 1e-5
5. **Teacher Forcing Rate Scheduler:** Manually set to values [1.0, 0.75, 0.6, 0.3, 0.1] based on model convergence
6. **Network Architecture:**
    - **Encoder:** Listener with pBLSTM layers and LockedDropout
    - **Decoder:** Speller with attention mechanism

## Results

The model was trained and evaluated on the provided dataset. The best model checkpoint is saved and can be used for inference.

## References

- [Listen, Attend and Spell (LAS) Paper](https://arxiv.org/abs/1508.01211)
- [PyTorch Documentation](https://pytorch.org/docs/stable/index.html)
- [WandB Documentation](https://docs.wandb.ai/)
