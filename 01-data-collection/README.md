# 01-data-collection

**Purpose**: Download and organize datasets from public sources for training the MLoT-Spark language model.

## Overview

This directory implements the data collection pipeline that gathers training data from four primary sources:
- **40%** Project Gutenberg (pre-1925 literature)
- **30%** Wikipedia Commons (historical/scientific articles)  
- **20%** arXiv papers (mathematics, physics, CS - pre-2020)
- **10%** Public domain news articles and journals

**Target**: ~5GB of cleaned, copyright-free text data

## Key Files

```
01-data-collection/
├── download_gutenberg.py    # Project Gutenberg books
├── download_wikipedia.py    # Wikipedia Commons articles
├── download_arxiv.py        # arXiv papers (pre-2020)
├── download_news.py         # Public domain news
├── download_manager.py      # Orchestrate all downloads
└── README.md               # This file
```

## Implementation Status

- [ ] Dataset download scripts for each source
- [ ] Automated collection pipeline
- [ ] Data organization and storage
- [ ] Download progress tracking

## Data Sources

### Project Gutenberg (40% of dataset)
- **Content**: Pre-1925 literature (copyright-free)
- **Format**: Plain text books
- **Advantages**: Rich vocabulary, diverse writing styles
- **Estimated Size**: ~2GB

### Wikipedia Commons (30% of dataset)
- **Content**: Historical and scientific articles
- **Format**: Article text (no markup)
- **Advantages**: Factual content, encyclopedic knowledge
- **Estimated Size**: ~1.5GB

### arXiv Papers (20% of dataset)
- **Content**: Academic papers (mathematics, physics, CS)
- **Timeframe**: Pre-2020 papers only
- **Format**: Abstract and full text
- **Advantages**: Technical vocabulary, formal writing
- **Estimated Size**: ~1GB

### Public Domain News (10% of dataset)
- **Content**: Historical news articles and journals
- **Format**: Article text
- **Advantages**: Current events, journalistic style
- **Estimated Size**: ~0.5GB

## Usage

Once implemented, run the data collection pipeline:

```bash
python download_manager.py
```

This will:
1. Download data from all sources
2. Organize files by source type
3. Track download progress
4. Create dataset manifest
5. Prepare for preprocessing step

## Next Steps

After data collection, proceed to:
- **02-data-preprocessing**: Clean and filter the collected text
- **03-tokenization**: Build custom BPE tokenizer from the dataset

## Dependencies

- Standard Python libraries only
- Internet connection for downloads
- ~15GB available disk space (raw + processed data)