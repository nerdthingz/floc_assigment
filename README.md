# Medical Compliance Checker

A hybrid RAG + Regex system for analyzing medical text compliance with FDA/EMA regulations.

## Why RAG?

RAG is optimal for medical compliance checking because:
- **Dynamic Rule Updates**: New regulations can be added to the knowledge base without model retraining
- **Real-time Context**: Always references current regulatory documents
- **Cost Effective**: No need for continuous fine-tuning as rules change
- **Transparency**: Shows which specific regulations inform each decision

## Architecture

### Two-Stage Analysis
1. **Regex Pre-filtering**: Fast detection of obvious violations (guarantees, 100%, cure)
2. **RAG + LLM**: Retrieves relevant regulatory context and analyzes nuanced compliance

### Workflow
```
PDF Documents → Text Chunks → FAISS Index → Context Retrieval → LLM Analysis
```

### MedicalComplianceChecker Class
- **Vector Store**: FAISS for regulatory document similarity search
- **Embeddings**: `all-MiniLM-L6-v2` for text vectorization  
- **LLM**: Groq `deepseek-r1-distill-llama-70b` for final classification
- **Text Processing**: 500-char chunks with overlap for context preservation
- **UI Interface**: Interactive Gradio web application for real-time testing

## Customization

- **System Prompt**: Edit compliance criteria in `_setup_prompt()`
- **Regex Patterns**: Modify violation patterns in `_setup_regex_patterns()`
- **Document Base**: Add new regulatory PDFs to update knowledge base

The system prioritizes regulatory accuracy through dynamic document lookup over static model training.
