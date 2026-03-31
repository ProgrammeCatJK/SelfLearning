VLLM inference Report and Analysis

With inference framework
User expereince --> Low latency
reduce setup cost --> reduce resource
more compaticble with hardware --> Support hardware

部署工具:
Ollama, LocalAI, LM Studio, PrivateGPT

推理服务框架 
Text Generation Inference
Triton Inference Sercer 
LMDeploy 

底层优化引擎
vLLM 
TensorRT-LLM
llama.cpp 
MLX/Metal
ExLlamV2

硬件接口
2023年底添加了对Apple Silicon的初步支持
• 通过Metal Performance Shaders实现
• 在M1/M2/M3上性能表现尚可，但不如NVIDIA GPU优化充分
• 最新版本支持在Apple芯片上运行Mistral和Llama系列模型

LLaMA.cpp
MLX

Apple M2 Ultra 7B (tokens/s)

框架	FP16	INT8	INT4	内存效率
MLX	    ~80	    ~120    ~150    ★★★★★
llama.cpp (Metal)	
        ~40	    ~75	    ~95	    ★★★★★
Ollama  ~35 	~70 	~90 	★★★★☆
vLLM	~30	    ~45	    ~60	    ★★★☆☆
MLC-LLM	~45	    ~80	    ~100	★★★★☆

MLX框架是最好的

Apple Silicon特有优化技术
1. 统一内存架构利用
• CPU和GPU共享同一内存空间，无需显式数据传输
• MLX和MLC-LLM充分利用这一特性

Nvidia A100 15w
Apple M2 Ultra
Apple M3 Ultra 512G 4TB
NVIDIA RTX 4090