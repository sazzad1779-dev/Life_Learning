
### **Context Engineering**

Context Engineering is the discipline of designing, building, and optimizing the dynamic information ecosystem provided to an AI model to perform a task. 

This engineered context is a composite of multiple information streams, including but not limited to:

* **Instructions**: The system prompt that defines the LLM's persona, rules, and high-level objectives.
* **User Input:** The immediate query or task from the user.
* **Memory**: This includes both short-term memory, such as the history of the current dialogue, and long-term memory, like stored user preferences or facts learned in previous sessions.
* **Retrieved Knowledge**: Documents and data retrieved from external knowledge bases via Retrieval-Augmented Generation (RAG) to ground the model in factual, up-to-date, or proprietary information.
* **Tool Definitions and Outputs**: Schemas describing available external tools (e.g., APIs for weather, stock prices, or internal databases) and the data returned from their execution.
* **Output Constraints**: Instructions that specify the desired format of the output, such as a JSON schema or a specific structured layout.
* **Agentic State**: For autonomous agents, this includes the current plan, intermediate "thoughts" or reasoning steps stored in a scratchpad, and the overall state of the task workflow.

#### **The "Context-as-a-Compiler" Analogy**


#### **Deterministic vs. Probabilistic Context**


* Deterministic Context refers to all static, controlled, and predictable inputs provided to the LLM. This includes the system prompt, user-uploaded documents, few-shot examples, and hard-coded rules or instructions. Most traditional prompt engineering techniques are focused on optimizing this deterministic portion of the context for clarity, efficiency, and cost (e.g., token usage).
* Probabilistic Context  **encompasses all dynamic, external, and inherently uncertain information sources that the LLM can access** . This primarily includes results from web searches or queries against large, evolving internal databases. When an agent is given access to the internet, this probabilistic context can overwhelm the deterministic inputs due to its sheer volume and variability.

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

### [How to Fix Your Context](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html)

##### Context Management Tactics

* [**RAG:** Selectively adding relevant information to help the LLM generate a better response](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#rag)
* [**Tool Loadout:** Selecting only relevant tool definitions to add to your context](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#tool-loadout)
* [**Context Quarantine:** Isolating contexts in their own dedicated threads](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#context-quarantine)
* [**Context Pruning:** Removing irrelevant or otherwise unneeded information from the context](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#context-pruning)
* [**Context Summarization:** Boiling down an accrued context into a condensed summary](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#context-summarization)
* [**Context Offloading:** Storing information outside the LLM&#39;s context, usually via a tool that stores and manages the data](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html#context-offloading)

Reference:

- https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html
- https://www.sundeepteki.org/blog/context-engineering-a-framework-for-robust-generative-ai-systems
