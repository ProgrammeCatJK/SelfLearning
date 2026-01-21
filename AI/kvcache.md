<img width="3322" height="1320" alt="Alculate and store litie" src="https://github.com/user-attachments/assets/29488d9c-cefc-41ed-aa87-b3a756910118" />
# KV Cache (Key-Value Cache)

## What is KV Cache?
KV Cache is an optimization technique used during **Transformer inference** to improve efficiency and speed.

It helps the model **reuse previously computed attention information** instead of recalculating everything from scratch.

Result:
- Faster text generation
- Lower compute cost
- Trade-off: higher memory usage

---

## The Problem
AI models generate text **token by token**.

Without KV cache:
- The model repeatedly recomputes attention for all previous tokens
- This is slow and inefficient, especially for long sequences

---

## The Idea Behind KV Cache
KV Cache **remembers important information from previous steps**.

Instead of recomputing keys and values every time:
- Store them once
- Reuse them for future tokens

---

## What You Need to Understand First
1. **Transformer Architecture**
   - Attention mechanism (Q, K, V)

2. **Autoregressive Modeling**
   - Models generate one token at a time
   - Each new token depends on previous tokens

3. **Linear Algebra Basics**
   - Matrix multiplication
   - Transpose
   - Used heavily in attention computation

---

## Autoregressive Generation (How LLMs Generate Text)

For each new token:
- Look at previous tokens
- Compute probabilities for the next token
- Generate the next token
- Repeat

This process is repeated **for every token**.

---

## What Does KV Cache Store?
KV Cache stores:
- **Keys (K)**
- **Values (V)**

These are intermediate states from the **attention layers** during inference.

---

## How KV Caching Works

### Step-by-Step

1. **First token**
   - Compute key and value
   - Store them in the cache

2. **Next tokens**
   - Retrieve cached keys and values
   - Compute only the new key and value
   - Append them to the cache

3. **Efficient Attention**
   - Use cached K and V
   - Only compute attention using the new query (Q)

4. **Repeat**
   - Add newly generated token to input
   - Continue generation

---

## KV Cache Growth Example

```
Token 1: [K1, V1] ➜ Cache: [K1], [V1]
Token 2: [K2, V2] ➜ Cache: [K1, K2], [V1, V2]
...
Token n: [Kn, Vn] ➜ Cache: [K1, K2, ..., Kn], [V1, V2, ..., Vn]
```

---

## Memory vs Efficiency Trade-off
- KV Cache uses **extra memory** to store past keys and values
- But greatly improves inference speed

Trade-off:
```
More Memory ➜ Faster Inference
```

---

## Simple PyTorch Example (KV Cache)

```python
import torch

class KVCache:
    def __init__(self):
        self.cache = {"key": None, "value": None}

    def update(self, key, value):
        if self.cache["key"] is None:
            self.cache["key"] = key
            self.cache["value"] = value
        else:
            self.cache["key"] = torch.cat([self.cache["key"], key], dim=1)
            self.cache["value"] = torch.cat([self.cache["value"], value], dim=1)

    def get_cache(self):
        return self.cache
```

This shows:
- How keys and values are stored
- How new keys and values are appended
- Why cache size grows with sequence length

---

## Advantages
- Faster inference
- Avoids redundant computation
- Essential for long-context generation
- Widely used in production LLM systems

---

## Disadvantages
- Increased memory usage
- Cache grows with sequence length
- Needs careful memory management

---

## Key Takeaway
KV Cache optimizes **autoregressive Transformer inference** by reusing past attention computations.

It trades **memory for speed**, making large language models practical for real-time use.
