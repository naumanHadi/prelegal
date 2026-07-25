---
name: OpenAI Inference
description: Use this to write code to call an LLM using LiteLLM against the OpenAI API directly
---

# Calling an LLM via OpenAI

These instructions allow you write code to call an LLM directly via the OpenAI API.  
This method uses LiteLLM.

## Setup

The OPENAI_API_KEY must be set in the .env file and loaded in as an environment variable.  

The uv project must include litellm and pydantic.
`uv add litellm pydantic`

## Code snippets

Use code like these examples in order to use OpenAI.

### Imports and constants

```python
from litellm import completion
MODEL = "gpt-4o-mini"
```

### Code to call OpenAI for a text response

```python
response = completion(model=MODEL, messages=messages)
result = response.choices[0].message.content
```

### Code to call OpenAI for a Structured Outputs response

```python
response = completion(model=MODEL, messages=messages, response_format=MyBaseModelSubclass)
result = response.choices[0].message.content
result_as_object = MyBaseModelSubclass.model_validate_json(result)
```