# hands-on-lab-neo4j-and-microsoft

Neo4j is the [leading graph database](https://db-engines.com/en/ranking/graph+dbms) vendor.  We’ve worked closely with Microsoft engineering for years.  Our SaaS database, Neo4j Aura, is offered as a managed service on Azure.  This is available through the [Azure Marketplace](https://marketplace.microsoft.com/en-us/product/neo4j.neo4j-aura).

In this hands on lab, you’ll get to learn about [Neo4j](https://neo4j.com/) and [Microsoft Foundry](https://azure.microsoft.com/en-us/products/ai-foundry).  The lab is intended for data scientists and data engineers.  We’ll walk through deploying Neo4j and Foundry in a Microsoft Azure account.  Then we’ll get hands on with a real world dataset.  First we'll use AI to parse and load data.  Then we'll show how to layer an AI agent over the knowledge graph.  You’ll come out of this lab with enough knowledge to apply graph AI to your own datasets.

We’re going to analyze the quarterly filings of asset managers with $100m+ assets under management (AUM).  These are regulatory filings made to the Securities and Exchange Commission’s (SEC) EDGAR system.  We’re going to show how to load that data from Azure Blob Storage into Neo4j.  We’ll then explore the relationships of different asset managers and their holdings using the Neo4j Browser and Neo4j’s Cypher query language.

If you’re in the capital markets space, we think you’ll be interested in potential applications of this approach to creating new features for algorithmic trading, understanding tail risk, securities master data management and so on.  If you’re not in the capital markets space, this session will still be useful to learn about building agentic AI pipelines with Neo4j and Microsoft Foundry.

## Venue

These workshops are organized onsite in a Microsoft office.

## Duration

3 hours.

## Prerequisites

You'll need a laptop with a web browser.  Your browser will need to be able to access the Microsoft Azure Portal and the Neo4j Aura Console running on Microsoft Azure.  If your laptop has a firewall you can't control, you may want to bring your personal laptop.

## Agenda

### Assignment 1

* Introductions
* Lecture - Introduction to Neo4j (15 min)
  * What is Neo4j?
  * How is it deployed and managed on Microsoft Azure?
* Lab 1 - Sign In (5 min)
  * Improving the Labs
  * Sign into Microsoft Azure
* Lab 2 - Deploy Neo4j (15 min)
  * Deploying Neo4j Aura Professional
* Lab 3 - Connect to Neo4j (5 min)
* Break (5 min)

### Assignment 2

* Lecture - Moving Data (10 min)
  * LOAD CSV
  * Neo4j Aura Importer
* Lab 4 - Query (15 min)
  * Simple Load Statement
  * More Performant Load
* Lab 5 - Explore (10 min)
  * Graph Business Intelligence
* Break (5 min)

### Assignment 3

* Lecture - Foundry (15 min)
  * Microsoft and AI
  * What is Foundry
* Lecture - Neo4j and AI (15 min)
  * Generating Knowledge Graphs
  * Retrieval Augmented Generation
  * Using Foundry with Neo4j
* Lab 6 - Document Intelligence (15 min)
* Lab 7 - Deploy Foundry (15 min)
* Lab 8 - Use Foundry (15 min)
* Lab 9 - Aura Agent (15 min)
* Questions and Next Steps (5 min)