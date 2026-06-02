# Lab 8 - Use Foundry

Let's investigate our deployment in the Foundry portal.  

1. Open [https://ai.azure.com/](https://ai.azure.com/).
2. Click "Start building" in the upper right.

![](images/01.png)

Dismiss the dialog.

![](images/02.png)

You should see the project that our deploy script created.  In this case it is proj-foundry-neo4j-demo.  

Select your project.

![](images/03.png)

Click "Create agents."

![](images/04.png)

Enter the name "neo4j-research-agent"

![](images/05.png)

Click "Create."

![](images/06.png)

That will take a moment to run.

![](images/07.png)

For instructions enter:

    Role: investment research analyst. Source of truth: a Neo4j knowledge graph
    reached only through the get-schema and read-cypher tools (read-only). Be
    thorough and data-driven — cross-reference company data with news,
    relationships, and people.

    ## Workflows

    Company research: profile the company → fetch peers in its industry →
    fetch its relationships and people → fetch news mentions → synthesise.

    Industry analysis: list industries → companies in the chosen category →
    cross-org relationships across the leaders → industry news → synthesise.

    News-driven: articles by date or mentions → profile each mentioned company
    → relationships across them → synthesise.

    Always project `id` properties (e.g. `o.id AS company_id`) so follow-up
    questions can build on them.

    ## Output

    Cite every company_id and article_id. Use tables when comparing multiple
    entities, bullet lists for attributes of a single entity. Connect the dots
    — highlight patterns, anomalies, network position, sentiment trends.

    ## Grounding

    Call get-schema once per conversation. You MUST call read-cypher before any
    factual claim about a company, person, industry, location, or article.
    get-schema alone is not data. Answer only from read-cypher rows. Never use
    prior knowledge. If read-cypher returns nothing, reply "the graph doesn't
    contain that". Use modern Cypher (`WHERE x IS NOT NULL`).`

![](images/08.png)

Now under tools click "Add."

![](images/09.png)

Click "Browse all tools."

![](images/10.png)

Click "Custom."

![](images/11.png)

Click "Model Context Protocol (MCP)"

![](images/12.png)

Click "Create."

![](images/13.png)

We're going to need to fill out these values.

* Name - neo4j-mcp
* Remote MCP Server endpoint - value from last lab (note if you don't have this, you can open your Cloud Shell and run cat neo4j-agent-integrations/microsoft-foundry/.env to get it)
* Authentication - Key based

![](images/14.png)

For the key/value pair, enter the values:

* Authorization
* Basic Y29tcGFuaWVzOmNvbXBhbmllcw==

![](images/15.png)

Click "Connect."

![](images/16.png)

Let's remove the web search.  That way the agent will only use the MCP server for grounding.  To do so click the three dots next to web search.

![](images/17.png)

Click "Remove."

![](images/18.png)

Now let's try our agent.  In the "Message the agent..." field type:

    Tell me about Microsoft — what industry it competes in, who runs it, and where it's headquartered.

![](images/19.png)

Hit enter.

![](images/20.png)

Click "Approve."

![](images/21.png)

Click "Always approve this tool."

![](images/22.png)

Click "Approve."

![](images/23.png)

Click "Always approve this tool."

![](images/24.png)

That gives this result.

![](images/25.png)

Now let's try a different command:

    Find three companies that compete in the same industry as Microsoft.

![](images/26.png)

Here's another command to try:

    What recent articles mention Microsoft, and what topics do they cover?

![](images/27.png)

Feel free to explore and try your own ideas too!
