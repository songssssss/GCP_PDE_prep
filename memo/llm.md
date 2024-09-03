#### Result
Flan-t5-base: screened on the whole dataset (12,895) 20% mismatched (2,636)
Flan-t5-large: 677 mismatched
#### Improvements
Perform cleaning on the principle business activities.
Discard records of business nature with vague definitions (something related to investments)


Clean the principle business activities

elarborate abbreviations into sentences
eg. Prospect → The company
Tried different prompts


Split the question answering task into two small task as the model accept only 512 tokens

Summarize & Yes/no question
