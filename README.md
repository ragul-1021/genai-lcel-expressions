# Design and Implementation of LangChain Expression Language (LCEL) Expressions

## AIM
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality through relevant real-world examples.

## PROBLEM STATEMENT
To develop an LCEL-based application that accepts a topic and a preferred explanation style as inputs, generates a response using a language model, and converts the model output into a readable string using an output parser.

## DESIGN STEPS

### STEP 1: Configure the environment
Import the required LangChain modules and load the OpenAI API key from the `.env` file.

### STEP 2: Define the prompt and model
Create a prompt template with two parameters, `topic` and `style`. Initialize the ChatOpenAI model with a suitable model name and temperature.

### STEP 3: Construct and execute the LCEL chain
Create a `StrOutputParser` and combine the prompt, model, and parser using the LCEL pipe operator (`|`). Invoke the chain with sample inputs and display the generated response.

## PROGRAM

```python
import os
from dotenv import load_dotenv, find_dotenv

from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.output_parsers import StrOutputParser

# Load environment variables
load_dotenv(find_dotenv())

# Define the prompt template
prompt = ChatPromptTemplate.from_template(
    "Explain {topic} in a {style} way."
)

# Initialize the model
model = ChatOpenAI(
    model="gpt-4o-mini",
    temperature=0
)

# Initialize the output parser
output_parser = StrOutputParser()

# Create the LCEL chain
chain = prompt | model | output_parser

# Invoke the chain with two parameters
result = chain.invoke({
    "topic": "Artificial Intelligence",
    "style": "simple and easy to understand"
})

print("Output:")
print(result)
```

## OUTPUT
The program generates a simple, easy-to-understand explanation of Artificial Intelligence based on the provided topic and style.

## RESULT
Thus, the LangChain Expression Language (LCEL) expression was successfully designed and implemented using two prompt parameters and three components: prompt, model, and output parser. The chain was executed successfully to generate the desired output.
<img width="1535" height="712" alt="WhatsApp Image 2026-11-02 at 4 16 15 PM" src="https://github.com/user-attachments/assets/cb8b867a-0b7c-4124-8b6a-5ef169723a9c" />
