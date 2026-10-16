<h1 align="center">Lowaltitudeflight</h1>

<p align="center">
  <b>I build, benchmark and hand over self-hosted LLM systems</b><br>
  inference performance · multi-GPU tuning decisions · private-deployment delivery
</p>

<p align="center">
  <a href="https://github.com/Lowaltitudeflight?tab=repositories"><img src="https://img.shields.io/badge/repositories-4-blue?style=flat" alt="Repositories"></a>
  <a href="https://github.com/Lowaltitudeflight?tab=repositories"><img src="https://img.shields.io/badge/focus-LLM%20inference%20%26%20evaluation-orange?style=flat" alt="Focus"></a>
  <a href="https://gitee.com/wang-guangshuooo"><img src="https://img.shields.io/badge/Gitee-China%20mirrors-C71D23?style=flat&logo=gitee&logoColor=white" alt="Gitee"></a>
</p>

---

The work here comes out of real delivery jobs. The recurring question is not *"does it run?"* but **"can I prove it runs well, and can I hand it over to a customer?"**

## What I work on

| Area | In practice |
| --- | --- |
| **LLM inference & serving** | Benchmarking vLLM / Ollama across quantisation levels; TTFT, TPOT and tail-latency measurement; capacity planning from concurrency sweeps |
| **Multi-GPU tuning** | Parallelism, communication and quantisation choices on machines **without NVLink**, where PCIe topology bounds everything |
| **Private deployment delivery** | Environment survey → sizing → deployment → benchmarking → acceptance → troubleshooting, with templates and checklists |
| **RAG & agents** | Hybrid BM25 + vector retrieval with RRF fusion, tool-calling agents over locally hosted models, and evaluation harnesses that refuse to report what the data cannot support |

## Featured projects

| Project | What it is |
| --- | --- |
| **[llm-inference-bench](https://github.com/Lowaltitudeflight/llm-inference-bench)** | Cross-engine, cross-quantisation benchmarking for self-hosted LLMs. Concurrency sweeps, TTFT / TPOT / P99, VRAM curves, Prometheus + Grafana, and self-contained HTML reports. Benchmarked on real hardware: **30.8 tokens/s peak on an 8 GB RTX 4060 Laptop, saturating at concurrency 2**. |
| **[local-llm-tuning-guide](https://github.com/Lowaltitudeflight/local-llm-tuning-guide)** | Configuration decisions for multi-GPU LLM serving **without NVLink**: when replicas beat tensor parallelism, why a longer speculative draft can be slower, and how PCIe topology bounds every parallelism choice. Every conclusion carries an evidence grade (measured, derivable, or open) — an empty cell is preferred to an invented number. |
| **[llm-private-deploy-handbook](https://github.com/Lowaltitudeflight/llm-private-deploy-handbook)** | An 8-chapter private-deployment delivery handbook: environment survey → sizing → deployment → benchmarking → acceptance → troubleshooting. Includes VRAM estimation formulas with worked examples and a dependency-free estimator script. |

> Every repository is **English-first**: the English README is the front page, with the Chinese version one click away at the top of the file.

Earlier projects — a RAG QA system, an AIOps agent, a customer-service agent, an e-commerce data warehouse and a C/C++ data-structures collection — live on **[Gitee](https://gitee.com/wang-guangshuooo)** in Chinese.

## Tools I reach for

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![vLLM](https://img.shields.io/badge/vLLM-FF6F00?style=flat)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=flat&logo=ollama&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat&logo=langchain&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-0467DF?style=flat)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat&logo=grafana&logoColor=white)
![NVIDIA](https://img.shields.io/badge/NVIDIA-76B900?style=flat&logo=nvidia&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)

## What I keep in mind when building

These show up repeatedly across the work here, because each of them cost real time to learn:

- **A metric you have not validated is worse than no metric.** In one RAG evaluation, a single `==` comparison against a full path pinned Hit@K at zero for *every* configuration — the numbers looked like "poor retrieval quality", but the metric itself was broken.
- **Agree on definitions before comparing numbers.** TTFT measured at HTTP 200 and TTFT measured at the first content chunk are not the same quantity, and results from the two definitions cannot be placed in one table.
- **Report only what the data supports.** Benchmarking one configuration per point hides the saturation knee; averaging quoted and paraphrased questions hides both.
- **Deliverables have to survive the environment they land in.** Reports are self-contained HTML because customer networks are frequently isolated, and a report that pulls from a CDN opens to a blank page.

---

## Writing

I also write about these systems in Chinese: **[低空飞行357 on CSDN](https://blog.csdn.net/2302_79954719)** — notes on LLM inference benchmarking, private-deployment delivery, and multi-GPU tuning without NVLink.

---

<sub>Repositories are maintained in both languages: English README first, Chinese README alongside. Chinese-only projects stay on <a href="https://gitee.com/wang-guangshuooo">Gitee</a>.</sub>
