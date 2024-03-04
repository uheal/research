# 2/28/24 Guardrails + AI Security

---

## Prevalent Security Issues
![image](https://github.com/uheal/research/assets/50297836/855e513a-7767-47fb-a1c4-63250b0b24ea)

- Three quantiles: Over reliant, General, and Technical
- Multiple AI Security issues throughout the distribution:
    - [x]  Hallucinations
    - [x]  Client Side Jailbreaks + Guardrails
    - [x]  Man in the Middle
    - Coercive Attacks → To work on later, how can we fix?
- The built AI system is required to be performant in securing each of these issues.

---

## Research regarding Security Issues

---

### Hallucinations

*Ref. paper #1:* https://arxiv.org/pdf/2307.03987.pdf ← Possible Hallucination mitigation technique

- Hallucination Detection technique ~88%
- Mitigation Detection technique ~57.6% of the correctly classified hallucinations.
- Does not introduce new hallucination.
- Method for mitigation:
    - There are two phases: Detection and Mitigation. During Detection phase, completions are checked within a knowledge base while a validation question is created. This is then fed into the model in order to repair the sentence and continue generating the next one.
- Issues with mitigation: For medical purposes, its hard to get enough data to build a knowledge base to effectively validate

*Ref. paper #2:* https://arxiv.org/pdf/2311.05232.pdf ← Hallucination causes, principles, etc.


- Hallucinations are a very general and broad term meaning model overconfidence while being unfactual.
- Hallucinations have several different causes and variants.
- **Hallucination Causes/possible solutions:**
    - Hallucination from Data
        - Flawed Data Source - Ensure datasets used for fine-tuning are accurate and do not carry biases
        - Inferior Data Utilization/Knowledge Recall Failures - Knowledge Clue Enhancement
    - Hallucinations from Training
        - Issue with pretraining - Architectural Improvement
        - Mitigating Misalignment - Properly define objectives to prioritize proper results rather than undesired/harmful behaviors
    - Inference-related Hallucinations
        - Factuality Enhanced Decoding - Post-editing Decoding
            - Consists of Automated and Manual approaches - One with a person modifying decoded completion and another having a smaller model modify.
            - Within **Automated** post-edited decoding, a smaller model can be used for content filtering, etc.
        - SoftMax Bottleneck - Less complex distributions as a result of SoftMax.

- **Hallucination Detection / Benchmarks**
    

    

### Client Side Jailbreak + Guardrails:

*Ref. paper #1:* https://arxiv.org/pdf/2306.11698.pdf

- GPTs and auto decoder models are prone to jailbreaks

*Ref. paper #2:* https://arxiv.org/pdf/2310.08419.pdf

- Types of Jailbreaks:
    - Prompt Level - semantically meaningful deception and social engineering to elicit objectional content from LLMS (Like DAN)
    - Token Level - Finding hidden responses by modifying input tokens in a particular way
    - PAIR: Prompt Automatic Iterative Refinement - automates prompt-level jailbreaks.
        

        
    

*Ref. paper #3:  NeMo Guardrails -* https://arxiv.org/pdf/2310.10501.pdf

- Programmable Rails
- Using Colang, users can specify what their defined rails are in order to keep  the model aligned to the specific task
- Limitations
    - Should be used with embedded rails - System prompts, etc.
    - Extra latency/not as performant - This is due to the CoT prompting approach
    - Extra cost
    

*Ref. docs: Guardrails-ai -* https://www.guardrailsai.com/docs-selector

- Another open-source framework for guardrails
- uses RAIL - **R**eliable **AI** markup **L**anguage

- With Guardrails -  what should be protected:
    - User Data - Privacy
    - Specific Medical Domains - EMT (Ear, Mouth, Tongue)
    - Specific Dialogue flows to maintain domain specificity
    - LLM Security Vulnerabilities
    

## Man in the Middle:

- Guards for patient privacy - NeMo Guardrails, Secure DBs, etc.
- Specific  CHW IDs to ensure that they are the proper user and its not a malicious 3rd party.
