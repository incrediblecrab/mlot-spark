# 03-tokenization

**Purpose**: Build a custom Byte-Pair Encoding (BPE) tokenizer from scratch for the MLoT-Spark language model.

## Overview

This directory implements a complete tokenization system built from the ground up. Unlike using existing tokenizers, we create our own BPE implementation to generate a 32,000-token vocabulary specifically optimized for our training corpus and memory-based architecture.

## Key Files

```
03-tokenization/
├── bpe_tokenizer.py       # Core BPE algorithm implementation
├── vocab_builder.py       # Build vocabulary from corpus
├── tokenize_dataset.py    # Apply tokenizer to dataset
├── special_tokens.py      # Handle [PAD], [START], [END], etc.
├── tokenizer_test.py      # Verify tokenizer quality
└── README.md             # This file
```

## Implementation Status

- [ ] Byte-Pair Encoding implementation
- [ ] Vocabulary builder (32k tokens)
- [ ] Tokenization/detokenization tools
- [ ] Special token handling

## BPE Algorithm Overview

Byte-Pair Encoding iteratively merges the most frequent character pairs to build subword units:

1. **Initialize**: Start with character-level tokens
2. **Count pairs**: Find most frequent adjacent token pairs
3. **Merge**: Replace most frequent pair with new token
4. **Repeat**: Continue until target vocabulary size (32,000)
5. **Finalize**: Create encoding/decoding tables

## Components

### 1. Core BPE Implementation (`bpe_tokenizer.py`)
- **Character initialization**: Start with UTF-8 characters
- **Pair counting**: Efficient frequency counting
- **Merge operations**: Replace pairs with new tokens
- **Vocabulary management**: Track token mappings
- **Encoding/decoding**: Convert text ↔ token IDs

### 2. Vocabulary Builder (`vocab_builder.py`)
- **Corpus analysis**: Analyze training text statistics
- **Token frequency**: Count character and subword frequencies
- **Merge selection**: Choose optimal merges for vocabulary
- **Special token integration**: Reserve slots for special tokens
- **Vocabulary serialization**: Save/load vocabulary files

### 3. Dataset Tokenization (`tokenize_dataset.py`)
- **Batch processing**: Tokenize large datasets efficiently
- **Progress tracking**: Monitor tokenization progress
- **Output formatting**: Create training-ready token sequences
- **Validation**: Verify tokenization quality

### 4. Special Token Handling (`special_tokens.py`)
- **Reserved tokens**: [PAD], [START], [END], [UNK]
- **Memory tokens**: Special tokens for memory operations
- **Context markers**: Beginning/end of context segments
- **Token ID management**: Assign consistent IDs

### 5. Quality Testing (`tokenizer_test.py`)
- **Round-trip testing**: Encode → decode → verify
- **Coverage analysis**: Vocabulary coverage of corpus
- **Compression ratio**: Measure tokenization efficiency
- **Edge case testing**: Handle unusual text patterns

## Tokenizer Specifications

### Target Vocabulary
- **Size**: 32,000 tokens
- **Coverage**: >95% of training corpus
- **Special tokens**: ~100 reserved slots
- **Subword tokens**: ~31,900 learned tokens

### Special Tokens
```
ID    Token       Purpose
0     [PAD]       Padding sequences
1     [START]     Beginning of sequence
2     [END]       End of sequence
3     [UNK]       Unknown/rare tokens
4     [MASK]      Masked tokens for training
5-99  [MEM_*]     Memory system tokens
```

### Performance Targets
- **Encoding speed**: >1M tokens/second
- **Compression ratio**: ~3-4x vs character-level
- **Memory usage**: <2GB during vocabulary building
- **Accuracy**: >99.9% round-trip fidelity

## Usage

### Building Vocabulary
```bash
python vocab_builder.py --corpus ../02-data-preprocessing/processed_data --vocab_size 32000
```

### Tokenizing Dataset
```bash
python tokenize_dataset.py --input ../02-data-preprocessing/processed_data --output ./tokenized_data
```

### Testing Quality
```bash
python tokenizer_test.py --vocab_file ./vocabulary.json --test_data ./test_samples.txt
```

## Data Flow

```
Processed Text (from 02-data-preprocessing)
    ↓
Character Analysis (frequency counting)
    ↓
BPE Training (iterative merging)
    ↓
Vocabulary Creation (32k tokens)
    ↓
Dataset Tokenization (text → token IDs)
    ↓
Quality Validation (round-trip testing)
```

## Output Files

- **vocabulary.json**: Complete token vocabulary
- **merges.txt**: BPE merge operations
- **tokenized_dataset/**: Training data as token sequences
- **tokenizer_stats.json**: Quality and performance metrics

## Next Steps

After tokenization, proceed to:
- **04-architecture**: Design model architecture for token sequences
- **05-training**: Implement training with tokenized data

## Dependencies

- Standard Python libraries only
- NumPy for efficient array operations
- JSON for vocabulary serialization

## Memory Requirements

- **Vocabulary building**: ~4-6GB RAM
- **Dataset tokenization**: ~2-4GB RAM
- **Inference**: <100MB RAM