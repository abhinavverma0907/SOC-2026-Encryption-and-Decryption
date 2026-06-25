# SOC 2026 — Encryption & Decryption Project
## Midterm Submission

---

## Overview
Progression from data analysis → neural networks → specialized architectures for cipher breaking.

---

## Week 0 — Foundation (Data & Pandas)

**Assignments:**
- Q1: Detective case using Pandas filtering (Finding the Killer — Jhon Williams)
- Q2: Rocket fuel data analysis + cleaning + visualization

**Key Skills Learned:**
- Pandas: load, clean, filter, sort, visualize data
- Matplotlib: histograms, bar charts, scatter plots
- GitHub workflow + Colab integration

**Parameters:** N/A (data analysis, not ML)

**Accuracy/Results:** 
- Q1: Correctly identified killer (Jhon Williams, age 44, joined 2010)
- Q2: Cleaned dataset, created Power_Index column, saved modified.csv

---

## Week 1 — Neural Networks & Caesar Cipher

**Assignments:**
- Q1: Iris flower classification with Multi-Layer Perceptron
- Q2: Caesar cipher cracking using frequency analysis

**Q1 — Iris MLP**
- Architecture: Input(4) → Linear(16) → ReLU → Linear(3)
- Parameters: ~320 total
- Training: 200 epochs, SGD optimizer, lr=0.01
- **Accuracy: 96.67%** (3 flower species)

**Q2 — Caesar Cipher**
- Method: Frequency analysis (no brute force)
- Key insight: most common char in ciphertext = encrypted space
- Successfully decrypted Mary Queen of Scots' 1586 letter
- Shift identified: 17

---

## Week 2 — MLP for Shift Prediction

**Assignment:** Train MLP to predict Caesar shift (1–32) from ciphertext

**Architecture:** Input(20) → Linear(128) → ReLU → Linear(64) → ReLU → Linear(32)

**Parameters Chosen:**
- Hidden layers: 128, 64 neurons
- Batch size: 64
- Learning rate: 0.001
- Optimizer: Adam
- Epochs: 15
- Activation: ReLU

**Dataset:**
- Text: Pride & Prejudice (~705K chars)
- All 32 shifts applied to entire text
- 20-character windows
- Total samples: 1,128,640 (~35,270 per shift)
- 80/20 train/test split

**Results:**
- **Final Test Accuracy: 38.93%**
- Random baseline: 3.125% (1 in 32)
- Loss: 3.22 → 2.04
- Improvement: **1145% over random**

**Key Insight:** MLP learns implicit frequency patterns without being programmed explicitly.

---

## Week 3 — RNN for Substitution Cipher

**Assignment:** Identify which of 3 permutation ciphers was used

**Architecture:**
- Embedding: 33 → 32 dims
- RNN: 1 layer, 128 hidden units
- Max pooling over time
- Linear: 128 → 3 classes

**Parameters Chosen:**
- Embedding dim: 32
- RNN hidden size: 128
- Batch size: 128
- Learning rate: 0.001
- Optimizer: Adam
- Epochs: 10

**Dataset:**
- 3 fixed random permutations
- 20-character sequences
- Total samples: 35,270 (balanced)
- 80/20 train/test split

**Results:**
- **Final Test Accuracy: 99.97%** 🎉
- Random baseline: 33.33%
- Loss: 0.1291 → 0.0012
- Hit 100% at epoch 9

**Why RNN > MLP:**
- MLP: treats all 20 chars independently
- RNN: sequential processing with memory
- RNN captures character dependencies → much better performance

**Limitation Noted:** RNNs have short-term memory. Works for 2–3 permutations; fails for hundreds. This led to Transformers (2017).

---

## Week 4 — LSTM Sequence-to-Sequence Decryption

**Assignment:** Learn to decrypt Caesar cipher directly (seq2seq)

**Architecture:**
- Embedding: 33 → 64 dims
- LSTM: 2 layers, 256 hidden units, 30% dropout
- Linear: 256 → 33 (vocab size)
- Seq2seq: each position predicts decrypted char

**Parameters Chosen:**
- Embedding dim: 64
- LSTM hidden size: 256
- LSTM layers: 2
- Dropout: 0.3
- Batch size: 64
- Learning rate: 0.001
- Optimizer: Adam
- Epochs: 15
- Sequence length: 30

**Dataset:**
- All 32 Caesar shifts
- 30-character ciphertext → plaintext pairs
- Total pairs: ~670,000
- 80/20 train/test split

**Results:**
- **Final Test Accuracy: 94.14%**
- Loss: from 0.4218 to 0.1918
- This is seq2seq (harder): predicting every character, not just classifying

**Why LSTM > RNN:**
- LSTM uses gates (forget/input/output) to maintain long-term memory
- RNN has single hidden state (vanishing gradient problem)
- LSTM better handles long sequences (30 chars)

---

## Code Explanation Summary

### Week 0–1: Basic ML
- Load data → split → train → evaluate
- Simple architectures (MLP)
- Classical algorithms (frequency analysis)

### Week 2–3: Deep Learning
- Neural networks learn feature patterns
- RNN introduces sequential memory
- Accuracy scales with data (1M vs 35K samples)

### Week 4: Seq2Seq
- Input sequence → output sequence (not just classification)
- LSTM's gating mechanism prevents short-term memory loss
- Harder problem = needs more capacity

### Common patterns across all weeks:
1. **Data preparation:** clean, encode as numbers
2. **Model design:** define architecture
3. **Training loop:** forward → loss → backward → optimize
4. **Evaluation:** accuracy on held-out test set
5. **Visualization:** loss curves + sample predictions

---

## Technologies Used
- **PyTorch:** neural network library
- **scikit-learn:** Iris dataset, preprocessing
- **Pandas:** data manipulation
- **Matplotlib:** visualization
- **Project Gutenberg:** text source
---
## Progression Overview
```
Week 0: Pandas fundamentals
   ↓
Week 1: First neural networks (MLP)
   ↓
Week 2: Scaling up (1M samples, 32 classes)
   ↓
Week 3: Sequential models (RNN)
   ↓
Week 4: Advanced seq2seq (LSTM)
   ↓
Next: Transformers, Attention, Production deployment
```
---
## Submitted By
Abhinav Verma

**Repo:** https://github.com/abhinavverma0907/SOC-2026-Encryption-and-Decryption
