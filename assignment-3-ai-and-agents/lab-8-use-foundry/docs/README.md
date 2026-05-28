# Lab 8 - Use Foundry

Let's investigate our deployment in the Foundry portal.  

1. Open [https://ai.azure.com/](https://ai.azure.com/).
2. Click "Sign in" in the upper right.

![](images/01.png)

Select your project.

![](images/02.png)

You should see the project that our deploy script created.  In this case it is proj-foundry-neo4j-demo.  

Note that "Create agents" is grayed out.  That is because a role is disabled.  Click the slider by "New Foundry" to go back to the previous UI version.

![](images/03.png)

Click "Continue without feedback."

![](images/04.png)

Click "Agents" in the left menu.

![](images/05.png)

Click "Fix Me" to fix the role.

![](images/06.png)

Click "X" to close the menu once it says it is fixed.

![](images/07.png)

Click "New agent."

![](images/08.png)

Click "Create new agent."

![](images/09.png)

If you've done this quickly, you may see an error that "You don't have permission to build agents in this project."  You can try refreshing or waiting for it to go away.

![](images/10.png)

Once the screen loads properly you should see the following.  Click "Create agent."

![](images/11.png)

Enter the name "neo4j-research-agent"

![](images/12.png)

Click "Create and open playground."

![](images/13.png)

That will take a moment to run.

![](images/14.png)

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

![](images/15.png)

Now under tools click "Add."

![](images/16.png)

Click "Browse all tools."

![](images/17.png)

Click "Custom."

![](images/18.png)

Click "Model Context Protocol (MCP)"

![](images/19.png)

Click "Create."

![](images/20.png)

We're going to need to fill out these values.

* Name - neo4j-mcp
* Remote MCP Server endpoint - value from last lab (note if you don't have this, you can open your Cloud Shell and run cat neo4j-agent-integrations/microsoft-foundry/.env to get it)
* Authentication - Key based

![](images/21.png)

For the key/value pair, enter the values:

* Authorization
* Basic Y29tcGFuaWVzOmNvbXBhbmllcw==

![](images/22.png)

Click "Connect."

![](images/23.png)

In the "Message the agent..." field type:

    Tell me about Microsoft — what industry it competes in, who runs it, and where it's headquartered.

![](images/24.png)

Hit enter.

![](images/25.png)

Click "Approve."

![](images/26.png)

Click "Always approve this tool."

![](images/27.png)

That gives this result.

![](images/28.png)

Now let's try a different command:

    Find three companies that compete in the same industry as Microsoft.

![](images/29.png)

Here's another command to try:

    What recent articles mention Microsoft, and what topics do they cover?

![](images/30.png)

It does appear the agent is using data from Bing, not just the database underlying the MCP server.  We can try to avoid that in two ways:

1. Disable Bing in the Foundry UI
2. Modify the prompt, adding text such as:

    You must ONLY answer using the provided knowledge sources.
    If the answer is not found in the retrieved data:
    * Respond with: "I don't know based on available data."
    * Do NOT use prior knowledge
    * Do NOT infer or guess
    Always cite the source used.

Feel free to explore and try your own ideas too!



