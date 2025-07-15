# MedSigLIP Diabetic Retinopathy Classification Example

This project demonstrates how to use Google's MedSigLIP-448 model for automated diabetic retinopathy classification from fundus photographs. The model can classify retinal images into different stages of diabetic retinopathy severity.

## Overview

MedSigLIP is a vision-language model specifically designed for medical imaging tasks. This example shows how to:

- Load and preprocess fundus photographs
- Use the MedSigLIP model to classify diabetic retinopathy severity
- Display classification results with confidence scores

## Classification Categories

The model classifies images into 5 categories:

- **No DR**: No diabetic retinopathy detected
- **Mild DR**: Mild non-proliferative diabetic retinopathy
- **Moderate DR**: Moderate non-proliferative diabetic retinopathy
- **Severe DR**: Severe non-proliferative diabetic retinopathy
- **PDR**: Proliferative diabetic retinopathy

## Requirements

- Python 3.9+
- PyTorch
- Transformers
- Pillow (PIL)

## Installation

Install the required packages:

```bash
pip install pillow transformers torch huggingface_hub ipywidgets
```

For Apple Silicon Macs, PyTorch will automatically use Metal Performance Shaders (MPS) for GPU acceleration.

## Authentication

The MedSigLIP model requires Hugging Face authentication. Login via CLI before running the notebook:

```bash
huggingface-cli login
```

You'll need to:

1. Create a free account at [Hugging Face](https://huggingface.co)
2. Generate an access token at [https://huggingface.co/settings/tokens](https://huggingface.co/settings/tokens) with "Read" permissions
3. Enter the token when prompted by the CLI command

**Note**: The model may be gated and require approval. If you encounter access issues, visit the [MedSigLIP model page](https://huggingface.co/google/medsiglip-448) and request access.

## Usage

1. Place your fundus photograph images in the project directory (e.g., `1.jpg`, `2.jpg`)

2. Run the Jupyter notebook `test.ipynb`

## Model Information

- **Model**: `google/medsiglip-448`
- **Input size**: 448x448 pixels
- **Architecture**: SigLIP (Sigmoid Loss for Language Image Pre-training) adapted for medical imaging
- **Training**: Specialized for medical imaging tasks

## Example Output

```
96.84% of 'No DR'
2.11% of 'Mild DR'
0.89% of 'Moderate DR'
0.13% of 'Severe DR'
0.03% of 'PDR'
Predicted class: No DR (96.84% confidence)
```

## Files

- `test.ipynb`: Main Jupyter notebook with complete example
- `1.jpg`, `2.jpg`: Sample fundus photographs for testing
- `README.md`: This documentation

## Zero-Shot Classification

This project demonstrates **zero-shot classification**, a powerful machine learning approach where the model can classify images into categories it has never been explicitly trained on. Here's how it works:

### What is Zero-Shot Learning?

Zero-shot learning allows a model to recognize and classify new concepts without having seen specific examples during training. Instead of training a traditional classifier with labeled diabetic retinopathy images, MedSigLIP uses:

1. **Vision-Language Understanding**: The model learns to connect visual features with textual descriptions
2. **Semantic Similarity**: It compares the visual content of an image with textual descriptions of different conditions
3. **Cross-Modal Matching**: The model finds the best match between what it "sees" in the image and what it "understands" from the text descriptions

### Limitations

- **Dependent on text quality**: The accuracy heavily relies on how well the text descriptions capture the visual characteristics
- **May miss subtle features**: Might not catch very subtle medical signs that require specialized training
- **Language dependency**: Performance can vary based on how medical conditions are described in text

This zero-shot approach makes MedSigLIP particularly valuable for medical applications where labeled data is scarce or expensive to obtain.
