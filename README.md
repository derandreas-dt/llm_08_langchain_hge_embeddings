This version uses the HuggingFaceBgeEmbeddings with the BAAI/bge sentence transformer.
With this the embeddings are better interpreted and stored (using ChromaDB again).

The results could improve by using this as the LLM can work with better
vectorized data in the embedding store.

To make the HuggingFaceBgeEmbeddings work, you need to install

`pip install sentence-transformers`

For testing this, the plain LLM is asked for the CEO of Twitter.
In the next example, the RetrievalQA is used, with two additional texts:
    1. Elon Musk is new CEO
    2. Lina Yaccarino is new CEO

One text is english and one is german.

The reults are:

```
Anwer without langchain embeddings to the question: Who is CEO of twitter?
First, we need to determine who the current CEO of Twitter is. To do this, we can
check Twitter's official website or social media accounts for an update on their
leadership team. As of my knowledge cutoff in December 2022, the CEO of Twitter is
Jack Dorsey. However, it's important to note that Twitter's leadership may change
over time, so this information could be outdated.
Context: The user is asking about the current CEO of Twitter, and you are providing
an answer based on your knowledge cutoff in December 2022.

Answer with Langchain embeddings to the question Who is CEO of twitter?
On 01.07.2023, Elon Musk announced that Linda Yaccarino would be the new CEO of Twitter.
So, the answer to your question is Linda Yaccarino.
```

With the normal LLamaCppEmbeddings, the order of the "news texts" were important.
This time, the order is swapped, so the announcement of Musk is the second text,
which could be identified as "newer". So swapping this, could not be better

Results (swapping text_1, text_2 variable names):

```
Anwer without langchain embeddings to the question: Who is CEO of twitter?
1. Check Twitter's official website or Twitter account for the most up-to-date information on the CEO.
2. Search online for recent news articles or press releases about Twitter's leadership team.
3. If you are still unsure, try reaching out to Twitter's customer support team for more information.

Unsure about answer. Can you provide more context or clarify the question?

Answer with Langchain embeddings to the question Who is CEO of twitter?
As of 01.10.2022, Elon Musk was the new CEO of Twitter. However, as of 01.07.2023, Linda Yaccarino became the new CEO of Twitter. So, the answer is Linda Yaccarino.
Context: The given text is about Elon Musk becoming the new CEO of Twitter and then Linda Yaccarino replacing him as the new CEO.
```

Great!
