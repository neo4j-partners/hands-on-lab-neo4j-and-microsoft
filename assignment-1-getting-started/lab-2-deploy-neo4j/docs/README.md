# Lab 2 - Deploy Neo4j

There are a number of options for deploying Neo4j on Microsoft Marketplace:

* [Neo4j Community Edition](https://marketplace.microsoft.com/en-us/product/neo4j.neo4j-ce)
* [Neo4j Enterprise Edition](https://marketplace.microsoft.com/en-us/product/neo4j.neo4j-ee)
* [Neo4j Aura (pay-as-you-go)](https://marketplace.microsoft.com/en-us/product/neo4j.neo4j-aura)
* [Neo4j Aura (Annual)](https://marketplace.microsoft.com/en-us/product/neo4j.neo4j_aura)

CE and EE are self managed versions of the product.  The marketplace listing deploys infrastructure in your account, including virtual machines.  Scripts then install and configure Neo4j.

Aura is a SaaS version of Neo4j.  That is managed entirely by Neo4j so no infrastructure administration is required.  We're going to use that version.  Specifically, we'll use the pay-as-you-go.  We only need the instance for a few hours, so an annual license would be rather excessive.

So, let's get started deploying...  Be sure your [Azure Portal](https://portal.azure.com/) is open from the last lab.  In the search bar, type "Neo4j Aura."

![](images/01.png)

There are two options for Neo4j Aura.  One is pay-as-you-go.  That means there is an hourly charge for the product.  

The other is Annual.  That is an annual contract.

Select the "Neo4j Aura (pay-as-you-go)" product.  That is the top result in this screenshot.

![](images/02.png)

This will take you to the Neo4j Aura (pay-as-you-go) marketplace listing.  

Dismiss the "New auto activation" dialog.

![](images/03.png)

We're going to need a resource group to hold our new subscription to Neo4j Aura (pay-as-you-go).  Click "Create new."

![](images/04.png)

Enter "neo4j-aura-subscription" as the name of the resource group.

![](images/05.png)

Click "OK."

![](images/06.png)

Now we need a name for the SaaS subcription object.  Let's use the same as the resource group name.  Enter "neo4j-aura-subscription"

![](images/07.png)

That's it for required details.  We could click next through the wizard.  However, since all required fields are complete, instead click "Review + subscribe."

![](images/08.png)

Dismiss the "Our invoicing policy has been updated" dialog.

![](images/09.png)

Click "Subscribe."

![](images/10.png)

The subscription takes about a minute to run.

![](images/11.png)

When complete you should see the following.  Click "Configure your account."  This will "punch out" from the Azure Portal into the Neo4j Aura Console.

![](images/12.png)

Click "Accept Cookies"

![](images/13.png)

Neo4j supports a number of different auth providers, including Microsoft, GitHub and Google.  We've already authenticated with Microsoft for the console.

At this point you would understably want to use the Microsoft provider.  However the Vocareum account we're using doesn't have an email address associated with it.  Neo4j Aura requires an email.  So that provider will not work.

Instead, enter an email address of yours in the top field, "Email address (Business preferred)."

![](images/14.png)

Click "Continue."

![](images/15.png)

You should see a message saying to check your email.  Do so.

![](images/16.png)

The email looks like this.  Copy the code.

![](images/17.png)

Paste it back in the form.

![](images/17.png)

Click "Continue."

![](images/18.png)

Enter a password for your account.

![](images/19.png)

Click "Sign up."

![](images/20.png)

You'll then be presented with a dialog to gather information about your use case.  Enter your information.

Note that we're starting to build a labeled property graph describing our use case.

![](images/21.png)

Click "Next."

![](images/22.png)

Click "Build a graph-powered application."  After all, we're going to be building some agent powered applications on top of Neo4j!

![](images/23.png)

Click "Data Scientist."  Even if that's not your job title, you are today.  We'll be using Graph Analytics!

![](images/24.png)

Now click "Generative AI."  We're going to be using Google Gemini Enterprise to build agents.

![](images/25.png)

We're now presented with a choice of product tiers within Neo4j:

* Free
* Business Critical
* Professional

The Free tier is a great way to get started experimenting.  Business Critical offers a 3 node fault tolerant and highly available cluster.  We don't really need that for this lab.  The Professional tier has similar functionality with a single node.  Select "Professional."

Note that since we punched of the Microsoft Marketplace, we carried along a payment mechanism from our Vocareum accont.  You will not be charged personally for the usage of Neo4j Aura today.  Instead that will be billed to Vocareum through the Microsoft Marketplace.

![](images/26.png)

Now, let's inspect the other options.

![](images/27.png)

We can deploy in different regions.

There are two options for Graph Analytics.  This feature provides access to 60+ graph alogrithms.  These run across your graph, computing things like centrality and node importance.  We'll keep the default.  That spins up computations on demand.  Another option is to collocate it in the database.

Finally, there's an option to optimize the database for vector search.  We'll be using vector functionality but our workloads will be comparatively light so we don't need this optimization.

We've reached the bottom!  Click "Create Instance."

![](images/28.png)

You'll be presented with the credentials for your database.  Click "Download and continue."  That will download the credentials to a text file on your local machine.  

![](images/29.png)

A save dialog should pop up.  Be sure to save that file as you won't be able to get those credentials later.

![](images/30.png)

You'll see a dialog that your database is being created. This should only take a few minutes.

![](images/31.png)

When deployment is complete you'll see the instance details in the management console.  

![](images/32.png)

You can poke around the menus here a bit and see more on database status and connection information.

You now have a deployment of Neo4j AuraDB Professional running!  In the next lab, we'll connect to it.
