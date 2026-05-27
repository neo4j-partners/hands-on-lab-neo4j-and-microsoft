# Lab 8 - Use Foundry

Let's investigate our deployment in the Foundry portal.  

1. Open [https://ai.azure.com/](https://ai.azure.com/).
2. Click "Sign in" in the upper right.

![](images/01.png)

Dismiss the pop up.

![](images/02.png)

You should see the project that our deploy script created.  In this case it is proj-foundry-neo4j-demo.  Click on that project to open it.

![](images/03.png)

Click the slider by "New Foundry" to go back to the previous UI version.

![](images/04.png)

Click "Continue without feedback."

![](images/05.png)

Click "Agents" in the left menu.

![](images/06.png)

Click "Fix Me" to fix the role.

![](images/07.png)

Click "X" to close the menu once it says it is fixed.

![](images/08.png)

Click "New agent."

![](images/09.png)

Click "Create new agent."

![](images/10.png)

Enter the name "neo4j-research-agent"

![](images/11.png)

Click "Create."

![](images/12.png)

That will take a moment to run.

![](images/13.png)

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

![](images/14.png)

Now click "Add."

![](images/15.png)

Click "Browse all tools."

![](images/16.png)

Click "Custom."

![](images/17.png)

Click "Model Context Protocol (MCP)"

![](images/18.png)

Click "Create."

![](images/19.png)

We're going to need to fill out these values.

* Name - neo4j-mcp
* Remote MCP Server endpoint - value from last lab
* Authentication - Key based

![](images/20.png)

Then click "Add key value pair."

![](images/21.png)

For the key/value pair, enter the values:

* Authorization
* Basic Y29tcGFuaWVzOmNvbXBhbmllcw==

![](images/22.png)

Click "Connect."

![](images/23.png)

Click "Save."

![](images/24.png)

In the "Message the agent..." field type:

    Tell me about Microsoft — what industry it competes in, who runs it, and where it's headquartered.

![](images/25.png)

Hit enter.

![](images/26.png)

Now let's try a different command:

    Find three companies that compete in the same industry as Microsoft.

Here's another command to try:

    What recent articles mention Microsoft, and what topics do they cover?

Feel free to explore and try your own ideas too!