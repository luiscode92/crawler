# crawler
 The following are the tools that I used to build this prototype

 - Semantic search
 - Embeddings
 - Faiss
 - hugginface's transformes
 - gpt-3
 - a .csv dataset (for individuals)

# Summary
The Crawler is a matching system for candidate and job offers, for that 
I thought that We could use semantic search to capture the context of a job post and then match that context to relevant Cvs from a dataset

for the scope of this prototype, and aa first development step, I focused on based on a jod¿b offer description to get the most relevant (high-ranked) resumes from a “raw” Job post. That would us alot.

# The dataset
To start processing the resumes, we need to load the data in CSV format into a Huggingface Dataset object.

the strcuture goes like:

1 — Extract the embedding vector of all our resumes using a pre-trained model from Huggingfaces.
acording to teh documentation "sentence-transformers/multi-qa-mpnet-base-dot-v1" performs a great semantic search, now we take ethe embedded vector and adding to a new column call "embeddings"

2 — Store the embedding vectors in Faiss.
  we add a Faiss index to the new embeddings column.

3 — Extract the embedding vector of a job post.
Given a jod_description/question we can match candidate using Semantic search, then extract the embeddings of that job post.

4 — Query the Faiss index using the embedding vector of the job post.
Now we can search the index to find the X resumes most similar to the job post.

5- Uuse using Pandas to sort and show the query result.


# Next Steps

1. We have a dataset od job offers provided by Torre, so we need to connect our crawler to that job post provider. which is in aws
2. tune the model to be able to address adge cases like:
  - Only remote jobs
  - update job offers
  among other
3. figure it out who to make it cheaper as possible, and solid as possible
4. probably create some UI
5 deploy everything



