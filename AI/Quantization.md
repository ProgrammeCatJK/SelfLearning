# Quantization of LLM Models

## What is Quantization?
Quantization is the process of reducing the precision of model parameters to make large language models more efficient.

Example:
- FP32 → FP16 → INT8 → INT4

Lower precision means:
- Smaller model size
- Lower VRAM usage
- Faster inference

Trade-off: possible loss in accuracy

---

## Why Quantize LLMs?
- Bigger models require more VRAM
- Quantization reduces memory footprint
- Enables running large models on limited hardware

Example:
```
70B model → quantized version ≈ much smaller runtime footprint
```

(⚠️ Parameter count stays the same, but storage and compute cost drop)

---

## Core Idea
Quantization reduces the accuracy of parameter values, not the number of parameters.

- FP32: high precision, high cost
- INT8: low precision, low cost

---

## Affine Quantization Scheme

Quantized weight calculation:

```
quantized_weight_val = round(weight / scaling_factor + zero_point)
```

### Scaling Factor
- Positive FP32 value
- Scales the original weight values into INT8 range

### Zero Point
- INT8 value
- Represents where float32 value = 0 maps in INT8

---

## Calibration

Calibration squeezes the high dynamic range of FP32 values into the 255 values of INT8.

Key idea:
- Once the max value is known
- Other values are scaled relative to it

---

## Scale Factor Formula

```
scale_factor = (2^n - 1) / max_value
```

Where:
- n = number of bits (e.g. 8 for INT8)
- max_value = maximum absolute weight value

---

## How Quantization Works (Intuition)

1. Find max value in weights
2. Compute scale factor
3. Divide weights by scale factor
4. Round values (approximation)
5. Store in INT8 range

Rounding = loss of precision

---

## Types of Quantization

### Post-Training Quantization (PTQ)
- Applied after the LLM is fully trained
- Requires calibration
- Faster to apply
- Slightly higher accuracy loss

---

### Quantization-Aware Training (QAT)
- Model is fine-tuned with quantization in mind
- Simulates quantization during training
- Reduces accuracy loss
- Less calibration needed after training

---

## Advantages
- Faster inference response
- Less energy consumption
- Lower cost
- Enables local or edge deployment

---

## Disadvantages
- Potential loss in accuracy
- High-precision weights are squeezed into low precision
- Poor calibration can hurt performance

---

## Key Takeaway
Quantization trades precision for efficiency.

The goal is acceptable accuracy loss for large gains in:
- Speed
- Cost
- Scalability