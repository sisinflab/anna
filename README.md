# Anna

## Anna: a Virtual Assistant to interact with the Puglia Digital Library

In the last years, a huge amount of data has been released by private and public bodies as Linked Open Data. By their inner nature,  these data contain rich semantic information that can be automatically processed by software agents and explored by humans via visual tools or structured SPARQL queries. Although they result useful for many tasks, these latter approaches miss the simplicity of the interfaces based on interactions via natural language implemented in modern virtual assistants. 
In this paper, we present a system able to assist the user in exploring the knowledge exposed by the \textit{Puglia Digital Library} containing information and data associated with digital goods related to the Apulia region in Italy. We show how to interact with the Digital Library by means of a virtual assistant and how, thanks to its publication as Linked Open Data, it is possible to easily integrate it on-the-fly with external knowledge sources such as geographical ones.  

In 2012, Google announced its [Knowledge Graph](https://googleblog.blogspot.it/2012/05/introducing-knowledge-graph-things-not.html) as a new tool to improve the identification and retrieval of entities in return to a search query. Most of the knowledge encoded in Google Knowledge Graph originally came from Freebase which was a crowd-sourced effort to create a base of facts in all possible knowledge domains. Alongside with the development of the above-mentioned initiatives, following the original idea of a Semantic Web, new technologies have been developed and released with the aim of embedding structured knowledge with unambiguous semantics into Web pages in order to allow software agents to consume and elaborate information in an automated way. 
In this paper, we report the experience in making accessible the [Puglia Digital Library](http://www.pugliadigitallibrary.it/) (PDL) through _Anna_: a virtual assistant able to explore the knowledge graph behind PDL via natural language-based interactions. 

 In the proposed approach, speech recognition is delegated to Google Assistant, whereas [Dialogflow](https://dialogflow.com/) is adopted to manage the interaction with the user. 


## Reference
If you publish research that uses Anna please use:
~~~
This work is currently Under Review
~~~
The full paper describing the overall approach WILL BE available here [PDF](link)

## Architecture and Intents Overview
The software ecosystem behind the chatbot Anna is depicted in Figure 1. 

![Figure 1: Architecture](https://github.com/vitowalteranelli/anna/blob/master/architecture/architecture1.png)

The first step to create Anna consisted of creating a SPARQL endpoint to retrieve information from the PDL knowledge base in an effective way.  
A Virtuoso server instance was created with a SPARQL 1.1 endpoint that allows humans, and automated agents to query the underlying Knowledge Graph using SPARQL queries. Differently from SQL queries, SPARQL is based on the idea of graph matching.
SPARQL query language lets the user express a graph pattern (in which one or more parts of the triple are substituted by variables), to retrieve the necessary knowledge. 

The user can interact with the system using a Web browser or a mobile phone with the Italian Google Assistant. The Web App was implemented in _node.js_ and deployed on a specific server. The Google Assistant is an _Actions on Google_ project that enables users to interact with _DialogFlow_, converting the speech to text. 
The Web App copes with the communication protocol adopted by Google Assistant to provide a unified communication protocol. 
The DialogFlow module handles the conversation itself: each interaction moves the conversation from a state to another, called contexts, in which a specific choice is made by the user (intent). Contexts, and intents are at the core of the interaction mechanism and are depicted in Figure 2.

![Figure 2: Intents](https://github.com/vitowalteranelli/anna/blob/master/architecture/intents1.png)

The Webhook keeps the history of the iterative queries of the user, in order to refine the final query. If any further knowledge is required, the Webhook sends a message with the needed information to the Query Manager, which poses the query against the remote SPARQL endpoint. 
Finally, for the sake of privacy, the Webhook itself does not store any information, and once the session is terminated that specific user history is deleted.
In Figure 2 the most important intents are depicted. The directed rows show the outgoing contexts. Whenever the user operates a choice, her input is analyzed and the conversation is moved to a new context. Intents basically defines the usability of the tool, hence the intents'scheme was defined under the instructions of _Puglia Digital Library_ users, and managers. 


## Credits
This algorithm has been developed by Vito Walter Anelli and Joseph Trotta and Luca Riccardi while working at [SisInf Lab](http://sisinflab.poliba.it) under the supervision of Tommaso Di Noia.  

## Contacts

   Tommaso Di Noia, tommaso [dot] dinoia [at] poliba [dot] it  
   
   Vito Walter Anelli, vitowalter [dot] anelli [at] poliba [dot] it 
   
   Joseph Trotta, joseph [dot] trotta [at] poliba [dot] it 
