# VLLM

LLM needs VLLM to serve the model,
issue memory hoarding
It support quantization and tool calling
LLM predicting machine 
Intensive calculation

Aim to solve memory fragmentation to batch execution and distruting inference. Improving gpu usage and latency

Page Attention 
Better manage attention key and value to generate the next token kv-cache 
Memory is divided into measurable chunck(pages in the book)

continuous batching --> fill gpu slot immediately as soon as sequences are completed 

It also includes optimizations for serving models such as CUDA drivers in order to maximize performance on specific hardware

Amongst many tool to serve LLM 

what is AI interencing?
How well an AI performance on completing task?

Traning-->Inferencing Stage
Putting what we learning during training

Training figuring relationship between data
Weights and parameter

Inference --> Real time data
generalize the the stored representation to be able to interpret this new unseen data

calculate the output(actionable result)
what result? 
Eg: 
Flag email if it is spam

Model would learn email would learning feature of a spam email 
Generate a complex equation and fine-tune

Return spam or not spam and this is a probability calculation and tehen associated with the bussiness rule setting the threshold

high cost during inferencing (90%) --> It happens many time

Fast AI model need to received multiple requests

Hardware level: Chips --> Energy efficient ways

middleware: between software and hardware
graph fusion (reduce the number of node in the graph)
parallel tensor (split calcultion into chucks) 

Software level: 
pruning: remove unnecessary weight in the model and thus faster calculation

Inference Engine:

offloading(avoid)
All model can be split into CPU and GPU

try to fit everything in the GPU




