# How to Use the DeepSeek R1 Model via NVIDIA AI API (Using OpenAI Python Client)
#### Overview
DeepSeek R1 is a powerful large language model (LLM) accessible through NVIDIA’s AI API platform. It is designed for high-performance text generation and natural language understanding tasks. Instead of calling OpenAI-hosted models like GPT-4, you use OpenAI’s Python client to interface with NVIDIA-hosted models like DeepSeek R1.

### Step-by-Step Guide
###### Step 1: Install Required Libraries
You’ll need the official OpenAI client SDK for Python.

````
pip install openai
````


###### Step 2: Get Your API Key from NVIDIA NGC

To access NVIDIA's hosted models via API, you need an API key:

+ Go to https://org.ngc.nvidia.com.

+ Log in and navigate to Setup > API Keys.

+ Generate a new key or copy your existing key.


**Note: This key is only required if you're running the code outside of NVIDIA’s infrastructure.**


###### Step 3: Initialize the OpenAI Client with NVIDIA Endpoint
```
from openai import OpenAI

client = OpenAI(
    base_url="https://integrate.api.nvidia.com/v1",  # NVIDIA's AI endpoint
    api_key="YOUR_NVIDIA_API_KEY"
)
```

**base_url: Routes the OpenAI client to NVIDIA’s backend instead of OpenAI’s.**

**api_key: Ensures authenticated access.**


###### Step 4: Prepare the Chat Completion Request
```
completion = client.chat.completions.create(
    model="deepseek-ai/deepseek-r1",
    messages=[
        {"role": "user", "content": "Explain quantum computing in simple terms."}
    ],
    temperature=0.6,
    top_p=0.8,
    max_tokens=1024,
    stream=True
)
```

###### Step 5: Stream and Display the AI Response

```
for chunk in completion:
    if chunk.choices[0].delta.content is not None:
        print(chunk.choices[0].delta.content, end="")
```

### Use Cases for DeepSeek R1

•	Natural language understanding

•	Conversational AI (chatbots)

•	Content summarization

•	Code generation and explanation

•	Research assistants and Q&A bots

