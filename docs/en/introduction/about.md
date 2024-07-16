# Introduction to KWeaver

## About KWeaver

KWeaver is a cognitive intelligence framework based on Large Language Models and Knowledge Networks. It supports the integration of various large language models and enables prompt development based on these models. It allows the creation of knowledge networks that include knowledge graphs, taxonomies, and lexicons in a visual manner. Using these two technologies, developers can quickly build various AI applications, such as intelligent Q&A, intelligent dialogue, intelligent recommendations, and more.

> **What is a Knowledge Network?**
> A knowledge network is a collection of knowledge representation methods, including knowledge graphs, taxonomies, and lexicons. Knowledge networks can be used to build various AI applications, such as intelligent Q&A, intelligent dialogue, and intelligent recommendations.
>
> **What is the role of a Knowledge Network in LLM applications?**
> A knowledge network can serve as a knowledge base for LLMs, enhancing their knowledge representation capabilities. [GraphRAG](https://github.com/microsoft/graphrag) is a typical example of using knowledge graphs for knowledge enhancement. Large models can access more knowledge through knowledge networks, improving their capabilities in dialogue, Q&A, recommendations, and more.

## KWeaver includes the following features

+ **Knowledge Network Creation and Management**
  + **Knowledge Graph:** Supports the visual creation of knowledge graph ontologies and integration with various structured databases. It supports visual display and querying of knowledge graphs, as well as real-time or scheduled knowledge graph construction tasks.
  + **Taxonomy:** Also known as Taxonomy, supports the visual creation of taxonomies, with capabilities for visual display, querying, and exporting.
  + **Lexicon:** Supports importing and exporting lexicons, and allows the creation of lexicons using synonyms and entity linking.

+ **Model Factory**
  + **Large Model Integration:** Supports the integration of various large language models, such as GPT-4, Llama3, Qwen, Baichuan, etc., through OpenAI-like APIs.
  + **Prompt Application:** Supports prompt development based on large models, allowing visual creation of prompts, selection of model parameters, and prompt debugging, and finally publishing as a service.
  + **Prompt Templates:** Supports the creation of prompt templates. The difference between prompt templates and prompt applications is that in actual development, prompt templates and parameters are used, but external services are not provided. Instead, external large model services are used.

+ **Agent Factory (Under Development)**
  + **Agent Development:** Visual Agent development, supporting types such as ReAct and Tool Use. It includes built-in tools like GraphQA, Text2SQL, and Text2API. Users can also develop their own tools for integration.
  + **Agent Debugging:** Supports Agent debugging, including log monitoring and large model output.
  + **Agent Deployment:** Supports Agent deployment, monitoring, and logging.

## KWeaver has the following features

+ Easy Deployment: KWeaver adopts full containerized deployment, allowing users to quickly deploy locally or on the cloud.
+ Usability: KWeaver provides easy-to-use APIs, allowing users to get started quickly.
+ Flexibility: KWeaver offers a rich set of functional modules, allowing users to choose according to their needs.
+ Rich Documentation: KWeaver provides comprehensive documentation, including API documentation, tutorials, examples, and more.
+ Open Source License: KWeaver follows the Apache 2.0 license, allowing users to use and modify the code for free.
+ Community Support: The KWeaver community provides technical support, including user forums, developer forums, WeChat groups, and more.

## Future Plans

KWeaver is currently in development, with future improvements focusing on large model integration, knowledge network construction, and Agent development. We welcome everyone to follow KWeaver and participate in its development!