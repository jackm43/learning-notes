

> Domain: `{{domain}}`  
> Related topic(s): [[topics/{{topic-name}}]]  
> Date started: 18-04-2025
> Status: `in-progress`

---

## goal or objective
- How to fine-tune a pre-trained model.

---

## setup / tools used
- Environment:  
  - OS / Hardware / Notebook / IDE / etc.
- Tools / Materials:
  - 
- Resources referenced:
  - [ ] [[pipelines]]
  - [ ] https://huggingface.co/learn/llm-course/en/chapter1/3
  - [ ] https://github.com/huggingface/notebooks/blob/main/transformers_doc/en/preprocessing.ipynb

---

## steps taken / experiment log
Break down what you did or tried, step-by-step, day-by-day, or section-by-section.
`/mnt/chatting/projects/jakbot/notebooks` / github.com/jackm43/jakbot

1. Finished parser for fb + discord
2. Generated with and without labels, and with and without the names of people in DMs.
3. First go was with people in DM's, the chatbot would find specific stuff in the dataset.
4. Originally setup the huggingface tutorial model
5. Moved to gpt2
6. Learned about pickling
7. I try different model now.
8. Was mostly just having a crack at trying different attemts and my own preprocessing and data input experimentation.
9. Will look for open source now - first up `data-prep-toolkit-transforms[all]`
10. What I kept having todo:
	1. Removing exact msg dupes
	2. Removing / categorising URLs and emojis
	3. Running sentiment analysis 
	4. Implementing random stopwords
	5. Filtering shit slowly