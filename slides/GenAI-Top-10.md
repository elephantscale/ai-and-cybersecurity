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
* Neglecting to validate LLM outputs may lead to downstream security exploits, including code execution that compromises systems and exposes data.
* Mitigation
* Integrate Data Sanitization Techniques
  * Implement data sanitization to prevent user data from entering the training model. This includes scrubbing or masking sensitive content before it is used in training. 
* Robust Input Validation
  * Apply strict input validation methods to detect and filter out potentially harmful or sensitive data inputs, ensuring they do not compromise the model.

---

## LLM03: Training Data Poisoning
* Tampered training data can impair LLM models leading to responses that may compromise security, accuracy, or ethical behavior.
![](../images/openverse-1397376024_dcb6ee9ebf.jpg)
---


## LLM04: Model Denial of Service
* Overloading LLMs with resource-heavy operations can cause service disruptions and increased costs.
---


## LLM05: Supply Chain Vulnerabilities
* Depending upon compromised components, services or datasets undermine system integrity, causing data breaches and system failures.
---


## LLM06: Sensitive Information Disclosure
* Failure to protect against disclosure of sensitive information in LLM outputs can result in legal consequences or a loss of competitive advantage.
---


## LLM07: Insecure Plugin Design
* LLM plugins processing untrusted inputs and having insufficient access control risk severe exploits like remote code execution.
---

## LLM08: Excessive Agency
* Granting LLMs unchecked autonomy to take action can lead to unintended consequences, jeopardizing reliability, privacy, and trust.
---

## LLM09: Overreliance
* Failing to critically assess LLM outputs can lead to compromised decision making, security vulnerabilities, and legal liabilities.
---


## LLM10: Model Theft
* Unauthorized access to proprietary large language models risks theft, competitive advantage, and dissemination of sensitive information.
---

## References
* [Ref](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Conf](https://genai.owasp.org/)
* [Project](https://genai.owasp.org/llm-top-10/)

---

