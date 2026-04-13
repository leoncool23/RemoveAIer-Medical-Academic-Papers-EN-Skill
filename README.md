# RemoveAIer-Medical-Academic-Papers-EN-Skill

> An advanced AI Skill for Claude Code, OpenClaw, and Codex designed to remove AI-generated writing patterns from English-language biomedical manuscripts and make them read like authentic researcher-authored prose.

## 🧬 Overview

Large Language Models leave distinct statistical fingerprints on medical manuscripts—overused vocabulary, inflated significance claims, and templated structures that immediately flag papers to peer reviewers and AI detection tools. 

This Skill provides a rigorous, two-pass humanization engine. It doesn't just "rewrite" text; it performs a targeted audit of 28 specific AI patterns (grounded in 2025 PubMed corpus data) and injects authentic academic voice while maintaining absolute scientific integrity.

## ✨ Key Features

- 🎙️ **Voice Calibration (Optional):** Provide a sample of your previous writing, and the Skill will mirror your sentence length, hedging habits, and punctuation style.
- 🔍 **Evidence-Based Vocabulary Detection:** Flags and replaces Tier 1, 2, and 3 AI words identified by Kobak et al. (*Science Advances*, 2025) in a 15-million abstract analysis (e.g., *delve*, *underscore*, *meticulous*, *tapestry*).
- 🧠 **Two-Pass Anti-AI Audit:** 
  - **Pass 1:** Comprehensive draft rewrite removing obvious AI syntax and promotional language.
  - **Pass 2:** A self-diagnostic audit ("What makes this obviously AI-generated?") followed by targeted surgical fixes.
- 🛡️ **Pattern Targeting:** Identifies 28 specific malicious patterns, including trailing participial phrases, false range constructions, copula avoidance (*serves as* instead of *is*), and templated limitation sections.
- ✍️ **"Soul" Injection:** Goes beyond sterilizing text. It adds authorial stance, varies sentence rhythm, and acknowledges uncertainty—transforming Wikipedia-sounding neutral text into a paper worth reading.

## 📂 Supported Document Types

- Original research articles, case reports, brief communications
- Systematic reviews, meta-analyses, narrative reviews
- Biomedical abstracts (PubMed-indexed or journal-submitted)
- Theses, fellowship applications, grant background sections
- Clinical trial protocols, ethics committee submissions

## ⚙️ How It Works

### Pass 1: Draft Rewrite
Scans the text to identify and rewrite AI patterns. This includes deflating overstated significance, converting vague attributions ("studies have shown") into properly cited claims, breaking forced triads, and removing marketing/advertorial language.

### Pass 2: Final Anti-AI Audit
The engine runs an internal diagnostic prompt on its own Pass 1 output. It checks for residual AI tells (same-length sentences, uncited claims, trailing optimism) and applies a final humanization pass before delivering the output.

## 🚀 Usage

### 1. Installation
Place the `SKILL.md` file in your AI coding assistant's skill directory:

- **Claude Code:** `.claude/skills/` or project root.
- **OpenClaw:** `.claw/skills/` or mapped `skill_path`.
- **Codex / Others:** `./skills/` or `./prompts/`.

### 2. Triggering the Skill
Use any of the following prompts to activate the skill (defaults to Pass 1):

- `humanize a medical paper`
- `reduce AI detection in a clinical manuscript`
- `remove AI writing patterns from a biomedical abstract`
- `make a research article sound less like ChatGPT`
- `lower AIGC rate in an English medical paper`
- `polish an AI-assisted draft for journal submission`

### 3. Advanced: Voice Matching
To calibrate the output to your personal writing style, include a sample in your prompt:
> *"Please humanize this manuscript. Here is a sample of my writing for voice matching: [paste sample]"*

### 4. Interaction Flow
- **Input Text + Trigger** ➡️ Receive Pass 1 Draft + Internal Audit Notes + Final Pass 2 Rewrite.
- *(Note: Unlike the Chinese versions, this English Skill is designed to output both passes and the audit log in a single structured response for maximum transparency.)*

## 🛑 Non-Negotiable Constraints

- **Zero Hallucination:** Never adds new facts, data, citations, effect sizes, or clinical recommendations.
- **Statistical Inviolability:** Preserves *exactly* all drug names/doses, lab values/units, statistical results (P values, OR, HR, 95% CI), and sample sizes.
- **Clinical Direction Lock:** Does not change the direction of efficacy, safety, or prognostic claims.
- **Academic Register Maintained:** Does not colloquialize Methods/Results. Respects standard scientific passive voice.

## 📚 Scientific Grounding

The vocabulary targeting in this Skill is directly based on:
- **Kobak et al. (2025), *Science Advances*** — Analysis of 15 million PubMed abstracts identifying 379 excess style words with LLM fingerprints.
- **Lin Z. (2024), *Nature Biomedical Engineering*** — Vocabulary shifts in biomedical writing post-ChatGPT.

## 📄 License

MIT License

---
*Disclaimer: This tool is designed to assist researchers in refining AI-assisted drafts to meet stylistic journal standards. Authors are responsible for the scientific accuracy, ethical compliance, and originality of their submitted work.*
