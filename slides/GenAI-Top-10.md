# GenAI Top 10

---

## About

* The OWASP Top 10 for Large Language Model Applications started in 2023
* Community-driven effort to highlight and address security issues specific to AI applications. 
* The technology has continued to spread across industries and applications, and so have the associated risks. 
* As LLMs are embedded more deeply in everything from customer interactions to internal operations
* Developers and security professionals are discovering new vulnerabilities—and ways to counter them.
* ![](../images/openverse-42645941185_30884891c2_b.jpg)

---

## LLM01:2025 Prompt Injection
* A Prompt Injection Vulnerability occurs when user prompts alter the LLM’s behavior or output in unintended ways. These inputs can affect the model even if they are imperceptible to humans, therefore prompt injections do not need to be human-visible/readable, as long as the content is parsed by the model.
* Direct Prompt Injections
  * Direct prompt injections occur when a user’s prompt input directly alters the behavior of the model in unintended or unexpected ways.
* Indirect Prompt Injections
  * Indirect prompt injections occur when an LLM accepts input from external sources, such as websites or files.

---

## Prompt injection payload
* Disclosure of sensitive information
* Revealing sensitive information about AI system infrastructure or system prompts
* Content manipulation leading to incorrect or biased outputs
* Providing unauthorized access to functions available to the LLM
* Executing arbitrary commands in connected systems
* Manipulating critical decision-making processes

---

## Example Attack Scenarios
* Scenario #1: Direct Injection
  * An attacker injects a prompt into a customer support chatbot, instructing it to ignore previous guidelines, query private data stores, and send emails, leading to unauthorized access and privilege escalation.

* Scenario #2: Indirect Injection
  * A user employs an LLM to summarize a webpage containing hidden instructions that cause the LLM to insert an image linking to a URL, leading to exfiltration of the the private conversation.

* Scenario #3: Unintentional Injection
  * A company includes an instruction in a job description to identify AI-generated applications. An applicant, unaware of this instruction, uses an LLM to optimize their resume, inadvertently triggering the AI detection.

---

## LLM01: Prompt Injection Mitigation
* Manipulating LLMs via crafted inputs can lead to unauthorized access, data breaches, and compromised decision-making.
* Mitigation
* Constrain model behavior
  * Provide specific instructions about the model’s role, capabilities, and limitations within the system prompt. Enforce strict context adherence, limit responses to specific tasks or topics, and instruct the model to ignore attempts to modify core instructions.
* Define and validate expected output formats
  * Specify clear output formats, request detailed reasoning and source citations, and use deterministic code to validate adherence to these formats.
  * Lab: Getting Structured LLM Output
* Implement input and output filtering
  * Provide the application with its own API tokens for extensible functionality, and handle these functions in code rather than providing them to the model. Restrict the model’s access privileges to the minimum necessary for its intended operations.
* [Details](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
---

# LLM02:2025 Sensitive Information Disclosure
* Sensitive information can affect both the LLM and its application context. 
  * Personal identifiable information (PII), 
  * financial details, 
  * health records, 
  * confidential business data, 
  * security credentials, and l
  * egal documents. 
* Proprietary models may also have unique training methods and source code considered sensitive, 
  * especially in closed or foundation models.
* [Details](https://genai.owasp.org/llmrisk/llm022025-sensitive-information-disclosure/)
---

## Common Examples of LLM02 Vulnerability
* PII Leakage
  * Personal identifiable information (PII) may be disclosed during interactions with the LLM.

* Proprietary Algorithm Exposure
  * Poorly configured model outputs can reveal proprietary algorithms or data. Revealing training data can expose models to inversion attacks, where attackers extract sensitive information or reconstruct inputs. For instance, as demonstrated in the ‘Proof Pudding’ attack (CVE-2019-20634), disclosed training data facilitated model extraction and inversion, allowing attackers to circumvent security controls in machine learning algorithms and bypass email filters.

* Sensitive Business Data Disclosure
  * Generated responses might inadvertently include confidential business information.

---


## Prevention and Mitigation Strategies

* Integrate Data Sanitization Techniques
  * Implement data sanitization to prevent user data from entering the training model. This includes scrubbing or masking sensitive content before it is used in training.

* Robust Input Validation
  * Apply strict input validation methods to detect and filter out potentially harmful or sensitive data inputs, ensuring they do not compromise the model.

---

## LLM03:2025 Supply Chain
* LLM supply chains are susceptible to various vulnerabilities, which can affect the integrity of training data, models, and deployment platforms. 
* These risks can result in biased outputs, security breaches, or system failures. 
* While traditional software vulnerabilities focus on issues like code flaws and dependencies, in ML the risks also extend to third-party pre-trained models and data.

* These external elements can be manipulated through tampering or poisoning attacks.

*![](../images/openverse-15983822552_81e81003e5_b.jpg)
---

## Common Examples of Risks
* Traditional Third-party Package Vulnerabilities
  * Such as outdated or deprecated components, which attackers can exploit to compromise LLM applications. This is similar to “A06:2021 – Vulnerable and Outdated Components” with increased risks when components are used during model development or finetuning. (Ref. link: A06:2021 – Vulnerable and Outdated Components)

* Licensing Risks
  * AI development often involves diverse software and dataset licenses, creating risks if not properly managed. Different open-source and proprietary licenses impose varying legal requirements. Dataset licenses may restrict usage, distribution, or commercialization.

* Outdated or Deprecated Models
  * Using outdated or deprecated models that are no longer maintained leads to security issues.

---

## Sample Attack Scenarios
* Vulnerable Python Library
  * An attacker exploits a vulnerable Python library to compromise an LLM app. This happened in the first Open AI data breach. Attacks on the PyPi package registry tricked model developers into downloading a compromised PyTorch dependency with malware in a model development environment. 
* Direct Tampering

---

## LLM04:2025 Data and Model Poisoning
* Data poisoning occurs when pre-training, fine-tuning, or embedding data is manipulated to introduce vulnerabilities, backdoors, or biases. 
* This manipulation can compromise model security, performance, or ethical behavior, leading to harmful outputs or impaired capabilities. 
* Common risks include degraded model performance, biased or toxic content, and exploitation of downstream systems.

---

## LLM05:2025 Improper Output Handling

* Improper Output Handling refers specifically to insufficient validation, sanitization, and handling of the outputs generated by large language models before they are passed downstream to other components and systems. 
* Since LLM-generated content can be controlled by prompt input, this behavior is similar to providing users indirect access to additional functionality.

---

## LLM06:2025 Excessive Agency
* An LLM-based system is often granted a degree of agency by its developer – the ability to call functions or interface with other systems via extensions (sometimes referred to as tools, skills or plugins by different vendors) to undertake actions in response to a prompt.
* Common triggers include:
  * hallucination/confabulation caused by poorly-engineered benign prompts, or just a poorly-performing model;
  * direct/indirect prompt injection from a malicious user
* The root cause of Excessive Agency is typically one or more of:
  * excessive functionality;
  * excessive permissions;
  * excessive autonomy.
  
---

## LLM07:2025 System Prompt Leakage
* The system prompt leakage vulnerability in LLMs refers to the risk that the system prompts or instructions used to steer the behavior of the model can also contain sensitive information that was not intended to be discovered.
* Common Examples of Risk
  * Exposure of Sensitive Functionality
  * Exposure of Internal Rules
  * Revealing of Filtering Criteria
  * Disclosure of Permissions and User Roles
* Prevention and Mitigation Strategies
  * Separate Sensitive Data from System Prompts

---


## References
* [Top 10](https://genai.owasp.org/llm-top-10/)
* [Ref](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Conf](https://genai.owasp.org/)


---

