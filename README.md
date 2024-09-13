### Agentic RAG Lightboard

A quick refresher on what Retrieval-Augemented Generation is:

Retrieval-Augmented Generation (RAG) is a powerful and popular pipeline that enhances responses from a Large Language Model (an LLM) by incorporating relevant data retrieved from a vector database, which is added to the prompt and sent to the LLM for generation. What this does, is  allows the LLM to ground its response in concrete and accurate information, which improves the quality and reliability of the response.

(I will quickly sketch this out to explain)

A user makes a query, which is then sent to our vector database, and the result from the db is added as context to the prompt, which is sent to the LLM to generate a response.

![simple_rag](./imgs/Simple_RAG.png)


In a typical RAG pipeline, we call the LLM once and use it solely to generate a response. But what if we could leverage the LLM to perform additional tasks, like deciding which vector database to query or determining the type of response to give?

This is where the Agentic RAG pipeline comes into play. In Agentic RAG, the LLM goes beyond just generating a response. It takes on an active role, and can make decisions that will improve both the relevance and accuracy of the retrieved data.

Let’s revisit our initial RAG pipeline example, but this time, let’s introduce an agent into the mix. In the initial RAG pipeline, we simply retrieved data from a single source and used it to augment the LLM’s output. Now, let’s explore how we can augment that initial process with an Agent and a couple of different sources of data.

Imagine we have two vector databases:

One for storing internal company documentation - things like policies, procedures, and guidelines

Another containing general industry knowledge - best practices, industry standards, and public resources.

![two_vbs](./imgs/two_vbs.png)

So how can we get the LLM to use the vector db that contains the data that will be most relevant to the query?

With an Agent in the pipeline, it can intelligently decide which Database to query from based on the users question. 

![agent_flow](./imgs/agent_flow.png) 

If an employee asks "What is the company's policy on remote work during the holidays?" the agent can direct this question to the internal company database.

But if the question is more general, like "What are the industry standards for remote work in tech companies?" the agent will query the industry knowledge database.


The agent isn't just making a random guess, it's using NLP techniques to analyze the query and to understand its context. So, if the query contains keywords like 'policy' or 'company,' the agent, which is powered by an LLM, will send the query to the internal database, but if it sees terms like 'industry standards' or 'best practices,' it goes to the industry knowledge database.

And lets say the query is totally out of left field, and has nothing to do with the data in either of our vector dbs, we can have a failsafe. So if the query is something like "How to tell if my cat is conspiring against me?" the agent can route to a canned response saying, "sorry, I do not have the information you are looking for." 

![sorry](./imgs/sorry.png) 
 
This Agentic RAG pipeline can be used for customer support systems. It can be used for Legal tech, where a lawyer can source answers to their questions from internal briefs from one query, and public case law databases from another.

The Agent can be used in a ton of different ways. Agentic RAG is an evolution in how we can enhance the RAG pipeline, by going beyond simple response generation to more intelligent decision-making. Allowing an agent to choose the best data sources and then even incorporate external information when needed, we can create a pipeline that's more responsive, accurate, and adaptable. This approach opens up so manyh possibilities for applications in customer service, legal tech, healthcare, anything really. As the tech continue to evolve, we will see AI systems that truly understand context and can deliver amazing value to end-users.
