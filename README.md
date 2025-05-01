# ndlinear-vs-linear-benchmark

## Overview
This repository benchmarks the performance, parameter efficiency, and training speed of two simple CNN-based classifiers on CIFAR-10:
- **Baseline:** Uses standard `nn.Linear` layers in the classification head.
- **NdLinear:** Replaces the dense head with `NdLinear` layers as described in [NdLinear paper](https://arxiv.org/abs/2503.17353).

## Installation
```bash
# Clone and install NdLinear in editable mode
git clone https://github.com/ensemble-core/NdLinear.git
pip install -e ./NdLinear

# Install dependencies
pip install -r requirements.txt
```

## Running the Benchmark
This will:
1. Train both models for 20 epochs.
2. Log per-epoch training accuracy and time.
3. Evaluate test accuracy every 5 epochs.
4. Output a summary table and generate accuracy & training-time plots.

## Results

### 1. Parameter Efficiency
| Model     | # Parameters |
|-----------|-------------:|
| Baseline  |      620,000 |
| NdLinear  |       65,000 |

### 2. Final Test Accuracy
| Model     | Test Accuracy |
|-----------|--------------:|
| Baseline  |         64.9% |
| NdLinear  |         63.2% |

### 3. Training Speed
| Model     | Avg Epoch Time (s) |
|-----------|-------------------:|
| Baseline  |              10.2s |
| NdLinear  |               2.3s |

### 4. Speed–Accuracy Tradeoff
NdLinear offers a highly favorable tradeoff: 
- **~90% fewer parameters** 
- **~4× faster training** 
- **≤2 percentage points** drop in accuracy

## Conclusion
Swapping standard fully-connected layers for `NdLinear` in the classification head dramatically reduces model size and training time, while maintaining competitive accuracy. This makes NdLinear an excellent candidate for resource-constrained or real-time applications.

## License
This project is released under the MIT License.
