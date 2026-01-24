# Multi-Expert TNM Staging for Lung Cancer Radiology Reports

## Overview

This repository contains the source code for **automated TNM staging from lung cancer radiology reports** using large language model (LLM) ensembles. Our systems achieved **1st and 2nd place** in the NTCIR-18 RadNLP 2024 English main task competition.

**Key Achievements:**
- **System I**: 1st place with joint accuracy of 0.6543 (T: 0.7037, N: 0.9136, M: 0.8889)
- **System II**: 2nd place with joint accuracy of 0.6296 (T: 0.7284, N: 0.9383, M: 0.8395)

## Systems Description

### System I: Expert-Enhanced Few-Shot Ensemble

System I uses **GPT-4o with structured reasoning** and expert-grounded few-shot prompting:

- **Three-phase architecture**: Training rationale generation, multi-run classification with few-shot learning, and hard voting aggregation
- **7-shot learning framework** with 3-vote aggregation
- **Structured reasoning**: Generates clinical rationales for each training case
- **Hard voting mechanism**: Aggregates predictions across multiple inference runs

### System II: Multi-Model Expert Panel

System II implements a **multi-model consensus approach** simulating collaborative medical expert panels:

- **Dual-model architecture**: Alternating between GPT-4o and Gemini-2
- **DSPy framework**: Declarative programming for modular AI systems
- **MIPROv2 optimization**: Joint optimization of instructions and few-shot demonstrations
- **Five-iteration consensus mechanism**: Multiple independent assessments with final synthesis

## Requirements

### System Requirements
- **Python**: 3.12 or higher
- **Operating System**: Linux
- **Frameworks**: PyTorch 2.6, DSPy 3.0

### API Access
- OpenAI GPT-4o API key
- Google Gemini-2 API key (for System II)

## Installation

```bash
# Clone the repository
git clone https://github.com/nlptmu/multi-expert-tnm-staging.git
cd multi-expert-tnm-staging

# Install PyTorch 2.6
pip install torch>=2.6.0

# Install DSPy 3.0
pip install dspy-ai>=3.0.0
```

## Dataset

The systems were evaluated on the **NTCIR-18 RadNLP TNM Staging Task** dataset:

| Dataset | English Track |
|---------|---------------|
| Train   | 108 samples   |
| Validation | 54 samples |
| Test    | 81 samples    |

**Data Preprocessing Philosophy:**
- Minimal preprocessing to maintain authentic clinical report structure
- Preserves natural variability in formats, terminology, and detail levels
- Ensures consistency with expert annotation logic

## Configuration

### System I Parameters

**Phase 1 - Rationale Generation:**
- `temperature = 1.0`
- `top_p = 1.0` 
- `max_tokens = 200`

**Phase 2 - Classification:**
- `temperature = 0.2`
- `top_p = 0.8`
- `max_tokens = 50`

### System II Parameters

**MIPROv2 Optimization:**
- `max_bootstrapped_demonstrations = 50`
- `max_labeled_demonstrations = 50`
- `temperature_range = (0.001, 0.85)`

**Multi-Model Configuration:**
- `num_iterations = 5`
- `models = ["gpt-4o", "gemini-2"]`

## Performance Results

### Competition Results

| System | Rank | Joint Accuracy | T Accuracy | N Accuracy | M Accuracy |
|--------|------|----------------|------------|------------|------------|
| System I | 1st | 0.6543 | 0.7037 | 0.9136 | 0.8889 |
| System II | 2nd | 0.6296 | 0.7284 | 0.9383 | 0.8395 |

## Key Features

- **Clinical Reasoning**: Both systems provide interpretable clinical reasoning for TNM classifications
- **Multi-Model Consensus**: System II simulates collaborative medical expert panels
- **Robust Evaluation**: Strict separation between optimization and evaluation datasets
- **Real-World Applicability**: Handles varying report formats and terminology
- **State-of-the-Art Performance**: Achieved top rankings in international competition

## Citation

If you use this code in your research, please cite our paper:

```bibtex
@article{your_paper_2024,
  title={Multi-Expert LLM Ensemble for Automated TNM Staging from Lung Cancer Radiology Reports},
  author={[Authors]},
  journal={Bioinformatics},
  year={2026},
  note={Submitted}
}
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

We welcome contributions! Please feel free to submit a Pull Request.

## Contact

For questions or issues, please contact:
- [Your Name] - [your.email@institution.edu]
- [Co-author Name] - [coauthor.email@institution.edu]

## Acknowledgments

- NTCIR-18 RadNLP 2024 organizers
- OpenAI for GPT-4o API access
- Google for Gemini-2 API access
- DSPy framework developers

---

**Note**: This repository contains the implementation of systems that achieved 1st and 2nd place in the NTCIR-18 RadNLP 2024 English main task for automated TNM staging from lung cancer radiology reports.
