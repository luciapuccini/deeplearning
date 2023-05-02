# Deeplearning
Prompt Engineering for Developers

# Principles for prompts
## 1. Write clear and specific instructions
### Use delimiters
Can be anything like:
 - quotes """
 - backticks """
 - dashes: ---
 - angle brackets <>
 - XML tags: <> </>

 Example:
 > Summaryze the text delimited by triple quotes into a single sentece. """{text}"""

### Ask for structured output 
> Generate a list of three made-up book titles along 
with their authors and genres. 
Provide them in JSON format with the following keys: 
book_id, title, author, genre.

### check wheather conditions are satisfied
> You will be provided with text delimited by triple quotes. 
> If it contains a sequence of instructions,  
> re-write those instructions in the following format:
> Step 1 - ...
> Step 2 - …
> …
> Step N - …
>If the text does not contain a sequence of instructions,  
> then simply write \"No steps provided.\"
> \"\"\"{text_1}\"\"\"

### Few-shot propmpting
  give successful examples of completing task and then ask to perform task
> Your task is to answer in a consistent style.

> < child >: Teach me about patience.

> < grandparent >: The river that carves the deepest valley flows from a modest spring; the  grandest symphony originates from a single note; the most intricate tapestry begins with a solitary thread.

> < child >: Teach me about resilience.

## 2. Give the model time to think
Chan of reasoning so that it gives more computational time so that the model doesn't "guess"  

###  Specify the steps required to complete a task
>Perform the following actions: 
>1 - Summarize the following text delimited by triple 
>backticks with 1 sentence.

>2 - Translate the summary into French.

>3 - List each name in the French summary.

>4 - Output a json object that contains the following 
>keys: french_summary, num_names.

>Separate your answers with line breaks.

>Text:
> """{text}"""

## Instruct the model to work out its own solution before rushing to a conclusion

>Your task is to determine if the student's solution is correct or not.
>To solve the problem do the following:

>First, work out your own solution to the problem. 
>Then compare your solution to the student's solution and evaluate if the student's solution is correct or not.  Don't decide if the student's solution is correct until  you have done the problem yourself.

> Use the following format: Question: """question here""

> Student's solution:"""student's solution here"""

> Actual solution:"""steps to work out the solution and your solution here """

> Is the student's solution the same as actual solution just calculated: """yes or no"""


## Model Limitations: Hallucinations
The model doesn't know the boundries of its knowledge, so it can make up some solutions.
This can be dangerous because the responses sound realistics
One aditional tatic to reduce hallucinations is to ask first to find relevant information and then answer based on that.