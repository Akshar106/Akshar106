<div align="center">
  <img src="assets/banner.svg" alt="Akshar Patel — building LLM systems that survive real users, and the evals that keep them honest" width="100%"/>
</div>

<p align="center">
  <a href="https://www.linkedin.com/in/akshar-patel11/"><img src="https://img.shields.io/badge/LinkedIn-Akshar_Patel-0A66C2?style=for-the-badge" alt="LinkedIn"/></a>
  <a href="mailto:patelakshar1104@gmail.com"><img src="https://img.shields.io/badge/Email-patelakshar1104%40gmail.com-EA4335?style=for-the-badge" alt="Email"/></a>
  <img src="https://img.shields.io/badge/Open_to-AI%2FML%2FDS_·_2027-34D399?style=for-the-badge" alt="Open to AI/ML/DS roles, 2027"/>
</p>

MS Data Science @ **Indiana University Bloomington** (4.0 GPA, May 2027). Currently: **AI Engineering Intern @ Hitachi Global Air Power** and **ML Engineer (part-time) @ Indiana University**. I build multi-agent and RAG systems for real users, then build the evaluation suites that tell me whether to trust them.

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch"/>
  <img src="https://img.shields.io/badge/🤗_Hugging_Face-FFD21E?style=for-the-badge&logoColor=black" alt="Hugging Face"/>
  <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white" alt="LangChain"/>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI"/>
  <img src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white" alt="Flask"/>
  <img src="https://img.shields.io/badge/FAISS-0467DF?style=for-the-badge" alt="FAISS"/>
  <img src="https://img.shields.io/badge/Pinecone-121212?style=for-the-badge" alt="Pinecone"/>
  <img src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB"/>
  <img src="https://img.shields.io/badge/Snowflake-29B5E8?style=for-the-badge&logo=snowflake&logoColor=white" alt="Snowflake"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" alt="GitHub Actions"/>
  <img src="https://img.shields.io/badge/AWS-FF9900?style=for-the-badge" alt="AWS"/>
  <img src="https://img.shields.io/badge/Azure-0078D4?style=for-the-badge" alt="Azure"/>
</p>

## 🚀 Flagship systems

<table>
<tr>
<td width="50%" valign="top">

### 🎓 [EduPilot](https://github.com/Akshar106/EduPilot-A-Multi-Agent-Source-Grounded-Educational-AI-System-for-Adaptive-and-Cross-Domain-Learning)

**Multi-agent, source-grounded RAG** for graduate coursework. 7-stage pipeline with hybrid retrieval (Pinecone + BM25, fused via Reciprocal Rank Fusion) and LLM-as-judge verification. Every answer cites the exact lecture and page.

`FastAPI` `Pinecone` `BM25 + RRF` `Groq Llama 3.3 70B`

📊 **50-case, 8-metric eval suite** — faithfulness, citation accuracy, adversarial hallucination tests
⚡ **Finding: a 3.7x citation-accuracy gap** between 70B and 8B models on identical inputs

Built with [Khushi Shah](https://github.com/shahkhushi28k)

</td>
<td width="50%" valign="top">

### 🏥 [IntelliSphere](https://github.com/Akshar106/IntelliSphere-Domain-Specific-RAG-Conversational-AI-)

**Domain-specific RAG, deployed for real.** Healthcare + legal document QA with MongoDB-backed multi-session conversation memory and metadata-tagged FAISS retrieval.

`Flask` `LangChain` `FAISS` `Gemini` `MongoDB`

🚢 **Full CI/CD**: Docker → GitHub Actions → Amazon ECR → auto-deploy to EC2 (self-hosted runner)
☁️ FAISS indexes synced from **S3** at container startup, served by gunicorn

</td>
</tr>
</table>

### How EduPilot thinks

```mermaid
flowchart LR
    Q([query]) --> R{router}
    R --> S[splitter]
    S --> H["hybrid retrieval<br/>Pinecone + BM25 → RRF"]
    H --> RR[reranker]
    RR --> G[domain agents]
    G --> SY[synthesizer]
    SY --> V{{"LLM-as-judge<br/>verifier"}}
    V -->|cited answer| A([answer + sources])
```

## 🔒 Shipped behind private walls

The work I can't open-source, with the receipts I can share:

| System | Stack | Receipt |
|---|---|---|
| Query router for IU's **One.IU** portal | embeddings + fuzzy + LLM tiebreaker | **98.6% accuracy** across a closed catalog of 33 applications |
| Live-data tool API for IU's **ChatAIU** assistant | Azure App Service, REST | **Adopted by the ChatAIU team** as an agent tool |
| **LLM autograding** platform on Canvas LMS | Flask, OAuth2, schema-validated outputs | Every grade passes a **faculty review-and-override queue** |
| Enterprise **multi-agent assistant** @ Hitachi | Copilot Studio, MCP, Snowflake Cortex | **60 users across 5 departments** on Teams |

<details>
<summary><b>🔬 The 3.7x finding, in 60 seconds</b></summary>
<br/>

Same pipeline. Same prompts. Same retrieved context. The only variable: the generator model.

- **Llama 3.3 70B** — citation accuracy **1.00**
- **Llama 3.1 8B** — citation accuracy **0.27**

Measured across a shared query set inside a 50-case, 8-metric evaluation suite (faithfulness, citation accuracy, retrieval hit rate, quality, coverage, latency, intent and domain accuracy). The takeaway that changed how I build: **model choice alone decided whether citations could be trusted** — retrieval quality couldn't compensate. This is why every system I ship now includes an eval suite before it includes a feature roadmap.

</details>

> I try to know the denominator behind every number I claim.

---

<p align="center">
  <a href="mailto:patelakshar1104@gmail.com">📫 patelakshar1104@gmail.com</a> · <a href="https://www.linkedin.com/in/akshar-patel11/">💼 LinkedIn</a> · Open to full-time AI/ML/Data Science roles starting 2027
</p>
