



### [How Long Contexts Fail](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html)

##### Managing Your Context is the Key to Successful Agents

* [Context Poisoning: When a hallucination makes it into the context](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html#context-poisoning)

  *Context Poisoning is when a hallucination or other error makes it into the context, where it is repeatedly referenced.*
* [Context Distraction: When the context overwhelms the training](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html#context-distraction)

  *Context Distraction is when a context grows so long that the model over-focuses on the context, neglecting what it learned during training.*
* [Context Confusion: When superfluous context influences the response](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html#context-confusion)

  *Context Confusion is when superfluous content in the context is used by the model to generate a low-quality response.*
* [Context Clash: When parts of the context disagree](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html#context-clash)

  *Context Clash is when you accrue new information and tools in your context that conflicts with other information in the context*


# [How to Fix Your Context](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html)

##### Context Management Tactics

* [**RAG:** Selectively adding relevant information to help the LLM generate a better response](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#rag)
* [**Tool Loadout:** Selecting only relevant tool definitions to add to your context](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#tool-loadout)
* [**Context Quarantine:** Isolating contexts in their own dedicated threads](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#context-quarantine)
* [**Context Pruning:** Removing irrelevant or otherwise unneeded information from the context](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#context-pruning)
* [**Context Summarization:** Boiling down an accrued context into a condensed summary](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#context-summarization)
* [**Context Offloading:** Storing information outside the LLM&#39;s context, usually via a tool that stores and manages the data](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#context-offloading)


Reference:

- https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html
