# Lab 2 - Deploy Neo4j

There are a number of options for deploying Neo4j on Microsoft Marketplace:

* [Neo4j Community Edition](https://marketplace.microsoft.com/en-us/product/neo4j.neo4j-ce)
* [Neo4j Enterprise Edition](https://marketplace.microsoft.com/en-us/product/neo4j.neo4j-ee)
* [Neo4j Aura: Graph Intelligence Platform](https://marketplace.microsoft.com/en-us/product/neo4j.neo4j-aura)

CE and EE are self managed versions of the product.  Those marketplace listings deploy infrastructure in your account, including virtual machines.  Scripts then install and configure Neo4j.

Aura is a SaaS version of Neo4j.  That is managed entirely by Neo4j so no infrastructure administration is required.  We're going to use that version.  

That listings has mulitple plans.  We only need the instance for a few hours, so we will use a Pay as you go (PAYG) plan.  There is a different option for an annual purchase.

So, let's get started deploying...  Be sure your [Azure Portal](https://portal.azure.com/) is open from the last lab.  In the search bar, type "Neo4j Aura."

![](images/01.png)

"Neo4j Aura: Graph Intelligence Platform" is our newest listing that includes multiple plans.  Select that.

![](images/02.png)

This will take you to the "Neo4j Aura: Graph Intelligence Platform" marketplace listing.  

We will keep all the defaults. Simply click "Complete purchase."

![](images/03.png)

You will see a message that your subscription is in progress.

![](images/04.png)

After a moment, you should see that subcription completed.  Click "Continue to publisher's website."

This will "punch out" from the Azure Portal into the Neo4j Aura Console.

![](images/05.png)

Click "Accept Cookies"

![](images/06.png)

Neo4j supports a number of different auth providers, including Microsoft, GitHub and Google.  We've already authenticated with Microsoft for the console.

At this point you would understably want to use the Microsoft provider.  However the Vocareum account we're using doesn't have an email address associated with it.  Neo4j Aura requires an email.  So that provider will not work.

Instead, enter an email address of yours in the top field, "Email address (Business preferred)."

![](images/07.png)

Click "Continue."

![](images/08.png)

You should see a message saying to check your email.  Do so.

![](images/09.png)

The email looks like this.  Copy the code.

![](images/10.png)

Paste it back in the form.  Click "Continue."

![](images/11.png)

Enter a password for your account.

![](images/12.png)

Click "Sign up."

![](images/13.png)

We're now presented with a choice of product tiers within Neo4j:

* Free
* Business Critical
* Professional

The Free tier is a great way to get started experimenting.  Business Critical offers a 3 node fault tolerant and highly available cluster.  We don't really need that for this lab.  The Professional tier has similar functionality with a single node.  Select "Professional."

Note that since we punched of the Microsoft Marketplace, we carried along a payment mechanism from our Vocareum accont.  You will not be charged personally for the usage of Neo4j Aura today.  Instead that will be billed to Vocareum through the Microsoft Marketplace.

![](images/14.png)

Now, let's inspect the other options.

![](images/15.png)

We can deploy in different regions.

There are two options for Graph Analytics.  This feature provides access to 60+ graph alogrithms.  These run across your graph, computing things like centrality and node importance.  We'll keep the default.  That spins up computations on demand.  Another option is to collocate it in the database.

Finally, there's an option to optimize the database for vector search.  We'll be using vector functionality but our workloads will be comparatively light so we don't need this optimization.

We've reached the bottom!  Click "Create Instance."

![](images/16.png)

You'll be presented with the credentials for your database.  Click "Download and continue."  That will download the credentials to a text file on your local machine.  

![](images/17.png)

A save dialog should pop up.  Be sure to save that file as you won't be able to get those credentials later.

![](images/18.png)

You'll see a dialog that your database is being created. This should only take a few minutes.

![](images/19.png)

When deployment is complete you'll see the instance details in the management console.  

![](images/20.png)

You can poke around the menus here a bit and see more on database status and connection information.

You now have a deployment of Neo4j AuraDB Professional running!  In the next lab, we'll connect to it.
