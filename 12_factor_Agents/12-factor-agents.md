

I have made a draft learning of [12-factor-agents](https://github.com/humanlayer/12-factor-agents) to make the learning fast and effecient.

* [Factor 1: Natural Language to Tool Calls](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-01-natural-language-to-tool-calls.md)

  One of the most common patterns in agent building is to convert natural language to structured tool calls. This is a powerful pattern that allows you to build agents that can reason about tasks and execute them.

  Natural language input will be converted to any format like json or single string for tool calling input for external data extraction.
* [Factor 2: Own your prompts](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-02-own-your-prompts.md)

  Your prompts are the primary interface between your application logic and the LLM.

  Key benefits of owning your prompts:

  1. **Full Control** : Write exactly the instructions your agent needs, no black box abstractions
  2. **Testing and Evals** : Build tests and evals for your prompts just like you would for any other code
  3. **Iteration** : Quickly modify prompts based on real-world performance
  4. **Transparency** : Know exactly what instructions your agent is working with
  5. **Role Hacking** : take advantage of APIs that support nonstandard usage of user/assistant roles - for example, the now-deprecated non-chat flavor of OpenAI "completions" API. This includes some so-called "model gaslighting" techniques

  Having full control over your prompts gives you the flexibility and prompt control you need for production-grade agents.
* [Factor 3: Own your context window](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-03-own-your-context-window.md)
* [Factor 4: Tools are just structured outputs](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-04-tools-are-structured-outputs.md)
* [Factor 5: Unify execution state and business state](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-05-unify-execution-state.md)
* [Factor 6: Launch/Pause/Resume with simple APIs](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-06-launch-pause-resume.md)
* [Factor 7: Contact humans with tool calls](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-07-contact-humans-with-tools.md)
* [Factor 8: Own your control flow](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-08-own-your-control-flow.md)
* [Factor 9: Compact Errors into Context Window](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-09-compact-errors.md)
* [Factor 10: Small, Focused Agents](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-10-small-focused-agents.md)
* [Factor 11: Trigger from anywhere, meet users where they are](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-11-trigger-from-anywhere.md)
* [Factor 12: Make your agent a stateless reducer](https://github.com/humanlayer/12-factor-agents/blob/main/content/factor-12-stateless-reducer.md)

References:

* https://github.com/humanlayer/12-factor-agents
