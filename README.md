# Lab 2a: Generating Text with OpenAI’s Models

---

## 📘 Introduction

In this lab, we delve into the fascinating world of AI-driven text generation using OpenAI's advanced models. The rapid evolution of AI technologies has made it possible to generate coherent, contextually relevant, and often insightful text completions and responses. This technology is not just a cornerstone of modern natural language processing (NLP) but is also reshaping how we interact with machines, creating new possibilities in various fields like journalism, creative writing, programming, and more.

By the end of this lab, you will be equipped with the practical skills to harness the power of AI in generating text, which is a critical skill in the evolving landscape of business and technology.

---

## 🎯 Learning Objectives

- **Understand the Capabilities of OpenAI's Language Models:** Gain a foundational understanding of what OpenAI's language models like GPT-3.5-turbo are capable of, including their strengths and limitations in text generation.
- **Develop Skills in Using OpenAI's API for Text Generation:** Learn to effectively utilize OpenAI's API to generate text, including setting up the necessary development environment, understanding API documentation, and executing API calls.
- **Implement Python Functions for Customized Text Generation:** Acquire the ability to write Python functions that interact with OpenAI’s models, enabling tailored text generation based on specific user inputs and scenarios.
- **Explore and Analyze Different Text Generation Techniques:** Experiment with various prompts and settings to understand how different inputs influence the AI's text output.

---

## ⏱️ Estimated Time
1 hour

---

## 💵 Estimated Cost
$0.02 (View your OpenAI usage [here](https://platform.openai.com/usage))

---

## 🧰 Materials

- OpenAI account & API key  
- [Text Completions Colab notebook](https://colab.research.google.com/drive/1A70EtOMPj8IKoXW_7URsWuXFDc4fho0E?usp=sharing)

---

## ⚙️ Setting Up Your Development Environment

1. **Make a copy** of the [Text Completions Colab](https://colab.research.google.com/drive/1A70EtOMPj8IKoXW_7URsWuXFDc4fho0E?usp=sharing)

2. To set up your development environment, you will need to install the OpenAI Python library, which we will use to generate text in this lab. You can run the following shell scripts, which are also **pre-written** in the first cell of your Colab notebook, to do so.

```Python
# Uninstall Colab's preinstalled modules which have dependency conflicts with OpenAI
!pip uninstall tensorflow-probability -y 
!pip uninstall llmx -y 

# Install the OpenAI Python library
!pip install --upgrade openai
```

3. Now, locate your OpenAI API key that you have saved in Lab 1. You may already have one from a previous lab; if not, please refer to Lab 1 for instructions. If you cannot find your API key anymore, you may need to create a new one [here](https://platform.openai.com/api-keys).

---

## 📥 Importing and Initializing OpenAI

1. Now that you have the OpenAI Python library installed, we can begin to code. At the top of your cell, import OpenAI.

```Python
from openai import OpenAI
```

2. Next, initialize an OpenAI object. This will allow you to use the OpenAI API to communicate with OpenAI’s models. Make sure to **replace your-api-key-here** with your API key.

```Python
client = OpenAI(api_key='your-api-key-here')
```

---


## 💬 Function to Generate a Response from the Model

1. Create a function titled get_completion with 2 parameters: prompt and model= "gpt-3.5-turbo" 
      - This function will prompt the specified OpenAI model with the user’s input (prompt) to generate 
        and return a desired response.

```Python
def get_completion(prompt, model="gpt-3.5-turbo"):
```

2. The **chat.completions.create** function is a function from the OpenAI Python library which creates a model response for the given chat conversation. It has 2 required parameters: **model and messages**. 

model is specified as a string, the name of one of OpenAI’s different text generation models (i.e. gpt-4, gpt-4 turbo, gpt-3.5-turbo). Different models can be selected for different purposes.

messages is a list of message objects, which are of the form {"role": _____, "content": ___}. Each object has a **role** (either "system", "user", or "assistant") and **content**. Conversations can be as short as one message or many back and forth turns.

Use the **chat.completions.create** function inside your **get_completion** function as shown below to retrieve the desired response. 

```Python
def get_completion(prompt, model="gpt-3.5-turbo"): 
   completion = client.chat.completions.create(
        model=model,
        messages=[
        {"role": "system", "content": ___}, 
        {"role": "user", "content": prompt},
        ]
    )
   return completion.choices[0].message.content
```

3. Fill in the blank after "content" to tell OpenAI what role to play. (In ours, we told it to "Be a couplet poet"! Other ideas might include "You are William Shakespeare.")

⚠️ Running the get_completion function will call the OpenAI API, which costs money. This is typically a few cents per call (depending on the model used), but it can add up, so don’t run it before you are ready.


---


## 🎮 Using the Function with User Input

1. Now we have a function that can give the OpenAI model a role to play, then return its response to a prompt. Let’s test it out! First, ask the user for an input and store it in a variable named **prompt**.

```Python
prompt = input("Enter a prompt: ")
```

2. Pass the input through the **get_completion** function and store it in a variable named **response**.

⚠️ Running the get_completion function will call the OpenAI API, which costs money. This is typically a few cents per call (depending on the model used), but it can add up, so don’t run it before you are ready.

```Python
response = get_completion(prompt)
```

3. Finally, display the response obtained from OpenAI! 

```Python
print(response)
```

4. Try playing around with different inputs and giving the model different roles and see what happens!

5. Finally, modify your code so that it can create a poem based on your prompt.

6. After you finish your lab, check your OpenAI usage [here](https://platform.openai.com/usage) to get a sense of the cost associated with the Open AI API calls. Take a screenshot of your usage, including “Cost” and “Activity”


---


## ✅ Congratulations, you have successfully finished the lab tutorial!

Please submit your work as a PDF file with 
1) a Colab link
2) the prompt you used
3) screenshots of your output 
4) screenshots of your usage page including both Cost and Activity

To help the teaching team grade your lab effectively and to protect your API security. 

Please follow these steps before submitting:

  1. Update your Colab setting so that everyone in SJSU group can be a viewer;

  2. Please change your API key in your code to “my-api-key-here”


---


## 🔗 References

[OpenAI Quickstart](https://platform.openai.com/docs/quickstart?lang=ChatCompletions)

[OpenAI Chat API Docs](https://platform.openai.com/docs/api-reference/chat)




