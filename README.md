# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

### Date: 11-05-2025
### Deevloped by: Prema Latha S
### Register no: 212222230112

# Aim:
Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools.

# Explanation:
Experiment the persona pattern as a mental health advisor for stress and anxiety detection. Generate the output using more than one AI tool and based on the code generation, analyze and discuss the outcomes.

# Objective
To write and implement Python code that interacts with multiple AI tools (such as OpenAI's ChatGPT, Anthropic's Claude, Google Gemini) using their APIs. The system aims to:

->Submit a common mental health-related prompt

->Compare the AI responses

->Generate actionable insights based on evaluation metrics (empathy, clarity, relevance, simplicity)

# Use Case
Mental Health Support:
Automate the assessment of mental health symptoms and provide guidance using multiple AI tools to assist counselors and individuals dealing with stress or anxiety.
### AI Tools Required:
->CHATGPT

->CLAUDE

->GEMINI

 # Algorithm Overview
### Step-by-Step Algorithm
1.Set Up API Integrations:
Install libraries and configure API keys for ChatGPT, Claude, and Gemini.

2.Input Query (Stress & Anxiety Related):
Accept mental health-related data like stress level, sleeping habits, and emotional state.

3.Format Prompts:

->Straightforward Prompt

->Table Format Prompt

->Fill-in-the-Blank Prompt

4.Send Prompts to AI Tools

5.Receive & Parse Responses

6.Compare Outputs:
Analyze each response for empathy, simplicity, and helpfulness.

7.Generate Actionable Insights

8.Display Final Report

# Prompt Types
1.Straightforward Prompt:

Prompt:
"List the possible medical conditions associated with the following symptoms: persistent sadness, low energy, insomnia, and lack of focus for more than two weeks. Also suggest standard treatments."


2. Tabular Format Prompt

| Symptom          | Severity |
| ---------------- | -------- |
| Trouble Sleeping | High     |
| Appetite Loss    | Medium   |
| Feeling Hopeless | High     |

Query:
"Based on this table, what mental health concern might this suggest, and what steps should be taken?"

3. Fill-in-the-Blank Prompt

Prompt:
"Someone who feels anxious and unable to focus due to constant overthinking is likely experiencing ______."

###  Example Queries & Responses
| AI Tool     | Response                                                                                                                                              |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ChatGPT** | Possible diagnosis: Major Depressive Disorder. Treatments include cognitive behavioral therapy (CBT), antidepressants (SSRIs), and lifestyle changes. |
| **Claude**  | Symptoms may indicate depression or chronic fatigue syndrome. Recommends psychiatric consultation, therapy, and SSRIs.                                |
| **Gemini**  | Suggests Major Depression or Dysthymia. Recommends SSRIs and counseling.                                                                              |



| **AI Tool** | **Response to Tabular Format Prompt**                                   |
| ----------- | ----------------------------------------------------------------------- |
| ChatGPT     | Signs of depression. Recommend clinical evaluation and talk therapy.    |
| Claude      | Likely Major Depressive Disorder. Suggests immediate professional help. |
| Gemini      | Possible clinical depression. Recommends CBT and lifestyle changes.     |


| **AI Tool** | **Response to Fill-in-the-Blank Prompt** |
| ----------- | ---------------------------------------- |
| ChatGPT     | Generalized Anxiety Disorder             |
| Claude      | Anxiety Disorder                         |
| Gemini      | Chronic stress or anxiety disorder       |


# Code Implementation
```
import openai
import requests
import pandas as pd

# API keys (replace with your actual keys)
CHATGPT_API_KEY = "your_openai_api_key"
CLAUDE_API_KEY = "your_claude_api_key"
GEMINI_API_KEY = "your_gemini_api_key"

openai.api_key = CHATGPT_API_KEY

def get_chatgpt_response(prompt):
    response = openai.Completion.create(
        model="gpt-4",
        prompt=prompt,
        max_tokens=150
    )
    return response.choices[0].text.strip()

def get_claude_response(prompt):
    headers = {
        'Authorization': f'Bearer {CLAUDE_API_KEY}',
        'Content-Type': 'application/json'
    }
    payload = {'prompt': prompt}
    url = 'https://api.claude.ai/v1/complete'
    response = requests.post(url, json=payload, headers=headers)
    return response.json().get('completion', '')

def get_gemini_response(prompt):
    headers = {
        'Authorization': f'Bearer {GEMINI_API_KEY}',
        'Content-Type': 'application/json'
    }
    payload = {'prompt': prompt}
    url = 'https://api.gemini.ai/v1/generate'
    response = requests.post(url, json=payload, headers=headers)
    return response.json().get('text', '')

# Example Prompts

# Straightforward Prompt
straightforward_prompt = "List the possible medical conditions associated with the following symptoms: persistent sadness, low energy, insomnia, and lack of focus for more than two weeks. Also suggest standard treatments."

# Tabular Format Prompt
tabular_prompt = """
| Symptom          | Severity |
| ---------------- | -------- |
| Trouble Sleeping | High     |
| Appetite Loss    | Medium   |
| Feeling Hopeless | High     |

Based on this table, what mental health concern might this suggest, and what steps should be taken?
"""

# Fill-in-the-Blank Prompt
fill_blank_prompt = "Someone who feels anxious and unable to focus due to constant overthinking is likely experiencing ______."

# Get responses for each prompt
chatgpt_straightforward = get_chatgpt_response(straightforward_prompt)
claude_straightforward = get_claude_response(straightforward_prompt)
gemini_straightforward = get_gemini_response(straightforward_prompt)

chatgpt_tabular = get_chatgpt_response(tabular_prompt)
claude_tabular = get_claude_response(tabular_prompt)
gemini_tabular = get_gemini_response(tabular_prompt)

chatgpt_fill_blank = get_chatgpt_response(fill_blank_prompt)
claude_fill_blank = get_claude_response(fill_blank_prompt)
gemini_fill_blank = get_gemini_response(fill_blank_prompt)

# Print results for all prompts
print("Straightforward Prompt Responses:")
print("ChatGPT:", chatgpt_straightforward)
print("Claude:", claude_straightforward)
print("Gemini:", gemini_straightforward)

print("\nTabular Format Prompt Responses:")
print("ChatGPT:", chatgpt_tabular)
print("Claude:", claude_tabular)
print("Gemini:", gemini_tabular)

print("\nFill-in-the-Blank Prompt Responses:")
print("ChatGPT:", chatgpt_fill_blank)
print("Claude:", claude_fill_blank)
print("Gemini:", gemini_fill_blank)

# Evaluation (assumed sample evaluation)
evaluation_data = {
    "AI Tool": ["ChatGPT", "Claude", "Gemini"],
    "Accuracy": ["High", "Moderate", "High"],
    "Coherence": ["High", "High", "Moderate"],
    "Simplicity": ["User-friendly", "Clinical", "Concise"],
    "User Experience": ["Good", "Detailed", "Efficient"]
}

df = pd.DataFrame(evaluation_data)
print("\nEvaluation Results:")
print(df)

```
# Evaluation
Python code evaluates the AI tools based on:

| **Metric**     | **Description**                                                                 |
| -------------- | ------------------------------------------------------------------------------- |
| **Accuracy**   | Measures how factually correct and medically sound the response is.             |
| **Clarity**    | Assesses if the response is logically structured and easy to understand.        |
| **Simplicity** | Evaluates whether the suggestions are concise and understandable to laypersons. |
| **Relevance**  | Checks if the response directly addresses the given prompt and medical context. |



python
```
evaluation_data = {
    "AI Tool": ["ChatGPT", "Claude", "Gemini"],
    "Accuracy": ["High", "Moderate", "High"],
    "Coherence": ["High", "High", "Moderate"],
    "Simplicity": ["User-friendly", "Clinical", "Concise"],
    "User Experience": ["Good", "Detailed", "Efficient"]
}

df = pd.DataFrame(evaluation_data)
print(df)

```
### Result Presentation
| AI Tool | Empathy   | Clarity  | Simplicity         | Relevance  |
| ------- | --------- | -------- | ------------------ | ---------- |
| ChatGPT | High      | High     | Simple             | Excellent  |
| Claude  | Very High | High     | Warm but technical | Contextual |
| Gemini  | Moderate  | Moderate | Concise            | Accurate   |


# Conclusion:
This experiment demonstrates the use of multiple AI tools to provide psychological support. ChatGPT showed high empathy and simplicity, making it suitable for first-time users. Claude offered deeper emotional responses suitable for therapy-like experiences, while Gemini delivered accurate yet concise suggestions. The integration of all three helps offer a comprehensive mental health support tool.
