# RAG-retrieval-augmented-generation-using-book-catalogs



The purpose is to augment the xLLM system introduced in section 7.2.2, with external input data consisting of
books. The focus is still on one particular sub-LLM: the “probability & statistics” category, initially built on the
Wolfram crawl. The additional input (the books) leads to an alternate taxonomy, complementing sub-categories
that don’t have much coverage in Wolfram, such as “Bayesian analysis”. The alternate taxonomy based on the
books may lead to a separate sub-LLM, or used for fusion with the existing one built earlier. Other input
sources to augment the back-end tables include the metadata attached to crawled documents, and the front-end
user prompts. For more on LLM fusion, see [37].
In the process, I also create a synonyms table built on glossaries and other structure found in the books, to
further enhance output results to user prompts. Then, I introduce double-tokens and scores: the latter measures
the relevancy of the results returned to the user, for a specific query. Finally, I further investigate self-tuning,
a better alternative to standard LLM evaluation metrics described in [30].
The project consists of the following steps:
Step 1: xLLM pluses and minuses. The benefits of xLLM are listed and contrasted to standard LLMs
in appendix C.3. What are the potential negatives?
Step 2: Data augmentation. How to incorporate additional input sources such as PDFs? In short,
explain how to reconstruct the underlying taxonomy of a PDF repository, and blend the augmented data
with the existing summary tables built in Step 1 in project 7.2.2. What other sources could be used?
The LATEX sources of my books are on GitHub, here. The PDF version of this document can be found
here. In these documents, what elements would you use to create / update the summary tables such as
categories or embeddings? These additional input sources (PDFs and so on) are referred to as augmented
data, corresponding to the letter A in the RAG architecture (retrieval-augmentation-generation).
Step 3: Scoring, evaluation, self-tuning. The results displayed to the user, broken down per section
(URLs, categories, tokens, related items and so on as in Figure C.1) are sorted according to relevancy:
see the numbers on the left column, attached to each item in Figure C.1. Lines 131-147 in the Python
script xllm5 short.py at the end of this section, take care of this.
How to create a global quality score attached to the output displayed to the user, based on the various
relevancy scores assigned to each returned item? How do you weight the various sources (original crawl,
augmented data such as PDFs)? Finally, if you allow the user to play with the hyperparameters (see
Step 5 in project 7.2.2), you can deliver customized results: two users with the same query get different
outputs. Discuss the challenges of creating a universal evaluation metric to compare various LLMs such
as OpenAI, Mistral, Claude, xLLM and so on. How would you identify the optimum set of parameters
and set it as default, based on user preferences? That is, based on the individual favorite hyperparameter
sets selected by the users.
Step 4: Enhancements. Some queries such as “Bayes” or “Anova” return very little, while “Bayesian”
or “analysis of variance” return a lot more. How to address this issue? How do you improve or build
a good stopwords list for a specific top category? Finally, what are the benefits of double tokens such
as “Gaussian+distribution”, in addition to the simple tokens “Gaussian” and “distribution”? How to
implement double tokens in embeddings and other tables?
Step 5: Combining multiple specialized LLMs. How do you manage multiple LLMs, one per top
category? The solution here is known as multi-agent system.
