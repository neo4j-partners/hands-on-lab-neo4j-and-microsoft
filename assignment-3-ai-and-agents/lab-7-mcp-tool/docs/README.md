# Lab 7 - MCP Tool

Model Context Protocol (MCP) provides a standard interface for agents to speak with one another.  Neo4j has an open source [MCP server](https://github.com/neo4j/mcp).

Neo4j and Microsoft collaborated to build scripts exposing that MCP server in Microsoft Foundry.  Documentation on that is [here](https://neo4j.com/labs/genai-ecosystem/genai-frameworks/microsoft-foundry-mcp/).  The underlying code is [here](https://github.com/neo4j-labs/neo4j-agent-integrations/blob/main/microsoft-foundry/).

In this lab we'll use that.

To get started, open your Azure Portal.

Open a cloud shell.

Clone the repo:

    git clone https://github.com/neo4j-labs/neo4j-agent-integrations.git
    cd neo4j-agent-integrations

Cd and run the deploy script.

    cd microsoft-foundry/infra
    ./deploy.sh

That creates a number of resources.  Investigate those in the portal.

Now let's run the server with:

    ./test-mcp.sh "$(azd env get-value mcpEndpoint)”

Now let's use the Foundry UI....
