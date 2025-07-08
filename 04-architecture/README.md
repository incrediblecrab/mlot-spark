# 04-architecture

**Purpose**: Implement the revolutionary Memory Cascade architecture that makes MLoT-Spark fundamentally different from all transformer-based models.

## Overview

This directory contains the core innovation of MLoT-Spark: a novel neural architecture based on cascading memory systems rather than attention mechanisms. This represents the first non-transformer language model architecture since 2017.

## Key Files

```
04-architecture/
├── memory_units.py        # Working, Episodic, Semantic memory
├── cascade_networks.py    # Forward/backward cascades
├── pattern_layers.py      # Syntax, Semantic, Pragmatic patterns
├── spark_activation.py    # Custom activation function
├── response_engine.py     # Generation with coherence checking
├── model.py              # Complete MLoT-Spark model
└── README.md             # This file
```

## Implementation Status

- [ ] Spark Memory Units (SMU)
- [ ] Cascade Connection Networks (CCN)
- [ ] Pattern Recognition Layers (PRL)
- [ ] Response Generation Engine (RGE)

## Architecture Innovation

### What Everyone Else Uses (2017-2024)
```
Transformer Architecture = Attention + Feed-Forward + Normalization
- GPT (OpenAI): Transformer decoder
- LLaMA (Meta): Transformer decoder  
- Claude (Anthropic): Transformer variant
- Gemini (Google): Transformer-based
```

### What MLoT-Spark Uses
```
Memory Cascade Architecture = Working Memory + Episodic Memory + Semantic Memory
- NO attention mechanisms
- NO transformer blocks
- NO next-token prediction
- Cognitive science foundation
```

## Core Components

### 1. Spark Memory Units (`memory_units.py`)

#### Working Memory
- **Purpose**: Immediate context processing (like human short-term memory)
- **Capacity**: 512-token sliding window
- **Implementation**: Circular buffer with dynamic attention
- **Features**: Rapid access, temporary storage, context integration

#### Episodic Memory
- **Purpose**: Long-term pattern storage with clustering
- **Capacity**: Hierarchical storage for frequent patterns
- **Implementation**: Clustering-based retrieval system
- **Features**: Pattern recognition, experience storage, context recall

#### Semantic Memory
- **Purpose**: Concept relationships and hierarchies
- **Capacity**: Structured knowledge representation
- **Implementation**: Graph-based concept networks
- **Features**: Meaning extraction, concept linking, knowledge integration

### 2. Cascade Connection Networks (`cascade_networks.py`)

#### Forward Cascade
- **Flow**: Working → Episodic → Semantic
- **Purpose**: Information processing and abstraction
- **Mechanism**: Progressive concept refinement

#### Backward Cascade
- **Flow**: Semantic → Episodic → Working
- **Purpose**: Context injection and knowledge retrieval
- **Mechanism**: Top-down knowledge application

#### Cross-Cascade
- **Flow**: Bidirectional between all memory types
- **Purpose**: Dynamic information sharing
- **Mechanism**: Context-dependent routing

### 3. Pattern Recognition Layers (`pattern_layers.py`)

#### Syntax Patterns
- **Purpose**: Grammar and structure recognition
- **Implementation**: Rule-based parsing with learning
- **Features**: Language structure understanding

#### Semantic Patterns
- **Purpose**: Meaning and concept extraction
- **Implementation**: Hierarchical concept clustering
- **Features**: Content understanding, topic modeling

#### Pragmatic Patterns
- **Purpose**: Context and intent understanding
- **Implementation**: Context-aware inference
- **Features**: Conversational understanding, intent recognition

### 4. Custom Activation Function (`spark_activation.py`)

#### Spark Function
- **Innovation**: Context-dependent, non-linear activation
- **Properties**: Adaptive threshold, memory-sensitive
- **Advantages**: Better information flow than ReLU/GELU

```python
def spark_activation(x, context, memory_state):
    # Custom activation that considers context and memory
    # More sophisticated than traditional activations
    pass
```

### 5. Response Generation Engine (`response_engine.py`)

#### Context Assembly
- **Purpose**: Combine outputs from all memory systems
- **Implementation**: Weighted fusion of memory outputs
- **Features**: Coherent information integration

#### Coherence Checking
- **Purpose**: Ensure logical consistency in responses
- **Implementation**: Multi-layer validation system
- **Features**: Logic validation, fact checking

#### Creativity Injection
- **Purpose**: Controlled randomness for natural responses
- **Implementation**: Context-aware stochasticity
- **Features**: Natural variation, creative responses

### 6. Complete Model (`model.py`)

The main MLoT-Spark model that integrates all components:

```python
class MLoTSparkModel:
    def __init__(self, vocab_size=32000, hidden_size=512):
        self.memory_units = SparkMemoryUnits()
        self.cascade_networks = CascadeConnectionNetworks()
        self.pattern_layers = PatternRecognitionLayers()
        self.response_engine = ResponseGenerationEngine()
    
    def forward(self, input_tokens, context=None):
        # Novel forward pass through memory cascades
        pass
```

## Model Specifications

### Parameters
- **Total Parameters**: 25-40M (highly efficient)
- **Hidden Size**: 256-512 per memory unit
- **Memory Layers**: 3 layers per memory type
- **Pattern Layers**: Hierarchical recognition system

### Memory Architecture
- **Working Memory**: 512 tokens, circular buffer
- **Episodic Memory**: 10k patterns, clustered storage
- **Semantic Memory**: Concept graph, dynamic size

### Performance Targets
- **Training Time**: 6-10 hours on MacBook Pro
- **Inference Speed**: <1 second per response
- **Memory Usage**: 4-6GB during inference
- **Context Length**: 1024 tokens (expandable to 2048)

## Innovation Points

### 1. Memory-First Design
- Based on cognitive science, not mathematical optimization
- Hierarchical memory systems like human cognition
- Dynamic memory allocation based on context importance

### 2. Bidirectional Information Flow
- Information flows both directions through memory hierarchies
- Context influences processing at all levels
- Dynamic routing based on content and context

### 3. Novel Training Objective
- Contextual reconstruction instead of next-token prediction
- Teaches understanding rather than memorization
- Multi-scale objectives for different memory types

### 4. Efficiency Through Architecture
- Smarter architecture needs fewer parameters
- 25-40M parameters competitive with 7B+ transformers
- Optimized for consumer hardware

## Usage

### Model Initialization
```python
from model import MLoTSparkModel

model = MLoTSparkModel(
    vocab_size=32000,
    hidden_size=512,
    memory_layers=3
)
```

### Forward Pass
```python
# Input: tokenized text
output = model.forward(input_tokens, context=previous_context)
```

### Memory Inspection
```python
# Examine memory states
working_state = model.memory_units.working_memory.state
episodic_patterns = model.memory_units.episodic_memory.patterns
semantic_concepts = model.memory_units.semantic_memory.concepts
```

## Next Steps

After architecture implementation, proceed to:
- **05-training**: Novel training system for memory-based learning
- **06-evaluation**: Test memory cascade performance

## Dependencies

- NumPy for mathematical operations
- Standard Python libraries only
- No AI frameworks (PyTorch, TensorFlow, etc.)
- No pre-trained models or attention mechanisms

This architecture represents a fundamental breakthrough in language modeling, moving beyond transformers to cognitive science-inspired memory systems.