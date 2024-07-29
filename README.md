# RAG-retrieval-augmented-generation-using-book-catalogs



The purpose is to augment the xLLM system introduced in section 7.2.2, with external input data consisting ofbooks.
The focus is still on one particular sub-LLM: the “probability & statistics” category, initially built on the Wolfram crawl. 
The additional input (the books) leads to an alternate taxonomy, complementing sub-categories that don’t have much coverage in Wolfram, such as “Bayesian analysis”. 
The alternate taxonomy based on the books may lead to a separate sub-LLM, or used for fusion with the existing one built earlier. 
Other input sources to augment the back-end tables include the metadata attached to crawled documents, and the front-end user prompts. 
implement double tokens in embeddings and other tables?
Step 5: Combining multiple specialized LLMs. How do you manage multiple LLMs, one per top
category? The solution here is known as multi-agent system.
