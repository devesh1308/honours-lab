# Experiment No. 2

# Title

System Prompt Engineering for Structured JSON Data Extraction using Large Language Models

---

# Aim

To design and implement a robust system prompt that extracts unstructured engineering fault logs into a predefined JSON schema using a Large Language Model (LLM).

---

# Theory

Large Language Models (LLMs) are capable of understanding natural language and generating structured outputs when guided through carefully designed prompts.

A **System Prompt** defines the behavior, role, and response format of the model. Unlike user prompts, system prompts remain active throughout the interaction and help enforce strict output constraints.

In software engineering applications, unstructured text such as maintenance logs, customer complaints, and incident reports cannot be directly processed by backend systems. Therefore, prompt engineering techniques are used to convert these logs into machine-readable formats like JSON.

The experiment demonstrates how schema enforcement, deterministic decoding, and JSON validation can be combined to produce reliable structured outputs suitable for downstream software applications.

---

# Software Used

- Python 3.x
- Visual Studio Code
- Groq API
- OpenAI Python SDK
- python-dotenv
- json module

---

# Sample Input

```text
URGENT LOG ENTRY - 02-AUG-2026 14:22 UTC

System alert raised on High-Pressure Boiler Unit #4.

Thermal sensors detected overheating in the primary coolant intake loop and pressure relief valve B.

Operator logged issue under INC-88201.

Severity classified as CRITICAL.

Immediate shutdown initiated and technician dispatch required to replace intake seals.
```

---

# JSON Schema

```json
{
  "incident_id": "string or null",
  "equipment_name": "string",
  "failure_type": "string",
  "severity": "string",
  "affected_subsystems": [
    "list of strings"
  ],
  "recommended_action": "string"
}
```

---

# Procedure

1. Install the required Python libraries.
2. Configure the Groq API key using the `.env` file.
3. Initialize the OpenAI-compatible Groq client.
4. Define a strict System Prompt describing the required JSON schema.
5. Provide the engineering fault log as the User Prompt.
6. Generate the JSON response using the LLM.
7. Parse the generated response using Python's `json.loads()` method.
8. Validate whether the generated response conforms to valid JSON syntax.
9. Display the structured output.

---

# Experimental Results

## Generated JSON Output

```json
{
  "incident_id": "INC-88201",
  "equipment_name": "High-Pressure Boiler Unit #4",
  "failure_type": "overheating",
  "severity": "CRITICAL",
  "affected_subsystems": [
    "primary coolant intake loop",
    "pressure relief valve B"
  ],
  "recommended_action": "replace intake seals and shutdown"
}
```

---

# Observation Table

| Parameter | Observation |
|-----------|-------------|
| System Prompt | Successfully constrained the LLM to generate structured JSON output. |
| Temperature = 0.0 | Produced deterministic and consistent responses. |
| JSON Validation | Successfully parsed using Python's `json.loads()` without errors. |
| Output Format | No conversational text or markdown formatting was generated. |
| Schema Enforcement | All required JSON fields were correctly populated from the engineering log. |

---

# Result Analysis

The experiment successfully demonstrated that carefully designed system prompts can reliably convert unstructured engineering logs into structured JSON objects.

The use of a deterministic temperature (`0.0`) ensured consistent output while the predefined schema prevented unwanted conversational responses.

Programmatic validation using Python's `json` module confirmed that the generated output was syntactically correct and ready for use in software applications such as maintenance systems, databases, and analytics pipelines.

---

# Comparison with Batchmates

Although all students used similar engineering logs, slight differences were observed in field naming, wording of the recommended action, and subsystem extraction depending on the model configuration and prompt wording.

However, the generated JSON structure remained consistent due to the predefined schema and deterministic decoding settings.

---

# Key Learning Outcomes

- Understood the importance of System Prompts in controlling LLM behavior.
- Learned how schema enforcement enables reliable structured output generation.
- Gained practical experience with JSON extraction from unstructured text.
- Learned how deterministic decoding improves consistency.
- Validated generated responses programmatically using Python.

---

# Conclusion

The experiment successfully demonstrated the practical application of prompt engineering for structured data extraction.

Using a carefully designed System Prompt, the Large Language Model accurately transformed an unstructured engineering fault log into a valid JSON object.

The generated output satisfied the predefined schema and passed Python-based validation, making it suitable for direct integration into software engineering workflows, database systems, and automated maintenance applications.

---

# Screenshots

## Program Output

![Program Output](EXPERIMENT2/OUTPUT.png)

