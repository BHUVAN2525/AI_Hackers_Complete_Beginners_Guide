# 🤖 AI & LLM Security — Complete Beginner's Roadmap

> *"The most powerful hacking tool is your curiosity and creativity. AI amplifies your abilities, but it doesn't replace your judgment, ethics, or expertise."*

A structured, hands-on guide to go from **zero → AI-powered security professional** — covering machine learning, large language models, offensive & defensive AI, and ethical hacking.

---

## 📋 Table of Contents

- [Who Is This For?](#-who-is-this-for)
- [Prerequisites](#-prerequisites)
- [Environment Setup](#-environment-setup)
- [Learning Roadmap](#-learning-roadmap-25-weeks)
- [Core Tools Arsenal](#-core-tools-arsenal)
- [OWASP Top 10 for LLMs](#-owasp-top-10-for-llm-applications)
- [Key Concepts Cheat Sheet](#-key-concepts-cheat-sheet)
- [Practice Platforms](#-practice-platforms)
- [Certifications](#-certifications-to-pursue)
- [Ethics & Legal](#️-ethics--legal-boundaries)
- [Resources](#-resources)

---

## 👤 Who Is This For?

| Background | Fit |
|---|---|
| Beginner with basic Python | ✅ Perfect starting point |
| Security student / CTF player | ✅ Great to add AI skills |
| Developer curious about AI security | ✅ Highly relevant |
| Complete non-programmer | ⚠️ Learn Python basics first |

---

## ✅ Prerequisites

### Knowledge
- Basic Python (variables, loops, functions)
- Fundamental networking concepts (TCP/IP, ports, HTTP)
- Familiarity with Linux command line

### Hardware (Minimum)
```
CPU  : 4-core processor (2018 or later)
RAM  : 8 GB (16 GB recommended)
Disk : 50 GB free space
GPU  : Optional but accelerates deep learning (NVIDIA preferred)
OS   : Kali Linux / Ubuntu 22.04 / macOS
```

### Accounts to Create (Free)
- [ ] [OpenAI Platform](https://platform.openai.com) — API access
- [ ] [Anthropic Console](https://console.anthropic.com) — Claude API
- [ ] [HuggingFace](https://huggingface.co) — Open-source models
- [ ] [GitHub](https://github.com) — Code management
- [ ] [TryHackMe](https://tryhackme.com) — Practice labs

---

## ⚙️ Environment Setup

### Step 1 — Install Python & Virtual Environment
```bash
# Update system
sudo apt update && sudo apt install python3 python3-pip git -y

# Install virtualenv
pip3 install virtualenv

# Create isolated environment
virtualenv ai_security_env
source ai_security_env/bin/activate  # Linux/macOS
# ai_security_env\Scripts\activate   # Windows
```

### Step 2 — Install Core Libraries
```bash
# Data & ML
pip install numpy pandas matplotlib seaborn scikit-learn

# Deep Learning
pip install torch torchvision torchaudio

# LLMs & NLP
pip install transformers datasets tokenizers

# API Clients
pip install openai anthropic

# Security & Web
pip install requests beautifulsoup4 scapy

# Notebooks
pip install jupyter jupyterlab
```

### Step 3 — Verify Installation
```python
import numpy, pandas, sklearn, torch, transformers

print(f"NumPy     : {numpy.__version__}")
print(f"Pandas    : {pandas.__version__}")
print(f"Sklearn   : {sklearn.__version__}")
print(f"PyTorch   : {torch.__version__}")
print(f"CUDA GPU  : {torch.cuda.is_available()}")
print("✅ All libraries loaded successfully!")
```

---

## 🗺️ Learning Roadmap (25 Weeks)

```
PHASE 1 ──► PHASE 2 ──► PHASE 3 ──► PHASE 4 ──► PHASE 5 ──► PHASE 6
Foundations   Python &     ML           Neural       LLMs        Prompt
(Wk 1-2)     Data (Wk     Basics       Networks     (Wk 9-10)   Engineering
              3-4)         (Wk 5-6)     (Wk 7-8)                 (Wk 11-12)
                                                                      │
                                                                      ▼
                                                               PHASE 7–12
                                                          Recon → Vuln Discovery
                                                          → Offensive AI → Defense
                                                          → Projects → Ethics
```

### 📅 Phase-by-Phase Breakdown

<details>
<summary><b>Phase 1 — Foundations (Weeks 1-2)</b></summary>

**Goal:** Understand AI basics and set up your lab

**Topics:**
- What is AI / ML / Deep Learning / LLMs — the hierarchy explained
- Why AI matters for security: automation, pattern recognition, evasion
- Setting up Kali Linux or Ubuntu with all required tools
- Running your first Python ML script

**Mini Project:** Install the full stack and run the verification script above.

</details>

<details>
<summary><b>Phase 2 — Python & Data Fundamentals (Weeks 3-4)</b></summary>

**Goal:** Master Python patterns used in AI/security pipelines

**Topics:**
- Lists, dicts, sets for storing scan results and vulnerability data
- NumPy arrays for feature matrices
- Pandas DataFrames for log analysis
- Feature engineering from raw network data

**Mini Project:** Parse a CSV network log, filter by port, compute stats with Pandas.

</details>

<details>
<summary><b>Phase 3 — Machine Learning Fundamentals (Weeks 5-6)</b></summary>

**Goal:** Build your first security classifier

| ML Type | How It Works | Security Use Case |
|---|---|---|
| Supervised | Learns from labeled data | Malware classification |
| Unsupervised | Finds hidden patterns | Anomaly detection |
| Reinforcement | Learns via reward/penalty | Automated pentesting |
| Semi-supervised | Mix of labeled & unlabeled | Threat intel |

**Key Concept — Model Metrics for Security:**

```
Accuracy   → Only use with balanced datasets
Precision  → Minimize false alarms  
Recall     → Minimize MISSED attacks ← Most critical in IDS
F1-Score   → Balance of Precision & Recall
AUC-ROC    → Threshold-independent evaluation
```

> ⚠️ **Security Focus:** High Recall > High Precision in intrusion detection.
> Missing a real attack is far more dangerous than a false alarm.

**Mini Project:** Train a Random Forest on the NSL-KDD dataset.

</details>

<details>
<summary><b>Phase 4 — Neural Networks & Deep Learning (Weeks 7-8)</b></summary>

**Goal:** Build neural networks for security tasks with PyTorch

**Architecture Layers:**
- **Input Layer** → Raw features (packet size, duration, port)
- **Hidden Layers** → Weighted transformations + activation functions
- **Output Layer** → Attack probability score

**Activation Functions Quick Reference:**

| Function | Range | Use For |
|---|---|---|
| ReLU | [0, ∞) | Hidden layers (default) |
| Sigmoid | (0, 1) | Binary classification output |
| Softmax | (0,1) summing to 1 | Multi-class output |
| Tanh | (-1, 1) | NLP hidden layers |
| LeakyReLU | (-∞, ∞) | Prevent dying ReLU |

**Mini Project:** Build a PyTorch `IntrusionDetector` neural network and train it on network traffic data.

</details>

<details>
<summary><b>Phase 5 — Large Language Models (Weeks 9-10)</b></summary>

**Goal:** Master LLMs for security research

**How Transformers Work (2017 Architecture):**
- **Self-Attention** → Weighs word importance relative to context
- **Multi-Head Attention** → Parallel attention operations
- **Positional Encoding** → Injects word position information
- **Feed-Forward Networks** → Non-linear transformations
- **Layer Normalization** → Stabilizes training

**Practical LLM Usage:**
```python
import anthropic

client = anthropic.Anthropic(api_key="your-key")

response = client.messages.create(
    model="claude-sonnet-4-20250514",
    max_tokens=1024,
    messages=[{
        "role": "user",
        "content": "Analyze this code for SQL injection vulnerabilities:\n<code here>"
    }]
)
print(response.content[0].text)
```

**Mini Project:** Build a code vulnerability scanner powered by an LLM API.

</details>

<details>
<summary><b>Phase 6 — Prompt Engineering for Hackers (Weeks 11-12)</b></summary>

**Goal:** Craft effective prompts for security tasks

**Core Techniques:**

| Technique | Description | Best For |
|---|---|---|
| Zero-Shot | Ask directly, no examples | Quick analysis |
| Few-Shot | Provide 2-5 examples | Structured output |
| Chain-of-Thought | "Think step by step" | Complex reasoning |
| Role Prompting | Assign expert persona | Detailed technical output |
| Structured Output | Request JSON/XML | Programmatic use |

**Prompt Injection — Types to Know:**
- **Direct Injection** → User overwrites system prompt
- **Indirect Injection** → Malicious instructions in external content
- **Stored Injection** → Saved to DB, triggers later
- **Multimodal Injection** → Hidden in images or documents

**Defenses:**
- Separate user input from system instructions
- Validate & sanitize all inputs
- Use minimal LLM permissions (least privilege)
- Log all LLM inputs and outputs

</details>

<details>
<summary><b>Phases 7-10 — Applied AI Security (Weeks 13-20)</b></summary>

| Phase | Topic | Key Skills |
|---|---|---|
| 7 | AI-Powered Recon | OSINT automation, DNS intel, subdomain discovery |
| 8 | Vulnerability Discovery | AI code auditing, smart fuzzing, bug finding |
| 9 | Offensive AI Techniques | Adversarial ML, FGSM attacks, evasion |
| 10 | Defensive AI & Detection | Anomaly detection, AI-SIEM, SOAR automation |

</details>

<details>
<summary><b>Phases 11-12 — Projects & Ethics (Weeks 21-25)</b></summary>

**Capstone Projects:**
1. **AI Recon Bot** — Automate subdomain discovery + AI-powered attack surface analysis
2. **AI Password Cracker Assistant** — Generate targeted wordlists with OSINT + LLM
3. **AI Code Auditor** — Scan files for vulnerabilities and output structured JSON findings
4. **Network Anomaly Detector** — IsolationForest-based real-time traffic analysis

</details>

---

## 🛠️ Core Tools Arsenal

### ML & AI Libraries
| Tool | Purpose | Install |
|---|---|---|
| PyTorch | Deep learning framework | `pip install torch` |
| Scikit-learn | Classical ML algorithms | `pip install scikit-learn` |
| HuggingFace Transformers | LLM interaction | `pip install transformers` |
| Pandas / NumPy | Data manipulation | `pip install pandas numpy` |

### LLM API Clients
| Tool | Purpose | Install |
|---|---|---|
| `openai` | GPT-4 / GPT-4o access | `pip install openai` |
| `anthropic` | Claude API access | `pip install anthropic` |
| `ollama` | Run local LLMs | [ollama.ai](https://ollama.ai) |

### Offensive AI Tools (Research / Authorized Use Only)
| Tool | Purpose | Category |
|---|---|---|
| PassGAN | GAN-based password generation | Password Cracking |
| DeepExploit | Automated pentesting via deep RL | Exploitation |
| Ghauri | SQL injection with ML payload mutation | Web App Testing |
| Neural Fuzzer | LSTM-based intelligent fuzzing | Fuzzing |

### Defensive AI Tools
| Tool | Purpose | Category |
|---|---|---|
| Darktrace | Unsupervised ML threat detection | NDR |
| Vectra AI | AI-powered network detection & response | NDR |
| Cylance (BlackBerry) | ML-based endpoint protection | EDR |
| Elastic SIEM + ML | AI-enhanced log analysis | SIEM |
| Microsoft Sentinel | Cloud-native AI SIEM | SIEM |
| Recorded Future | AI-powered threat intelligence | Threat Intel |

### LLM Security Research Tools
| Tool | Purpose | Install |
|---|---|---|
| Garak | LLM vulnerability scanner | `pip install garak` |
| LLMFuzzer | Automated jailbreak fuzzing | GitHub |
| TextAttack | NLP adversarial attacks | `pip install textattack` |
| CleverHans | Adversarial ML examples | `pip install cleverhans` |

---

## 🔐 OWASP Top 10 for LLM Applications

| ID | Vulnerability | Quick Description |
|---|---|---|
| LLM01 | **Prompt Injection** | Attacker hijacks LLM behavior via crafted inputs |
| LLM02 | **Insecure Output Handling** | LLM output not validated before downstream use |
| LLM03 | **Training Data Poisoning** | Backdoors introduced via manipulated training data |
| LLM04 | **Model Denial of Service** | Resource exhaustion through complex prompts |
| LLM05 | **Supply Chain Vulnerabilities** | Compromised models, plugins, or data sources |
| LLM06 | **Sensitive Information Disclosure** | LLM leaks PII or confidential training data |
| LLM07 | **Insecure Plugin Design** | Plugins without proper access controls |
| LLM08 | **Excessive Agency** | LLM given too much autonomous power to act |
| LLM09 | **Overreliance** | Trusting LLM output without human verification |
| LLM10 | **Model Theft** | Unauthorized extraction of proprietary models |

---

## 📖 Key Concepts Cheat Sheet

### ML Algorithms for Security

| Algorithm | Type | Best For | Complexity |
|---|---|---|---|
| Random Forest | Supervised | Malware classification, IDS | Low |
| Gradient Boosting | Supervised | Fraud detection | Medium |
| SVM | Supervised | Binary classification | Low-Med |
| K-Means | Unsupervised | Network clustering | Low |
| DBSCAN | Unsupervised | Anomaly detection, botnet C2 | Low |
| Isolation Forest | Unsupervised | Outlier detection | Low |
| Autoencoders | Unsupervised | Network anomaly, malware | High |
| LSTM/GRU | Supervised | Log analysis, sequence attacks | High |
| Transformer | Both | NLP security, code analysis | Very High |
| GAN | Generative | Adversarial examples | Very High |

### Essential Python One-Liners
```python
# Encode / decode Base64
import base64; base64.b64encode(b'payload').decode()

# SHA-256 hash
import hashlib; hashlib.sha256(b'password').hexdigest()

# Secure random token
import secrets; secrets.token_hex(32)

# Extract emails from text
import re; re.findall(r'[\w.+-]+@[\w-]+\.[\w.]+', text)

# Check if port is open
import socket; s = socket.socket(); s.connect_ex(('target.com', 80))

# Cosine similarity between vectors
from numpy import dot; from numpy.linalg import norm
cos_sim = lambda a, b: dot(a, b) / (norm(a) * norm(b))
```

### Cloud AI Security — Critical Misconfigurations

| Risk | Severity |
|---|---|
| Open S3 Buckets (training data exposed) | 🔴 CRITICAL |
| Public model inference endpoints (no auth) | 🔴 CRITICAL |
| Overprivileged IAM for ML services | 🟠 HIGH |
| Unencrypted model artifacts at rest | 🟠 HIGH |
| Jupyter notebooks exposed without auth | 🟠 HIGH |
| Training Data SSRF | 🟠 HIGH |
| No VPC isolation for ML infrastructure | 🟡 MEDIUM |

> ⚠️ **PyTorch Pickle Warning:** Never load untrusted `.pth` model files.
> Use `torch.load('model.pth', weights_only=True)` for safe loading.

---

## 🎯 Practice Platforms

### CTF & Labs
| Platform | Focus | Cost |
|---|---|---|
| [TryHackMe](https://tryhackme.com) | Guided cybersecurity labs | Free / Paid |
| [HackTheBox](https://hackthebox.com) | Penetration testing challenges | Free / Paid |
| [PortSwigger Web Academy](https://portswigger.net/web-security) | Web security | Free |
| [PicoCTF](https://picoctf.org) | Beginner CTF challenges | Free |
| [CTFtime.org](https://ctftime.org) | CTF event calendar | Free |
| [Google CTF](https://capturetheflag.withgoogle.com) | Advanced challenges | Free |

### AI & ML Learning
| Platform | Focus | Cost |
|---|---|---|
| [fast.ai](https://fast.ai) | Deep learning course | Free |
| [Coursera ML Specialization](https://coursera.org) | ML fundamentals | Free audit |
| [HuggingFace Learn](https://huggingface.co/learn) | LLMs & NLP | Free |

### CTF Tips — Using AI in Competitions
- Feed challenge files to an LLM for initial pattern analysis
- Use AI to decode unknown encodings and formats
- Ask LLMs to explain assembly code and reverse engineering puzzles
- Use AI for crypto challenge pattern recognition

---

## 🏅 Certifications to Pursue

| Certification | Focus Area | Timeline |
|---|---|---|
| **OSCP** — Offensive Security Certified Professional | Penetration Testing | 3-6 months prep |
| **CEH** — Certified Ethical Hacker | AI-powered hacking | 2-4 months |
| **GCIH/GCIA** — GIAC Incident Handler | Defensive Security | 3-6 months |
| **AWS/Azure/GCP ML** — Cloud ML certifications | AI Deployment | 2-3 months |
| **MLOps Professional** | Securing AI Pipelines | 3-6 months |

### Advanced Career Paths

| Path | Focus Area | Timeline |
|---|---|---|
| AI Red Teamer | Offensive AI, LLM security, adversarial ML | 3-6 months |
| AI Blue Teamer | Defensive AI, anomaly detection, SIEM/SOAR | 3-6 months |
| ML Engineer | Deep learning, model development, research | 6-12 months |
| AI Product Security | Securing AI systems, SDLC, compliance | 6-12 months |
| AI Security Researcher | Novel vulnerabilities, publications, CVEs | 12-24 months |

---

## ⚖️ Ethics & Legal Boundaries

### Key Laws You Must Know
- 🇺🇸 **Computer Fraud and Abuse Act (CFAA)** — USA
- 🇬🇧 **Computer Misuse Act 1990** — UK
- 🇪🇺 **EU Directive 2013/40/EU** — Europe
- 🇮🇳 **IT Act 2000** — India
- 🇦🇺 **Cybercrime Act** — Australia

### The Rule of Written Authorization
> Before testing **ANY** system, you must have **explicit written authorization** specifying:
> - Exact IP ranges and domains in scope
> - Types of testing permitted (scanning, exploitation, social engineering)
> - Testing window (dates and times)
> - Emergency contact procedures
> - Data handling and reporting requirements

### Responsible Disclosure Process
```
1. Document  → Reproduce the vulnerability with full steps
2. Contact   → Find security.txt / HackerOne / Bugcrowd
3. Report    → Send professional report privately
4. Timeline  → Give vendor 90 days to fix
5. Follow Up → Check in at 30 / 60 / 90 days
6. Coordinate→ Collaborate on patch timeline + CVE
7. Publish   → Technical writeup after patch ships
```

### AI Ethics in Security
- AI-generated exploits lower the barrier for less-skilled threat actors
- Automated AI attacks can cause unintended collateral damage at scale
- AI surveillance tools raise serious privacy concerns
- Bias in security models can produce discriminatory outcomes
- Always consider the **dual-use nature** of every technique you develop

---

## 📚 Resources

### Communities & Conferences
- [DEF CON AI Village](https://aivillage.org)
- [OWASP AI Security Project](https://owasp.org/www-project-ai-security-and-privacy-guide/)
- [Black Hat AI Summit](https://blackhat.com)
- Reddit: [r/netsec](https://reddit.com/r/netsec) + [r/MachineLearning](https://reddit.com/r/MachineLearning)

### AI Security Tool Repositories
- [Adversarial Robustness Toolbox — IBM](https://github.com/Trusted-AI/adversarial-robustness-toolbox)
- [CleverHans — Adversarial Examples](https://github.com/cleverhans-lab/cleverhans)
- [TextAttack — NLP Attacks](https://github.com/QData/TextAttack)
- [Garak — LLM Vulnerability Scanner](https://github.com/leondz/garak)

### Essential Reading
- [OWASP LLM Top 10](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
- [MITRE ATLAS — AI Threat Matrix](https://atlas.mitre.org)
- [NIST AI Risk Management Framework](https://www.nist.gov/system/files/documents/2023/01/26/AI RMF 1.0.pdf)

---

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/add-new-section`)
3. Commit your changes with clear messages
4. Open a Pull Request

---

## 📄 License

This guide is for **educational purposes only**. All techniques must be used legally, ethically, and only on systems you own or have explicit written permission to test.

---

<div align="center">

**Made with ❤️ by Bhuvan**

*Keep learning. Keep hacking (legally).*

⭐ Star this repo if it helped you!

</div>
