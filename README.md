# PuggleAI
A **chess coach powered by AI** that transforms raw Stockfish analysis into more human-like explanations, with a coaching tone.  

This project was a **proof of concept** to apply *fine-tuning* of language models to a very specific domain: chess game analysis.

## Goal
- Convert Stockfish evaluations into understandable feedback.  
- Add human elements such as encouragement, reasoning, and recognition of good moves.  
- Explore how to train and deploy an LLM with a custom dataset.  

## Pipeline
1. **Data generation**: games were annotated based on the repository [ChessCommentaryGeneration](https://github.com/harsh19/ChessCommentaryGeneration).  
2. **Dataset preparation**: custom dataset with inputs (moves + context) and outputs (coach-style comments).  
3. **Training**: fine-tuning of a model on [Hugging Face](https://huggingface.co/GusSedano/PuggleAI).  
4. **Deployment**: inference tests through Hugging Face to generate automatic commentary.  

## Repository structure
puggle-ai/
├── notebooks/ # Training and deployment notebooks
├── data/ # Example dataset
└── models/ # Link to Hugging Face model


## Example usage
```python
from transformers import pipeline

coach = pipeline("text2text-generation", model="GusSedano/PuggleAI")

text = "Move played: 12...Nf6 instead of 12...d5"
print(coach(text, max_length=150)[0]["generated_text"])
The move 12...Nf6 is not a serious mistake, but you missed the chance to play 12...d5,
which would have opened the center more forcefully. Still, your idea keeps the position solid.
Good effort!
```

## Installation 
git clone https://github.com/yourusername/puggle-ai.git
cd puggle-ai
pip install -r requirements.txt

## Results
The model provides understandable and encouraging feedback.
Although only a pilot version, it demonstrates the feasibility of applying LLMs to chess coaching.

## Resources
Stockfish
Transformers (Hugging Face)

## Author
Developed by GusMSR
