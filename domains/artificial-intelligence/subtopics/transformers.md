
## overview
Brief description of this subtopic.

---

## links to main topic
- [[domains/{{domain}}/topics/{{topic-name}}]]

---

## notes
- Writing in your own voice uses causal language modelling.
- Compared to matching my style of writing
- If I want to make decisions like me, I need **labels**. This needs **sequence classification**

- Wastes context to tokenize lines GPT-2 performs better in long chunks - 512 tokens
    
- Doesn’t allow the model to learn cross-line flow(???)
The training steps:
- **Input**
	- x amount of tokens as a stream - 512 for gpt2
		- For fine tuning here, to make it "like me", data was structured as
		- Name: msg
		- Included all participants of the chat
- **Model Forward Pass**: GPT2 uses **attention layers** to compute token predictions
- **Loss Calculation**: compares its prediction to the actual next token in the sequence using **cross entropy loss**
- **Backpropagation**: Adjusts model **weights**(Seems diff to params) for better training next time
	- What does this mean 
	- what does it look like 
	- how does it calculate it?
- **Repeat** for every chunk of 512 on all **epochs**

- **Post Training**
	- Almost like fine tuning your fine tune i guess
	- 1. Generate a chat completion with given params
	- 2. Refine:
		- **Temperature**: Creativity
		- **top_k**: Focus on top_10 most likely tokens in each **step**
		- **top_p**: Nucleus sampling ( cum probability ) (?????)
		- **max_length**: Max output tokens
		- **do_sample**: Always true if not a deterministic model


---

## questions
- How do I know if I should add 'text' and 'label' to my dataset?
- Whats a seed?
- What is SequenceClassification
- What is Hyperparameters
- What is a supervised/unsupervised model?
- Causal language modelling vs masked?
- What is an eos padding
- What is an epoch, is it just the concept of time? A model starts at "0" and the end of time is the time it takes to go through your dataset?



---

## 📎 resources
- https://stackoverflow.com/questions/76446228/setting-padding-token-as-eos-token-when-using-datacollatorforlanguagemodeling-fr


(e.g., complete messages, write in your voice)

Then you're looking to **fine-tune a language model** (like GPT, BERT-style models aren't meant for generation).

You'll need your data in a format like:
Jack: I think we should try a more elegant solution.
Jack: Can you give me a sec to look into that?
Jack: Here's what I propose...
Then you fine-tune a model like `GPT2` using these samples as the training corpus — no labels needed. You can format them as plain text or JSONL.

> This is called **causal language modeling**.


### 2. **Classify things like you?**

(e.g., detect whether you'd approve, or categorize messages)

Then you **do need labels** — this is a supervised task. You’d need to label some of your messages (manually or with a model), then fine-tune something like `bert-base-cased` on that.

> This is called **sequence classification**.

---

### 3. **Embed your writing style for similarity/search?**

(e.g., match messages to your vibe)

Then you might want to use a **sentence embedding model** (like `sentence-transformers`) and fine-tune it with **triplets** or **pairs** — which requires either labeled pairs or manual judgment of "similar vs different."

