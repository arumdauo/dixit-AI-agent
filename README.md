# Dixit AI Agent

An AI agent capable of playing the board game Dixit, combining vision-language models for image interpretation and creative hint generation. The agent can play both as a storyteller (generating hints) and as a guesser (interpreting hints and selecting cards).

## Overview

This project implements an AI system that can play Dixit, a creative card game where players must generate and interpret abstract hints about surreal artwork. The agent uses:
- BLIP-2 and ViT-GPT2 for image analysis
- CLIP for image-text matching
- Llama-2 for hint generation and reasoning
- A custom neural network trained on gameplay data

## Project Structure

```
.
├── checkpoints/           # Model checkpoints directory
├── data/                 # Data directory for images and descriptions
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
```

## Setup

1. Clone the repository:
```bash
git clone [your-repo-url]
cd dixit-ai
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up environment variables:
```bash
export HF_TOKEN="your-huggingface-token"
```

4. Prepare the data directory:
```bash
mkdir -p data/cards
```

## Configuration Files

The project uses several configuration files:

### Description Generation Config
```json
{
    "csv_path": "./data/descriptions.csv",
    "image_folder": "./data/cards",
    "model_name": "meta-llama/Llama-2-7b-chat-hf",
    "huggingface_token": "${HF_TOKEN}"
}
```

## Usage

### Generate Card Descriptions
Run the `generate_blip_vit_descriptions.ipynb` notebook to generate descriptions for your card images using BLIP and ViT models.

### Train Guesser Model
Use `guesser_train.ipynb` to train the guesser model on gameplay data.

### Run Agents
- Storyteller: Use `storyteller.ipynb` to generate creative hints for cards
- Guesser: Use `guesser.ipynb` to interpret hints and select cards

## Model Performance

In experimental games, the agent achieved competitive performance against human players:
- Won 5 out of 14 games
- Achieved an average score of 28.1

## Limitations

- Random distractor selection rather than strategic choice
- Hint generation could benefit from more sophisticated approaches
- Reasoning component could be enhanced through more extensive Chain of Thought prompting
- Limited cultural context understanding

## Requirements

- Python 3.8+
- PyTorch
- Transformers
- Hugging Face Account (for Llama-2 access)
- Jupyter Notebook

## License

[Your chosen license]
