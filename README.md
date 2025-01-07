# Dixit AI Agent

An AI agent capable of playing the board game Dixit, combining vision-language models for image interpretation and creative hint generation. The agent can play both as a storyteller (generating hints) and as a guesser (interpreting hints and selecting cards).

## Overview

This project implements an AI system that can play the board game Dixit. The agent uses:
- BLIP-2 and ViT-GPT2 for image analysis
- CLIP for image-text matching
- Llama-2 for hint generation and reasoning
- A custom neural network trained on gameplay data

## Project Structure

```
.
├── checkpoints/           # Model checkpoints directory
├── data/                 # Data directory for cards, generated cards descriptions, embeddings and games rounds dataset
├── notebooks/
│   ├── generate_blip_vit_descriptions.ipynb  # Generate card descriptions
│   ├── guesser.ipynb                        # Guesser agent implementation
│   ├── guesser_train.ipynb                  # Training for guesser model
│   └── storyteller.ipynb                    # Storyteller agent implementation
├── config/
│   ├── config_generate_blip_vit_descriptions.json  # Configuration for description generation
│   ├── config_guesser.json                         # Guesser configuration
│   ├── config_guesser_train.json                   # Training configuration
│   └── config_storyteller.json                     # Storyteller configuration
└── README.md
└── LICENSE

```

## Data
The gameplay dataset used in this project comes from boiteajeux.net, as collected and processed in:

```bibtex
@inproceedings{10.1145/3555858.3555863,
author = {Vatsakis, Dimitris and Mavromoustakos-Blom, Paris and Spronck, Pieter},
title = {An Internet-assisted Dixit-playing AI},
year = {2022},
publisher = {Association for Computing Machinery},
booktitle = {Proceedings of the 17th International Conference on the Foundations of Digital Games},
series = {FDG '22},
doi = {10.1145/3555858.3555863}
}
```

The dataset contains information about 116,226 rounds of Dixit games, including storyteller hints, played cards, ground truth cards, and voting information. This data was used to train the guesser model.

The dataset is publicly available at: https://www.spronck.net/datasets/Dixit_AI_data.zip

## Usage

### Generate Card Descriptions
Run the `generate_blip_vit_descriptions.ipynb` notebook to generate descriptions for your card images.

### Train Guesser Model
Use `guesser_train.ipynb` to train the guesser model on gameplay data.

### Run Agents
- Storyteller: Use `storyteller.ipynb` to generate creative hints for cards
- Guesser: Use `guesser.ipynb` to interpret hints and select cards

## Requirements
### Hardware
- NVIDIA A100 GPU (40/80GB VRAM) - Recommended for best performance

### Software
- Python 3.8+
- PyTorch with CUDA support
- Transformers
- Hugging Face Account (for Llama-2 access)
- Jupyter Notebook
