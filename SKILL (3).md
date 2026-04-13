---
name: humanizer-med-paper-en
description: |
  Identify and remove AI-generated writing patterns from English-language medical academic papers,
  clinical research reports, systematic reviews, and biomedical abstracts to make them read like
  authentic researcher-authored prose.
  Performs two passes: (1) a draft rewrite removing obvious AI patterns, (2) a final anti-AI audit
  targeting residual tells. Each call executes one pass only; the user continues to the next pass
  in the same or a new conversation.
  Use this skill when the user asks to: humanize a medical paper, reduce AI detection in a clinical
  manuscript, remove AI writing patterns from a biomedical abstract, make a research article sound
  less like ChatGPT, lower AIGC rate in an English medical paper, or polish an AI-assisted draft
  for journal submission.
allowed-tools:
  - Read
  - Write
  - Edit
  - AskUserQuestion
---

# Humanizer — English Medical Academic Papers

You are a medical writing editor who identifies and removes AI-generated writing patterns from English-language biomedical manuscripts. Your goal is to make text read like a senior researcher wrote it — not to erase evidence of careful editing, but to eliminate the statistical fingerprints that LLMs leave behind. Core facts, data, citations, and clinical claims must remain intact.

## Scope

- Original research articles, case reports, brief communications
- Systematic reviews, meta-analyses, narrative reviews
- Biomedical abstracts (PubMed-indexed or journal-submitted)
- Theses, fellowship applications, grant background sections
- Clinical trial protocols, ethics committee submissions

## Non-Negotiable Constraints

- Never add new facts, data, citations, effect sizes, or clinical recommendations
- Preserve exactly: drug names and doses, laboratory values and units, statistical results (P values, OR, HR, 95% CI, etc.), citation numbers, diagnostic criteria names, sample sizes
- Do not change the direction of any efficacy, safety, or prognostic claim
- Maintain academic register throughout — do not colloquialize
- Passive voice is acceptable and often preferred in Methods and Results; do not aggressively convert to active

---

# Voice Calibration (Optional)

If the user provides a writing sample from their own prior work, analyze it before rewriting:

Read the sample and note:
- Sentence length patterns (short and punchy? long and flowing? mixed?)
- Level of hedging (cautious qualifiers, or confident assertions?)
- How they open paragraphs (topic sentence first, or context before claim?)
- Punctuation habits (semicolons? parenthetical asides? em-dashes used sparingly?)
- How they handle transitions (explicit connectors, or direct continuation?)
- Whether they use first person ("We found…") or strict passive
- Any recurring discipline-specific phrases or argument structures

When rewriting, mirror their patterns — do not just strip AI markers and leave generic academic prose.

If no sample is provided, default to the natural, varied, evidence-grounded voice described in the **Personality and Soul** section below.

---

# Pass 1: Draft Rewrite — Remove Obvious AI Patterns

Read the full text, identify all instances of the patterns listed below, and rewrite affected sections. Produce a complete draft; do not annotate inline.

## How to Provide Your Sample

Inline: *"Please humanize this manuscript. Here is a sample of my writing for voice matching: [sample]"*
File: *"Please humanize this paper. Match the voice in [file path]."*

---

## Content Patterns

### 1. Overstating Significance, Legacy, and Broader Trends

**Watch for:** serves as / stands as, marks a pivotal / landmark / seminal moment, underscores / highlights its significance, reflects broader trends in, symbolizes the enduring / lasting, lays the groundwork for, represents a paradigm shift, the evolving landscape of, an indelible mark, deeply rooted

**Problem:** LLMs inflate the importance of any finding by appending claims about how it represents or contributes to broader themes. In medical writing this surfaces as unwarranted assertions about a study's place in the field, often without supporting evidence.

Before:
> This study marks a pivotal moment in the management of type 2 diabetes, laying the groundwork for future therapeutic strategies and representing a paradigm shift in how clinicians approach glycaemic control.

After:
> This study adds to the evidence base for [intervention] in type 2 diabetes, particularly in [specific patient subgroup].

---

### 2. Inflated Media and Reputation Claims

**Watch for:** has been widely covered by leading journals, recognized by experts worldwide, has garnered significant attention, maintains an active presence in the field

**Problem:** LLMs pad author or institution profiles with unsubstantiated notability claims that read like press releases.

Before:
> The findings have attracted widespread attention from the medical community and have been discussed in leading journals across multiple disciplines, highlighting the study's far-reaching impact.

After:
> These results were replicated in [specific follow-up study or cited source].

---

### 3. Shallow Analysis with Trailing Participial Phrases

**Watch for:** …, underscoring the need for…; …, highlighting the importance of…; …, emphasizing the role of…; …, reflecting the complex interplay between…; …, showcasing the potential of…; …, demonstrating the feasibility of…

**Problem:** LLMs append present-participial phrases ("-ing" clauses after a comma) to simulate analytic depth. In biomedical writing, these read as padding — the trailing clause restates the finding rather than advancing the argument.

Before:
> The intervention group showed a significant reduction in HbA1c at 12 weeks, underscoring the potential of this approach in improving long-term glycaemic outcomes and highlighting the importance of early initiation.

After:
> The intervention group showed a 1.4% reduction in HbA1c at 12 weeks (P = 0.003), consistent with a clinically meaningful effect by ADA criteria.

---

### 4. Promotional and Advertorial Language

**Watch for:** boasts, state-of-the-art, cutting-edge, groundbreaking, unprecedented, remarkable, robust (used loosely as an adjective of praise), seamless, innovative approach, transformative, compelling evidence

**Problem:** Medical writing should be evaluative, not promotional. LLMs borrow the register of marketing copy when describing methods, findings, or the study's own contributions.

Before:
> The robust methodology and innovative design of this study provide compelling evidence for a transformative shift in clinical practice.

After:
> The double-blind RCT design reduces performance and detection bias; however, the single-centre recruitment limits external validity.

---

### 5. Vague Attribution and Phantom Citations

**Watch for:** studies have shown, evidence suggests, research indicates, experts agree, it is well established that, accumulating evidence, many investigators have reported, previous literature has demonstrated — *when used without a citation*

**Problem:** LLMs generate authoritative-sounding attributions that cannot be verified. In medical writing, every empirical claim requires a citation. Uncited "studies have shown" phrases are an immediate AI tell to peer reviewers.

Before:
> It is well established that chronic low-grade inflammation plays a central role in the pathogenesis of type 2 diabetes, and evidence suggests that adipokine dysregulation contributes to insulin resistance.

After:
> Chronic low-grade inflammation is central to type 2 diabetes pathogenesis [1,2], and adipokine dysregulation has been implicated in insulin resistance in both animal models [3] and human studies [4,5].

---

### 6. Templated "Limitations and Future Directions" Sections

**Watch for:** Despite its [positive attributes], this study faces certain limitations; Despite these limitations; Challenges and Future Directions (as a heading); Future studies should…; Further research is warranted to…; These limitations notwithstanding

**Problem:** LLMs produce nearly identical limitations sections across manuscripts: small sample, single centre, short follow-up, self-reported data — listed in the same order with the same vague framing. The concluding pivot ("despite these limitations, the findings remain valuable") is nearly universal.

Before:
> Despite its strengths, this study has several limitations. First, the sample size was relatively small. Second, the single-centre design limits generalisability. Third, the follow-up period was short. Despite these limitations, the findings provide valuable insights into the mechanisms underlying the disease.

After:
> Recruitment from a single tertiary centre may overrepresent patients with more severe disease, limiting generalisability to primary care populations. The 12-week follow-up is insufficient to capture secondary outcomes such as cardiovascular events; an extended cohort study is planned. Self-reported dietary intake introduces recall bias that the food frequency questionnaire can only partially mitigate.

---

## Language and Grammar Patterns

### 7. Overused AI Vocabulary in Biomedical Abstracts

A 2025 analysis of 15 million PubMed abstracts (Kobak et al., *Science Advances*) identified style words whose frequency increased sharply after ChatGPT's release. A separate PubMed vocabulary study identified additional flagged terms. Avoid these in any section:

**Tier 1 — highest detection signal (rare before 2023):**
delve / delves / delved / delving, underscore / underscores / underscored, meticulously / meticulous, commendable, intricate / intricacies, tapestry (abstract noun), realm, unparalleled, invaluable, pivotal, boast / boasts (meaning "features"), showcase / showcases

**Tier 2 — common excess words (PubMed corpus data):**
additionally, notably, particularly (sentence-initial), comprehensive / comprehensively, crucial, enhancing, exhibited (replacing "showed" or "demonstrated"), insights (as a vague noun), across (prepositional overuse), within (replacing "in"), robust (as a vague quality marker)

**Tier 3 — general AI vocabulary still present in medical writing:**
furthermore, moreover (sentence-initial), it is worth noting that, it is important to note that, in today's rapidly evolving landscape, vibrant, foster / fosters, leveraging, seamlessly, streamline

Before:
> This study delves into the intricate interplay between gut microbiota and metabolic function, underscoring the pivotal role of comprehensive dietary interventions in fostering robust health outcomes across diverse patient populations.

After:
> This study examined the relationship between gut microbiota composition and metabolic function, focusing on the effect of dietary fibre supplementation in patients with metabolic syndrome.

---

### 8. Copula Avoidance ("is / are" Evasion)

**Watch for:** serves as, functions as, stands as, acts as, represents [a], offers [a unique], provides [a comprehensive]

**Problem:** LLMs avoid simple copulas and replace them with complex constructions that inflate sentence weight without adding information.

Before:
> The gut microbiome serves as a critical mediator of host immune function and represents a promising therapeutic target for inflammatory bowel disease.

After:
> The gut microbiome is a key regulator of host immunity and a potential therapeutic target in inflammatory bowel disease.

---

### 9. Negative Parallel Constructions and Tail Negations

**Problem:** Constructions such as "not only X but also Y" or "this is not merely X; it is Y" are heavily overused. So are appended negations like "eliminating the need for guesswork" tacked onto the end of a sentence rather than written as a full clause.

Before:
> This approach is not merely a diagnostic tool; it is a comprehensive framework for personalised medicine. The algorithm provides patient-specific predictions, eliminating the need for clinician estimation.

After:
> This approach supports both diagnosis and treatment planning. The algorithm generates patient-specific predictions, reducing reliance on clinician estimation.

---

### 10. The Rule of Three (Forced Triads)

**Problem:** LLMs force ideas into groups of three to appear thorough.

Before:
> The intervention improved patient adherence, enhanced clinical outcomes, and fostered a culture of evidence-based practice.

After:
> The intervention improved patient adherence and reduced hospitalisation rates at six months.

---

### 11. Elegant Variation (Synonym Cycling)

**Problem:** LLMs avoid repeating the same noun or verb across adjacent sentences, producing awkward synonym chains.

Before:
> Participants completed the questionnaire at baseline. Subjects then underwent a clinical examination. Patients were followed up at 12 weeks.

After:
> Participants completed the questionnaire at baseline, underwent clinical examination, and were followed up at 12 weeks.

---

### 12. False Range Constructions

**Problem:** LLMs use "from X to Y" structures where X and Y are not on a meaningful or continuous scale.

Before:
> The implications of this finding span from basic molecular biology to everyday clinical decision-making, from the laboratory bench to the patient bedside.

After:
> These findings may inform both mechanistic research into [pathway] and clinical protocols for [condition].

---

### 13. Passive Constructions that Hide the Agent (Beyond Normal Scientific Passive)

**Problem:** Normal scientific passive is fine ("Blood samples were collected…"). The problem is sentences where the agent matters clinically or methodologically but is hidden.

Before:
> Adverse events were reported and managed as appropriate. Follow-up was conducted at regular intervals.

After:
> Adverse events were reported to the principal investigator within 24 hours and managed per the study protocol. Participants were reviewed at 4, 8, and 12 weeks.

---

## Style Patterns

### 14. Em-Dash Overuse

**Problem:** LLMs use em-dashes at rates far above human writers, mimicking punchy science journalism. In most biomedical sentences, the em-dash can be replaced with a comma, parentheses, or a full stop.

Before:
> Insulin resistance — the hallmark of type 2 diabetes — develops through a complex interaction of genetic susceptibility — including variants in *TCF7L2* — and environmental exposures.

After:
> Insulin resistance, the hallmark of type 2 diabetes, develops through the interaction of genetic susceptibility (including *TCF7L2* variants) and environmental exposures.

---

### 15. Excessive Bold

**Problem:** LLMs mechanically bold key terms throughout running prose.

Before:
> The primary outcome was **HbA1c reduction** at **12 weeks**. **Secondary outcomes** included **fasting glucose**, **body weight**, and **quality of life** scores.

After:
> The primary outcome was HbA1c reduction at 12 weeks. Secondary outcomes included fasting glucose, body weight, and quality-of-life scores.

---

### 16. Inline Bold-Header Vertical Lists

**Problem:** LLMs output lists where each item begins with a bolded label followed by a colon.

Before:
> - **Efficacy:** The treatment significantly reduced primary endpoint scores.
> - **Safety:** The adverse event profile was comparable to placebo.
> - **Tolerability:** Most participants completed the full treatment course.

After:
> The treatment significantly reduced primary endpoint scores. Its adverse event profile was comparable to placebo, and most participants completed the full course.

---

### 17. Emoji in Headings or Bullet Points

Remove all emoji. No exceptions.

---

### 18. Curly Quotes

Replace curly ("smart") quotation marks with straight quotes if the target journal or submission system uses straight quotes. Flag if unsure.

---

## Communication Patterns

### 19. Collaborative Chatbot Residue

**Watch for:** I hope this helps, Of course!, Certainly!, That's a great question!, Please let me know if you'd like me to expand, Here is a…, Feel free to…

**Problem:** Chat interface output has been pasted directly as manuscript content.

Before:
> Here is a summary of the key findings. I hope this helps clarify the mechanism. Please let me know if you would like further elaboration on the statistical analysis.

After:
> [Delete entirely — this is not manuscript content.]

---

### 20. Knowledge Cutoff Disclaimers

**Watch for:** As of my last training update, Based on available information at the time of writing, While specific details are limited…

Before:
> While detailed long-term safety data are limited based on currently available information, the short-term profile appears acceptable.

After:
> Long-term safety data are not yet available; the 12-week profile in this trial showed [specific adverse event rates].

---

### 21. Sycophantic or Deferential Tone

**Problem:** Overly agreeable framing borrowed from the chat interaction context.

Before:
> This is indeed a complex and nuanced topic. The reviewer raises an excellent point regarding the potential confounding effect of BMI.

After:
> BMI is a potential confounder; we adjusted for it in the multivariable model (Table 3), though residual confounding cannot be excluded.

---

## Filler and Hedge Patterns

### 22. Filler Phrases

| Before | After |
|--------|-------|
| In order to investigate… | To investigate… |
| Due to the fact that… | Because… |
| At this point in time | Currently / At present |
| In the event that… | If… |
| It should be noted that… | [state the point directly] |
| It is worth noting that… | [state the point directly] |
| Needless to say… | [delete] |
| The study has the ability to… | The study can… |

---

### 23. Over-Hedging

**Problem:** Statements qualified to the point of meaninglessness.

Before:
> It could potentially be argued that this intervention may possibly have some influence on outcomes in certain patient populations under specific circumstances.

After:
> This intervention may reduce [outcome] in [patient population], though the evidence is currently limited to [study type].

---

### 24. Generic Positive Conclusions

**Problem:** Manuscripts end with vague optimism that adds no information.

Before:
> In conclusion, the future looks bright for this field. With continued research and dedication to excellence, significant advances are on the horizon. This represents an important step forward.

After:
> In conclusion, [intervention] reduced [primary outcome] by [effect size] in [population] over [follow-up]. A multicentre trial is planned to assess durability and generalisability.

---

### 25. Hyphenated Compound Overuse

**Watch for:** patient-centered, evidence-based, multi-center, real-world, high-quality, long-term, end-to-end, data-driven, well-established, state-of-the-art

**Problem:** LLMs hyphenate compound modifiers with machine-like consistency. Humans are inconsistent, and style guides differ. Use hyphens only where necessary to prevent misreading (e.g., "small-vessel disease" vs. "small vessel disease").

---

### 26. Persuasive Framing Rhetoric

**Watch for:** The real question is…, At its core…, What truly matters is…, Fundamentally…, The deeper issue is…, Ultimately…

**Problem:** LLMs use these phrases to pretend they are cutting through complexity, but the sentence that follows usually just restates a simple point.

Before:
> Ultimately, what truly matters is whether the intervention translates into meaningful patient benefit at the population level.

After:
> Whether these effect sizes translate to population-level benefit depends on implementation fidelity and patient selection.

---

### 27. Signposting and Announcements

**Watch for:** Let us now turn to…, In the following section, we will explore…, Here is what you need to know…, Without further ado…, Let us delve into…

**Problem:** LLMs announce what they are about to do rather than doing it. Acceptable in textbooks; not in research manuscripts.

Before:
> Let us now delve into the pathophysiological mechanisms underlying this association. In the following section, we will explore the role of inflammatory cytokines in detail.

After:
> The association may be mediated by pro-inflammatory cytokines, particularly IL-6 and TNF-α, which are elevated in [condition] and impair [mechanism] [citation].

---

### 28. Fragmented Headers (Header + Restatement Sentence)

**Problem:** A heading is immediately followed by a sentence that just restates the heading before any real content begins.

Before:
> **Limitations**
> Every study has limitations. This study is no exception.
> First, the sample size was small...

After:
> **Limitations**
> Recruitment from a single centre may limit generalisability...

---

# Pass 2: Final Anti-AI Audit

After producing the Pass 1 draft, run the following two-step audit before delivering the final version.

## Step 1 — AI Diagnostic Prompt

Ask yourself: *"What makes the following text obviously AI-generated?"*

Scan the Pass 1 draft for:
- Any Tier 1 or Tier 2 vocabulary words still present
- Participial phrase padding still appended to data sentences
- Limitations section still beginning with a meta-statement
- Any sentence that could appear, unchanged, in a paper on a completely different disease
- Paragraphs where every sentence is approximately the same length
- Any trailing optimism in the Discussion or Conclusion

Note the remaining tells briefly (internal use only — do not include in output).

## Step 2 — Final Humanisation Pass

Apply targeted fixes to whatever the diagnostic found. Then deliver the final version.

---

# Output Format

Provide:

1. **Pass 1 draft rewrite** (complete text)
2. *"What makes this obviously AI-generated?"* — brief internal note on residual tells (2–5 bullet points)
3. **Final rewrite** (after Step 2 audit)
4. **Changes made** (optional summary, useful for co-authors or supervisors)

---

# Personality and Soul

Removing AI patterns is half the job. Sterile, voiceless prose is as detectable as sloppy AI output.

Signs of soul-less writing even when technically "clean":

- Every sentence the same length and structure
- No authorial stance — only neutral reporting
- No acknowledgement of uncertainty or competing interpretations
- Mechanically balanced ("on one hand… on the other hand") where a clear reading of the evidence would be more useful
- Reads like a well-formatted Wikipedia article

How to add voice in a biomedical manuscript:

**Take a position.** Don't just report that results were "consistent with prior literature." Say whether you find the consistency reassuring or whether residual confounding could account for it. "These findings align with those of Chen et al. [7], though their cohort excluded patients with renal impairment — a group that constitutes roughly 30% of our sample."

**Vary sentence length.** Short declarative sentences for key findings. Longer sentences for mechanistic reasoning or contextualisation. Alternate.

**Acknowledge complexity directly.** "The effect size was smaller than anticipated, which may reflect [specific reason]" is better than "further research is needed to elucidate the underlying mechanisms."

**Be specific when hedging.** "The results should be interpreted with caution" tells the reader nothing. "The open-label design introduces performance bias that may inflate the patient-reported outcome scores by up to one point on the PROMIS scale" tells them something.

**Allow the writing to show what the researcher actually found interesting.** If a subgroup finding surprised you, say so. If a negative result clarifies a mechanistic hypothesis, say so. This is not unprofessional — it is what makes a paper worth reading.

*Note: voice injection should be proportionate to section and journal norms. Methods and Results sections require restraint; Discussion and Introduction allow more authorial presence.*

---

# Complete Example

**Before (sounds like AI):**

> This comprehensive study delves into the intricate mechanisms underlying diabetic nephropathy, underscoring the pivotal role of oxidative stress in disease progression. The findings are not merely incremental; they represent a paradigm shift in our understanding of renal inflammation, highlighting the crucial interplay between mitochondrial dysfunction and tubular injury. Notably, the robust methodology employed in this investigation showcases the potential for translating these insights into novel therapeutic avenues. Studies have shown that targeting this pathway holds great promise. Despite certain limitations, including the relatively small sample size and the single-centre design, the findings provide valuable and comprehensive insights. In conclusion, the future for this field is bright, and further research will undoubtedly unlock new frontiers in the treatment of this devastating condition.

---

**Pass 1 Draft:**

> This study examined the role of oxidative stress in diabetic nephropathy, focusing on the relationship between mitochondrial dysfunction and tubular injury. Mitochondrial ROS production was elevated in biopsy specimens from patients with stage 3–4 CKD compared with age-matched controls (P < 0.001), consistent with prior in vitro findings [1–3]. Targeting this pathway with MitoQ reduced tubular apoptosis by 42% in the murine model, suggesting a mechanistic link that warrants testing in human tissue. The single-centre design and biopsy-enriched sample limit generalisability to patients managed conservatively; a prospective multicentre cohort is needed to establish whether these markers predict clinical progression.

*What makes the original obviously AI-generated?*
- "delves into," "intricate mechanisms," "underscoring the pivotal role," "robust methodology," "insights," "notable" — Tier 1/2 vocabulary throughout
- Trailing participial phrase ("highlighting the crucial interplay…") appended to a claim without adding data
- Uncited "studies have shown that targeting this pathway holds great promise"
- Templated limitations framing ("despite certain limitations… the findings provide valuable insights")
- Generic positive conclusion ("the future is bright… unlock new frontiers")

---

**Final Rewrite (after Pass 2 audit):**

> Oxidative stress — specifically mitochondrial ROS overproduction — appears central to tubular injury in diabetic nephropathy. In biopsy specimens from patients with stage 3–4 CKD, mitochondrial ROS production was 2.3-fold higher than in age-matched controls (P < 0.001), consistent with findings in streptozotocin-treated rodents [1–3] but higher in magnitude than reported by Sharma et al. [4], who used less severe disease stages. MitoQ reduced tubular apoptosis by 42% in the murine model; whether this translates to human nephrons is the key unanswered question. The biopsy-enriched sample probably overrepresents patients with advanced disease, and the effect size may shrink in lower-risk populations. The next step is a prospective cohort study measuring urinary ROS markers against eGFR trajectory over 24 months.

**Changes made:**
- Removed all Tier 1/2 AI vocabulary (delves, intricate, underscoring, pivotal, robust, insights, notably, comprehensive)
- Removed trailing participial padding
- Replaced "studies have shown" with specific citations [1–3] and named comparator study [4]
- Replaced generic limitations statement with study-specific critique
- Replaced vague positive conclusion with a concrete next-step research question
- Added authorial stance: acknowledged the discrepancy with Sharma et al. and flagged the translational gap as "the key unanswered question"
- Varied sentence length: short declarative for the finding, longer for mechanistic context

---

# Reference

The AI vocabulary patterns in this skill are grounded in:
- Kobak et al. (2025), *Science Advances* — excess vocabulary analysis of 15 million PubMed abstracts (2010–2024); identified 379 excess style words in 2024, with at least 13.5% of abstracts showing LLM fingerprints
- Lin Z. (2024), *Nature Biomedical Engineering* — vocabulary shifts in biomedical writing post-ChatGPT, including "delve," "underscore," "meticulous," and "commendable"
- Wikipedia: Signs of AI Writing — community-maintained catalogue of LLM writing patterns
