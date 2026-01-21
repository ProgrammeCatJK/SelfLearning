# Mixture of Experts (MoE)

## What is MoE?
**Mixture of Experts (MoE)** is a neural network architecture designed to improve **efficiency** and **scalability** by conditionally activating only a small subset of model parameters for each input.

Instead of using the full model for every token, MoE dynamically selects a few specialized sub-networks (*experts*) to process the input, making inference and training faster at large scales.

---

## Why is MoE faster?
- Only a **fraction of the total parameters** are activated per input
- Reduces computation compared to dense models of similar size
- Enables extremely large models without proportional compute cost

---

## Core Idea

### Replacing FFN with MoE
In Transformer models:
- The standard **Feed-Forward Network (FFN)** layers are replaced with **sparse MoE layers**
- These layers use **thin and scattered activation**, meaning only selected experts are used

---

## Components

### Experts
- A collection of independent sub-networks
- Typically **8 to 2048 experts**
- Each expert is a small neural network
- Experts tend to specialize in different input patterns or tasks

### Router (Gating Network)
- Learns how to route each token
- Assigns tokens to **one or more experts**
- Routing decision is based on the input context
- Key challenge: balancing expert usage and avoiding overload

---

## How It Works (High-Level)
1. Input token enters the MoE layer
2. Router computes scores for all experts
3. Top-k experts are selected
4. Only selected experts process the token
5. Outputs are combined and passed forward

---

## Use Cases

### Multilingual Translation & Chat
- Experts specialize in different languages or linguistic patterns
- Improves performance without increasing inference cost per token

### Voice & Multimodal Assistants
- Different experts handle:
  - Speech
  - Text
  - Vision
- Efficient scaling across modalities

### Enterprise Copilots
- Experts specialize in:
  - Code generation
  - Document understanding
  - Business logic
- Enables scalable and cost-efficient enterprise AI systems

---

## Key Takeaways
- MoE trades **dense computation** for **conditional computation**
- Enables massive models with manageable cost
- Routing quality is critical to performance
- Commonly used in large-scale production LLMs