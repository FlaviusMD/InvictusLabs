# Invictus Labs

## Description ##

The scope of this project is to construct a platform for measuring the credit risk of DeFi (lending) pools, by modelling the relationships between entities that partake in borrowing through causal inference and machine learning techniques. 

Sophisticated financial institutions in TradFi model various types of risks, such as credit, counterparty, market, political, country risks. 

In order to mitigate risk, there exist two well known techniques:

- qualitative - methods that do not require a model. Here, the risk is assesed using mostly expert-driven techniques.
- quantitative - a mathematical model is used, allowing for more elaborate analysis.


## Value added ##
For example, we can answer questions such as how the risk of a malicious borrower could ‘’intoxicate’’ others, via ripple effects.
## Benchmarks ##
* Copula model
* Knowledge graph-based model

## Architecture ##
![image-description](assets/Invictus_Labs_overview_arch_1.png)




### Data ###

What kind of data we use and how do we structure it?



- **On-chain data** module: use (wallet) transaction data on DeXes, metrics from wallet addresses
- **Off-chain data** module: use balance sheets, margin/leverage history, equity/liquidity,  business registration details, historical business data, payment history and collections, public fillings, etc.
- **Data aggregator engine**: will combine the previous 2 modules, and will output structured *entities* and *relationships* between entities. We will use a text-to-entity approach, by applying a bi-directional LSTM model for capturing entities and relationships from unstructured text data.


### Copula model ###

A copula model is a type of mathematical model that is used to describe the dependence between different sources of risk. In the context of credit risk, a copula model can be used to understand the relationship between the likelihood of a borrower defaulting on a loan and the potential impact of that default on the lender.

The model consists of two components: a *marginal* model, which describes the distribution of the individual sources of risk, and a *copula* function, which describes the dependence between those sources of risk. The marginal model can be specified using a variety of different parametric forms, such as the logistic or normal distributions, while the copula function can be specified using a variety of different parametric forms, such as the Gaussian or Clayton copulas. 


### Graph-based model ###
In light of crypto recent events, borrower activities both depend upon and have consequences on the DeFi/Web3 ecosystem. *Bayesian networks* are able to synthesize different kinds of knowledge and explicitly account for the probabilities of different scenarios, therefore offering a very useful tool for risk assesment. 

*Bayesian networks* (causal inference models) are a type of probabilistic graphical model that explicitly describe
dependencies between a set of variables using a directed acyclic graph (DAG) and a set of
node probability tables (NPTs). Each node in a DAG has a node probability table (NPT) which describes the probability
distribution of the node conditional on its parents.


In order to build the model, the **Data Aggregator Engine** will fetch as input what *On-chain* and *Off-Chain* data modules offer, offering as output a tuple under the form *(Entity, Relationship, Entity)*. The on-chain data is more structured, by connecting wallets/pools as entities  and transactions (with their corresponding numerical values) as relationships.

For the off-chain data (such as reports, balance sheets, etc), we will make use of both a domain expert and a text-to-entity approach, by using a bidirectional LSTM to identify entities and relationships. 


## Risk assesment methodology ##

For every borrower, we will construct a **Overall risk score** which is composed of the output of model trained on the data offered by the borrower/ any externally accesibile data sources (**Individual credit risk**), along with the output of the Bayesian network inference model based on its relation with other borrowers (**Systemic Credit Risk**).
The **Risk assesment methodology** is comprised of the following steps:

*Individual Credit Risk* - obtained via 


## Allocation Engine ##



* Text to entity engine (using Transformer or Bidirectional LSTM architecture)
* Relationship modelling
* Quantify the impact of the relationship between entities
* Risk assesment engine




