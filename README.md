# Development-of-Python-Code-Compatible-with-Multiple-AI-Tools
Done by: Kaushika A<br>
Reg no: 212221230048

## Experiment:
Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights.
## Aim:
To compare the responses of two open-source language models, GPT-Neo and GPT-2, to a given question and analyze how different models generate text and handle natural language queries.
## Procedure:
### Install Required Libraries:
- Use the command below to install the necessary Python libraries:
    - pip install transformers torch
- Load Models:
    - Load two pre-trained language models from Hugging Face:
    - GPT-Neo (EleutherAI/gpt-neo-1.3B).
    - GPT-2 (gpt2).
- Define Functions:
    - Define two functions to generate text from both models.
    - GPT-Neo Function: Generates text from the GPT-Neo model.
    - GPT-2 Function: Generates text from the GPT-2 model.
- Generate Answers:
    - Input a question to both models and generate their responses.
- Compare Answers:
    - Compare the generated answers from both models to see if they match or differ.
    - Print the responses and a summary indicating whether the answers are the same or different.
- Execute the Code:
    - Run the code to generate and compare answers.

### Python Script: 
```py
from transformers import pipeline
# Load GPT-Neo and GPT-2 models
generator_neo = pipeline('text-generation', model='EleutherAI/gpt-neo-1.3B')
generator_gpt2 = pipeline('text-generation', model='gpt2')

# Function to get answer from GPT-Neo
def get_gpt_neo_answer(question):
    generated_text = generator_neo(question, max_length=100, num_return_sequences=1)
    return generated_text[0]['generated_text']

# Function to get answer from GPT-2
def get_gpt2_answer(question):
    generated_text = generator_gpt2(question, max_length=100, num_return_sequences=1)
    return generated_text[0]['generated_text']

# Function to compare answers from both models
def compare_answers(question):
    answer_gpt_neo = get_gpt_neo_answer(question)
    answer_gpt2 = get_gpt2_answer(question)
    
    print("GPT-Neo Answer:", answer_gpt_neo)
    print("GPT-2 Answer:", answer_gpt2)
    
    if answer_gpt_neo == answer_gpt2:
        summary = "Both models provided the same answer."
    else:
        summary = "The answers are different."
    
    print("Summary:", summary)
    
    return {
        "question": question,
        "gpt_neo_answer": answer_gpt_neo,
        "gpt2_answer": answer_gpt2,
        "summary": summary
    }


# Run the comparison with a sample question
question = "What is an internship?"
result = compare_answers(question)
print("Comparison Result:")
for key, value in result.items():
    print(f"{key}: {value}")
```

### Comparison Result:
```
GPT-Neo Answer: 
What is an internship?

An internship is a job that is offered by various institutions for students who want to get some extra hands on experience. The internship is a form of work experience, but it is offered to students who wish to pursue an area that they are interested in.

What are the requirements for an internship?

Internships come with certain requirements as well as stipulations for which students are expected to comply. Some of the stipulations include the following:


GPT-2 Answer: 
What is an internship?

An internship is a chance to learn new skills and provide new experiences.
An internship can be defined as providing new experiences in an unpaid role.
An internship lasts for three months and costs $80.
How do I find more information about internships?
Find out more about internships and how you can apply.


Summary: The answers are different.
```


### Conclusion:
In this experiment, we compared the responses of two different language models, GPT-Neo and GPT-2, to the same input question. The results showed that the models provided different answers, which indicates that each model has its unique way of generating text based on its training data and architecture. GPT-Neo provided general information with well sentence structure, while GPT-2 delivered a more concise, straightforward response. This indicates that each model has unique strengths and approaches to generating text, making them suitable for different use cases.
