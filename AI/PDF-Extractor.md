# Document Parsing & Local LLM Deployment with MinerU & vLLM
---

## ⚡ Overview

- **Local Server Deployment**: MinerU + vLLM 
- **vLLM Advantages**:  
  - Faster inference  
  - Integration with LangChain (MCP server)  
  - Supports multi-modal PDFs and images  

---

## 🗂️ LLM File Processing Pipeline

General workflow for document processing:

```
Document (PDF, Word, Excel)
        ↓
File Parser
        ↓
Text / Structured Data
        ↓
(Optional) Chunking + Vectorization (RAG)
        ↓
LLM Inference / Q&A / Summarization
```

> Note: PDF files are complex — they contain text, images, tables, charts, etc.  
> Context is expressed through titles, images, and table formats — all need to be preserved.

---

## 📄 Document Parsing Steps

### 1. PDF → Structured Output

- **Extract text / tables / images / charts**  
- Convert to **Markdown** (fixed syntax) or JSON for better understanding

### 2. RAG Chunking
- Split document into smaller, meaningful chunks  
- Prepare for retrieval-augmented generation (RAG)

---

## 🛠️ Models & Tools

| Model / Tool       | Purpose / Notes |
|-------------------|----------------|
| MinerU / vLLM      | Local pipeline, fast inference |
| PaddleOCR-VL       | OCR, layout & text recognition |
| DeepSeek-OCR       | OCR for scanned images |
| VLM-Transformer    | Vision-language model for image + text input |
| SGLang Engine      | Streamed token parsing for real-time Markdown output |
| LayoutLMv3 / DocLayout-YOLO | Layout detection (text, images, tables, icons, formulas) |
| UniMERNet          | Formula recognition → LaTeX |
| StructEqTable      | Table recognition → LaTeX / HTML / Markdown |
| PaddleOCR          | Text extraction from images |

---

## 📝 Post-processing Steps

1. **Document Processing**
   - Language detection, page size, page number  
   - Handle encrypted files  

2. **Content Parsing**
   - Layout detection  
   - Formula detection & recognition  
   - Table detection  
   - OCR for scanned text  

3. **Content Post-processing**
   - Resolve overlapping boxes  
   - Crop table/images  
   - Remove headers & footers  
   - Determine reading order  

4. **Format Conversion**
   - Middle JSON → Markdown / Final JSON  

---

## ⚙️ Local Deployment Pipeline

- **Pipeline Types**
  - Fast pipeline → low hallucination, high speed  
  - VLM transformer → slower, compatible  
  - mlx engine → faster on Apple Silicon  
  - vllm-engine → fast, compatible with vLLM ecosystem  

- **System Requirements**
  - OS: Windows / Linux / macOS  
  - CPU inference supported  
  - GPU: Volta+ architecture, ≥6GB VRAM or Apple Silicon  
  - RAM: ≥16GB (32GB recommended)  

---

## 🌐 Using Cloud API vs Local Models

### Cloud API
1. Upload PDFs / Word files with selectable text  
2. Ensure scanned documents are clear  
3. Avoid screenshots in tables  
4. Keep one topic per file  
5. Avoid combining unrelated documents  

### Local Model
```bash
export Miner_MODEL_SOURCE=local    # Use local model
export CUDA_VISIBLE_DEVICES=3
miner-api --host 192.168.110.131 --port 50000  # Start service
```

- FastAPI can parse files locally  
- Pipeline → ML / VLM → MinerU2.5 VLM  
- Extract JSON → Convert to Markdown  

---

## 🛠️ Installation Steps (Python Environment)

1. Create Python virtual environment  
2. Install Paddle framework (dependency for PaddleOCR)  
3. Install PaddleOCR library (core OCR functionality)  
4. Download pretrained models:  
   - `PaddleOCR-VL-0.9b`  
   - `PP-DocLayoutV2`  
5. Verify installation  

---
