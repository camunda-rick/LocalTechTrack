# Camunda Local Tech Track
Starter project to create your own Agent for Camunda local 2025-H2

# Technical Pre-requisites
1. Cluster 8.8.0 (and above)
2. Model provider (e.g. AWS Bedrock, Anthropic, Open AI compatible) and corresponding secrets

# Steps to run the agent
1. Import the sources from the starterProject into your Camunda webmodeler and deploy. Click Run and you're good to go.

Note: the agent is ready-to-use with a simple calculate step. Below are the steps to integrate a new REST tool as well as displaying the results via a user form

# Adding a tool to the Agent's toolbox
1. Add a task and select the REST outbound connector [template](https://docs.camunda.io/docs/components/connectors/protocol/rest/)
2. Add documentation to the task to explain to the agent what it will be doing
3. For this example we'll be calling this publically available [joke API](https://jokeapi.dev/). Add the properly formatted URL as a feel expression to the connector e.g: `"https://v2.jokeapi.dev/joke/" + userTopic + "?safe-mode&type=twopart"`
4. Add a variable mapping to the result expression field e.g. : 
`{"toolCallResult": {"setup": response.body.setup, "delivery": response.body.delivery}}`

# (Optional) Adding a User task to display the result
1. Add a user task after the agent toolbox
2. Set input variables to be displayed. e.g.:
* **setup** = toolCallResults[1].content.setup
* **delivery** = toolCallResults[1].content.delivery
3. Create a form and link it to the task. Have the form display the **delivery** and **setup** variables



