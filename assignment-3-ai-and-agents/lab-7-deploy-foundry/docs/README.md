# Lab 7 - Deploy Foundry

Model Context Protocol (MCP) provides a standard interface for agents to speak with one another.  Neo4j has an open source [MCP server](https://github.com/neo4j/mcp).

Neo4j and Microsoft collaborated to build scripts exposing that MCP server in Microsoft Foundry.  Documentation on that is [here](https://neo4j.com/labs/genai-ecosystem/genai-frameworks/microsoft-foundry-mcp/).  The underlying code is [here](https://github.com/neo4j-labs/neo4j-agent-integrations/blob/main/microsoft-foundry/).

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
    ls

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

This creates a fair amount of output.  

Be sure to make a note of the Endpoint as you will need it in the next lab.  In this case it was: https://ca-foundry-neo4j-demo.jollyocean-6151e4e7.swedencentral.azurecontainerapps.io/mcp.

One useful bit is a suggestion to run a smoke test.  Let's try that.  A generic version of the command is:

    ./test-mcp.sh "$(azd env get-value mcpEndpoint)"

![](images/19.png)

If everything is deployed well, you should see a message like this.

Now let's look at the deployed resources.  Click the line in the upper right to minimize the Cloud Shell.

![](images/20.png)

Click on "Resource Groups."

![](images/21.png)

Click on "rg-foundry-neo4j-demo."

![](images/22.png)

We can see a number of resources were created.  There's a Foundry project.  We'll use that in the next lab.  Then there is a container app hosting our MCP server.

![](images/23.png)

In this lab we created a Foundry project.  We deployed the Neo4j MCP server.  In the next lab we'll use the Foundry UI to create an agent on top of it.
