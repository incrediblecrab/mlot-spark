# 02-data-preprocessing

**Purpose**: Clean and prepare raw text data from the collection phase for training the MLoT-Spark language model.

## Overview

This directory implements the data preprocessing pipeline that transforms raw downloaded text into clean, training-ready format. The pipeline removes noise, filters quality, detects language, and eliminates duplicates to create a high-quality training corpus.

## Key Files

```
02-data-preprocessing/
├── clean_text.py           # Remove headers, footers, metadata
├── filter_quality.py       # Quality checks and filtering
├── deduplicate.py         # Remove duplicate content
├── preprocess_pipeline.py  # Full preprocessing pipeline
├── stats_analyzer.py      # Dataset statistics
└── README.md              # This file
```

## Implementation Status

- [ ] Text cleaning pipeline
- [ ] Quality filtering system
- [ ] Language detection
- [ ] Deduplication

## Processing Steps

### 1. Text Cleaning (`clean_text.py`)
- **Remove metadata**: Headers, footers, copyright notices
- **Normalize encoding**: Convert to UTF-8
- **Clean formatting**: Remove excessive whitespace, fix line breaks
- **Extract content**: Separate actual text from markup

### 2. Quality Filtering (`filter_quality.py`)
- **Length filtering**: Remove texts that are too short/long
- **Language detection**: Keep only English content
- **Character filtering**: Remove non-printable characters
- **Content validation**: Filter out low-quality or corrupted text

### 3. Deduplication (`deduplicate.py`)
- **Exact matching**: Remove identical text segments
- **Near-duplicate detection**: Identify similar content using hashing
- **Cross-source deduplication**: Remove overlaps between data sources
- **Preserve diversity**: Keep representative samples

### 4. Pipeline Integration (`preprocess_pipeline.py`)
- **Orchestrate processing**: Run all steps in sequence
- **Progress tracking**: Monitor processing status
- **Error handling**: Robust processing with recovery
- **Output organization**: Create clean dataset structure

### 5. Statistics Analysis (`stats_analyzer.py`)
- **Dataset metrics**: Size, vocabulary, distribution
- **Quality assessment**: Analyze text characteristics
- **Source analysis**: Compare different data sources
- **Validation reports**: Ensure preprocessing quality

## Data Flow

```
Raw Data (from 01-data-collection)
    ↓
Text Cleaning (remove noise)
    ↓
Quality Filtering (language, length, content)
    ↓
Deduplication (exact and near-duplicates)
    ↓
Clean Dataset (ready for tokenization)
    ↓
Statistics Analysis (quality validation)
```

## Expected Output

- **Clean text files**: Processed and filtered content
- **Dataset manifest**: Index of all processed files
- **Quality report**: Statistics and validation metrics
- **Processing log**: Record of all transformations

## Usage

Once implemented, run the preprocessing pipeline:

```bash
python preprocess_pipeline.py --input ../01-data-collection/raw_data --output ./processed_data
```

This will:
1. Clean all raw text files
2. Apply quality filters
3. Remove duplicates
4. Generate processing statistics
5. Create training-ready dataset

## Quality Metrics

Target metrics after preprocessing:
- **Language purity**: >99% English content
- **Deduplication rate**: <5% near-duplicates remaining
- **Average text quality**: High readability scores
- **Size reduction**: ~20-30% from raw to clean

## Next Steps

After preprocessing, proceed to:
- **03-tokenization**: Build custom BPE tokenizer from clean text
- **04-architecture**: Design model architecture for processed data

## Dependencies

- Standard Python libraries
- Optional: `langdetect` for language detection
- Optional: `nltk` for text analysis utilities