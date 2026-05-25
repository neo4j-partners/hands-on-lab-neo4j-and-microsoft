# Lab 7 - MCP Tool

Model Context Protocol (MCP) provides a standard interface for agents to speak with one another.  Neo4j has an open source [MCP server](https://github.com/neo4j/mcp).

Neo4j and Microsoft collaborated to build scripts exposing that MCP server in Microsoft Foundry.  Documentation on that is [here](https://neo4j.com/labs/genai-ecosystem/genai-frameworks/microsoft-foundry-mcp/).  The underlying code is [here](https://github.com/neo4j-labs/neo4j-agent-integrations/blob/main/microsoft-foundry/).

In this lab we'll use that.

To get started, open your [Azure Portal](https://portal.azure.com/).

Click the terminal icon in the top blue menu.  It is to the right of "Copilot."  That will open a cloud shell.

![](images/01.png)

Select "Bash."

![](images/02.png)

Click "Subscription."

![](images/03.png)

Select your subscription.  In this case it was "Neo4j Subscription 32."

![](images/04.png)

Click "Apply."

![](images/05.png)

The Cloud Shell then takes a moment to start.

![](images/06.png)

Click the arrow icon in the upper right of the Cloud Shell to expand it.

![](images/07.png)

Now we're going to clone a GitHub repo with the MCP Tool in it.  Run the command:

    git clone https://github.com/neo4j-labs/neo4j-agent-integrations.git

![](images/08.png)

Now let's cd into the Microsoft Foundry directory and see what we have in there.

    cd neo4j-agent-integrations
    cd microsoft-foundry/infra

![](images/09.png)

There's a login issue with the cloud shell.  To work around it we're going to login manually.  Do that with the command:

    azd auth login

![](images/10.png)

You'll see a code and a link.  Copy the code and open the link.  The link should open in a new tab.

![](images/11.png)

Paste the code.

![](images/12.png)

Click "Next."

![](images/13.png)

Select the Vocareum account we've been using.

![](images/14.png)

Click "Continue."

![](images/15.png)

Great.  You're logged in.  Return to the tab with the terminal.

![](images/16.png)

We can now run the deploy script.  To do so run:

    ./deploy.sh

![](images/17.png)

Select your subscription.  In my case it was called "Neo4j Subscription 32"

![](images/18.png)

This creates a fair amount of output.  One useful bit is a suggestion to run a smoke test.  Let's try that.  A generic version of the command is:

    ./test-mcp.sh "$(azd env get-value mcpEndpoint)"

![](images/19.png)

Assuming that looks good, let's investigate our deployment in the portal.  Open [https://ai.azure.com/](https://ai.azure.com/).

![](images/20.png)

Click "Sign in" in the upper right.

![](images/21.png)

Dismiss the pop up.

![](images/22.png)

You should see the project that our deploy script created.  In this case it is proj-foundry-neo4j-demo.  Click on that project to open it.

![](images/23.png)

Click the slider by "New Foundry" to go back to the previous UI version.

![](images/24.png)

Click "Continue without feedback."

![](images/25.png)

Click "Agents" in the left menu.

![](images/26.png)

Click "Fix Me" to fix the role.

![](images/27.png)

Click "X" to close the menu once it says it is fixed.

![](images/28.png)

Click "New agent."
s
![](images/29.png)

Click "Create new agent."

![](images/30.png)

Enter the name "neo4j-research-agent"

![](images/31.png)

Click "Create."

![](images/32.png)

That will take a moment to run.

![](images/33.png)

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

![](images/34.png)

Now click "Add."

![](images/35.png)

Click "Browse all tools."

![](images/36.png)

Click "Custom."

![](images/37.png)

Click "Model Context Protocol (MCP)"

![](images/38.png)

Click "Create."

![](images/39.png)

We're going to need to fill out these values.

![](images/40.png)

First, we're going to need a value from our Cloud Shell.  Back in there run:

    cd ..
    cat .env

Make a note of NEO4J_MCP_ENDPOINT.  In this case it was https://ca-foundry-neo4j-demo.blackcoast-f5039cd1.swedencentral.azurecontainerapps.io/mcp

![](images/41.png)

Ok.  Now back in the Foundry UI, let's enter the following values:

* Name - neo4j-mcp
* Remote MCP Server endpoint - value from last step
* Authentication - Key based

Click "Add key value pair."

![](images/42.png)

Enter the values:

* Authorization
* Y29tcGFuaWVzOmNvbXBhbmllcw==

![](images/43.png)

Click "Connect."

![](images/44.png)

Click "Save."

![](images/45.png)

In the "Message the agent..." field type:

    Tell me about Microsoft — what industry it competes in, who runs it, and where it's headquartered.

![](images/46.png)

Hit enter.

![](images/47.png)

Whoops.  Error.

![](images/48.png)

Try:

    Find three companies that compete in the same industry as Microsoft.

Try:

    What recent articles mention Microsoft, and what topics do they cover?