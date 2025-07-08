# 05-training

**Purpose**: Implement a novel training system specifically designed for the memory-based architecture of MLoT-Spark.

## Overview

This directory implements a revolutionary training approach that moves beyond next-token prediction to contextual reconstruction learning. The training system is designed to teach the memory cascade architecture how to understand and generate language through hierarchical memory consolidation.

## Key Files

```
05-training/
├── loss_functions.py      # Contextual reconstruction losses
├── training_loop.py       # Main training logic
├── curriculum.py         # Progressive difficulty scheduling
├── memory_transfer.py    # Episodic → Semantic consolidation
├── checkpointing.py      # Save/load model states
├── train.py             # Training entry point
└── README.md            # This file
```

## Implementation Status

- [ ] Contextual reconstruction loss
- [ ] Multi-scale objectives
- [ ] Progressive curriculum
- [ ] Memory consolidation

## Training Innovation

### Traditional Approach (All Other Models)
```
Next-Token Prediction: "The cat sat on the ___" → "mat"
- Predicts one token at a time
- Left-to-right generation only
- Memorization-focused learning
```

### MLoT-Spark Approach
```
Contextual Reconstruction: "The ___ sat on the mat" → "cat"
- Predicts missing segments from context
- Bidirectional understanding
- Comprehension-focused learning
```

## Core Components

### 1. Loss Functions (`loss_functions.py`)

#### Contextual Reconstruction Loss
- **Purpose**: Train model to understand context, not just predict next token
- **Mechanism**: Mask random segments, predict from surrounding context
- **Advantage**: Teaches understanding rather than memorization

#### Memory Consistency Loss
- **Purpose**: Ensure memory systems maintain coherent representations
- **Mechanism**: Validate consistency between working, episodic, and semantic memory
- **Advantage**: Stable memory formation and retrieval

#### Hierarchical Learning Loss
- **Purpose**: Train different memory systems at appropriate scales
- **Mechanism**: Different objectives for working vs episodic vs semantic memory
- **Advantage**: Optimized learning for each memory type

#### Coherence Loss
- **Purpose**: Ensure generated responses are logically consistent
- **Mechanism**: Multi-step validation of response coherence
- **Advantage**: Higher quality, more reliable outputs

### 2. Training Loop (`training_loop.py`)

#### Memory-Aware Training
- **Working Memory**: Short-term pattern recognition
- **Episodic Memory**: Medium-term pattern consolidation
- **Semantic Memory**: Long-term concept formation

#### Dynamic Learning Rates
- **Adaptive scheduling**: Different rates for different memory systems
- **Context-dependent**: Adjust based on learning progress
- **Memory-specific**: Optimize each memory type independently

#### Batch Processing
- **Context batching**: Group similar contexts for efficient training
- **Memory-aware batching**: Consider memory states in batch formation
- **Progressive difficulty**: Gradually increase batch complexity

### 3. Curriculum Learning (`curriculum.py`)

#### Progressive Difficulty
```
Week 1-2: Simple patterns (short sentences, basic vocabulary)
Week 3-4: Complex patterns (long sentences, diverse vocabulary)
Week 5-6: Advanced patterns (multi-sentence coherence, reasoning)
```

#### Memory Development Stages
1. **Working Memory Training**: Immediate context processing
2. **Episodic Memory Training**: Pattern storage and retrieval
3. **Semantic Memory Training**: Concept formation and relationships
4. **Integrated Training**: All memory systems working together

#### Adaptive Curriculum
- **Performance monitoring**: Adjust difficulty based on learning progress
- **Dynamic scheduling**: Speed up or slow down based on mastery
- **Memory-specific pacing**: Different schedules for different memory types

### 4. Memory Consolidation (`memory_transfer.py`)

#### Episodic → Semantic Transfer
- **Pattern promotion**: Move frequent patterns from episodic to semantic memory
- **Concept formation**: Abstract patterns into higher-level concepts
- **Memory optimization**: Consolidate similar patterns for efficiency

#### Memory Pruning
- **Importance scoring**: Identify which memories to keep vs discard
- **Capacity management**: Maintain optimal memory usage
- **Quality control**: Remove low-quality or inconsistent memories

#### Consolidation Scheduling
- **Regular intervals**: Periodic memory consolidation during training
- **Trigger-based**: Consolidate when memory reaches capacity
- **Performance-based**: Consolidate based on learning metrics

### 5. Checkpointing (`checkpointing.py`)

#### Comprehensive State Saving
- **Model parameters**: All neural network weights
- **Memory states**: Working, episodic, and semantic memory contents
- **Training progress**: Learning curves, curriculum position
- **Optimizer states**: For resuming training exactly

#### Efficient Storage
- **Compressed format**: Reduce checkpoint file sizes
- **Incremental saves**: Only save changes since last checkpoint
- **Memory-aware**: Optimize for memory architecture specifics

#### Recovery System
- **Robust loading**: Handle corrupted or incomplete checkpoints
- **Version compatibility**: Load checkpoints from different model versions
- **Progressive recovery**: Fallback to earlier checkpoints if needed

### 6. Training Entry Point (`train.py`)

Main training script that orchestrates the entire process:

```python
def main():
    # Load tokenized dataset
    # Initialize MLoT-Spark model
    # Set up training loop with curriculum
    # Begin memory-cascade training
    # Save checkpoints and monitor progress
```

## Training Specifications

### Objectives
- **Primary**: Contextual reconstruction (70% of loss)
- **Secondary**: Memory consistency (20% of loss)
- **Tertiary**: Coherence validation (10% of loss)

### Schedule
- **Total Time**: 6-10 hours on MacBook Pro M2
- **Batch Size**: 32-64 sequences
- **Learning Rate**: Adaptive, memory-specific
- **Epochs**: Variable based on convergence

### Hardware Requirements
- **Memory**: 8-12GB RAM during training
- **Storage**: 5GB for checkpoints
- **Compute**: M1/M2 MacBook Pro optimized

## Training Process

### Phase 1: Foundation (Hours 0-2)
1. Initialize memory systems
2. Begin working memory training
3. Learn basic token patterns
4. Establish vocabulary usage

### Phase 2: Development (Hours 2-6)
1. Episodic memory development
2. Pattern storage and retrieval
3. Context understanding
4. Memory consolidation begins

### Phase 3: Integration (Hours 6-8)
1. Semantic memory formation
2. Concept relationship learning
3. Full cascade integration
4. Coherence optimization

### Phase 4: Refinement (Hours 8-10)
1. Fine-tune all systems
2. Optimize memory efficiency
3. Final consolidation
4. Performance validation

## Monitoring & Metrics

### Loss Tracking
- **Reconstruction loss**: How well model predicts from context
- **Memory consistency**: Stability of memory representations
- **Coherence score**: Quality of generated responses

### Memory Analysis
- **Working memory usage**: Efficiency of immediate processing
- **Episodic patterns**: Quality and diversity of stored patterns
- **Semantic concepts**: Coherence of concept formation

### Performance Metrics
- **Training speed**: Tokens processed per second
- **Memory efficiency**: RAM usage during training
- **Convergence rate**: Speed of loss reduction

## Usage

### Start Training
```bash
python train.py --dataset ../03-tokenization/tokenized_data --model_config config.json
```

### Resume Training
```bash
python train.py --resume checkpoints/latest_checkpoint.pt
```

### Monitor Progress
```bash
python training_loop.py --monitor --checkpoint_dir checkpoints/
```

## Next Steps

After training completion, proceed to:
- **06-evaluation**: Comprehensive model evaluation
- **07-inference**: Optimize for fast inference

## Dependencies

- NumPy for mathematical operations
- Standard Python libraries
- No external ML frameworks
- Custom implementation throughout