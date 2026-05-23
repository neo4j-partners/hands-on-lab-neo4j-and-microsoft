# Lab 7 - MCP Tool

Model Context Protocol (MCP) provides a standard interface for agents to speak with one another.  Neo4j has an open source [MCP server](https://github.com/neo4j/mcp).

Neo4j and Microsoft collaborated to build scripts exposing that MCP server in Microsoft Foundry.  Documentation on that is [here](https://neo4j.com/labs/genai-ecosystem/genai-frameworks/microsoft-foundry-mcp/).  The underlying code is [here](https://github.com/neo4j-labs/neo4j-agent-integrations/blob/main/microsoft-foundry/).

In this lab we'll use that.

To get started, open your Azure Portal.

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

This directory contains some deployment scripts, a README and some underlying code.  We're going to deploy the example, so run:

    ./deploy.sh

![](images/10.png)

That creates a number of resources.  Investigate those in the portal.

Now let's run the server with:

    ./test-mcp.sh "$(azd env get-value mcpEndpoint)”

Now let's use the Foundry UI....
