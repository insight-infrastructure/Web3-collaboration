## **Project Description**

This project serves as an extension to the previously proposed and accepted load balanced endpoints proposal in which we provided the ecosystem with a multi-cloud reference architecture to deploy globally distributed sets of load balanced API endpoints configurable with a custom CLI. 

This proposal is now focused on operating those publicly accessible endpoints to be used by the Polkadot community. It is being paired with a soon to be submitted development proposal aimed at optimizing query response times for these endpoints with a microservices approach.  To inform which methods are highest priority for optimization, we will take a data driven approach by analyzing log data from this proposal and focus efforts on the most popular / most computationally demanding queries.  With these two grants executed in parallel, we aim to not only provide the community with an Infura-like interface at feature parity, but also make it easy for new users with different levels of experience to easily deploy their own clusters and contribute new endpoints.  

## **Team members**

- Engineers: Richard Mah, Rohit Gupta, Rob Cannon
- Project manager: Mitchell Krawiec-Thayer, Ph.D.

## **Team Website**

[www.insightdatascience.com](http://www.insightdatascience.com/)

[www.insightconsensus.com](http://www.insightconsensus.com/)

## **Legal Structure**

All contributors work with Insight, an US-based company that has been supporting specialized engineers since 2012.

## **Team's experience**

**Richard Mah** 

Holding a PhD in neuroscience, Richard has deep experience in the intersection between advanced data analysis and high performance computing. During his PhD, he employed a wide variety of machine learning techniques to automate the analysis of clinical data with a microservices-based architecture on Kubernetes. Since then, he became an Insight fellow working on immutable deployments of validator node infrastructure focusing specifically on monitoring and alarms.

[Github](https://github.com/shinyfoil)

**Rob Cannon**

DevOps developer in residence at Insight who focuses primarily on blockchain infrastructure. Focussing primarily on building automated deployments of validator nodes for the ICON blockchain, he is now looking to extend these patterns into other blockchains. Prior to Insight, he worked in the oil and gas industry founding a data science startup and working for a major operator.

[Github](https://github.com/robc-io), [Medium](https://medium.com/@robcannonxyz)

**Mitchell Krawiec-Thayer**

Decentralized Consensus Lead at Insight, mentor for Insight Residents. Have been doing privacy research and protocol SecEng for Monero Research Lab since 2017, and founded Noncesense Research Lab. Specializes in private protocol design, anti-heuristic engineering, empirical analysis, on & off-chain anomaly detection, metadata archive design & analysis.

[GitHub](https://github.com/mitchellpkt/), [Twitter](https://twitter.com/Mitchellpkt0), [LinkedIn](https://www.linkedin.com/in/mitchellpkt/), [Medium](https://medium.com/@mitchellpkt)

## **Team Code Repos**

- [github.com/insight-w3f](https://github.com/insight-w3f)
- [github.com/insight-w3f/terragrunt-polkadot](https://github.com/insight-w3f/terragrunt-polkadot)

## **Team LinkedIn Profiles**

- [linkedin.com/in/mitchellpkt/](https://www.linkedin.com/in/mitchellpkt/)
- [linkedin.com/in/rob-cannon-21571317/](https://www.linkedin.com/in/rob-cannon-21571317/)
- Richard Profile
- [https://www.linkedin.com/in/rohitbmw/](https://www.linkedin.com/in/rohitbmw/)

## **Development Roadmap**

This project aims at operating the previously developed load balanced endpoints.  All the infrastructure is in place and is currently operating at api.kusama.polkfura.com (json-rpc + wss).  While the prior grant gave us most of the production level components, certain items will still need further tuning to allow for easy operations of large clusters at scale. We would then like to aggregate health metrics from across the system and make them publicly available via a status page to display uptime.

One of the primary goals of this period in the grant is to gather user behavior to understand which queries need optimization. While the prior grant gave us a log collection stack (ELK), further improvements need to be made to support usage statistics. We intend on building those workflows to make analysis simple for benchmarking improvements.

We will also develop and operate a variety of quick sync chain data download locations on S3, CloudFront, and IPFS.  These locations will leverage the already developed "source of truth" node chain sync architecture as implemented by Infura for quick syncing of nodes.  Prior experience showed that sync times can be reduced by several orders of magnitude using this architecture that we believe would be beneficial to offer to the community. The intention would be to build an easily deployable quick sync tooling that can be shared around the community.

**Milestone 1: Public Load Balanced API Endpoints Deployment** 

**1.5 months**

---

**Goals:**

- Cost effective operation of globally distributed deployment of API endpoints

**Deliverables:**

- Operation of V1 endpoint on AWS in 2 regions with geo-routing through cloudflare
- Centralized monitoring and logging integration
- Metrics and logs populating Grafana and Kibana dashboards
- Status page for high level healthchecks on each zone

**Milestone 2: Quick sync endpoint development** 

**2 weeks** 

---

**Goals:**

- Provide an endpoint for node operator to quickly sync nodes off of

**Deliverables:**

- Operation of "source of truth" node to send copies of the chain data to persistent layers on a schedule
- "Requestor Pays" s3 bucket for downloading uncompressed blocks
- Content delivery network (cloudfront) for distributing compressed copies of the chain data
- IPFS content addresses with both compressed and uncompressed chain data
- CLI to facilitate download operations

**Milestone 3: Long Term Operations** 

**1 Year** 

---

**Goals:**

- 99% up time for publicly accessible load balanced and quick sync endpoints
- Data driven ranking of top queries to inform caching layers and microservice development
- Cost optimizations based on resource utilization

**Deliverables:**

- Quarterly report describing uptime, incidents, and operational changes
- AWS billing report and quarterly cost projections

### **Long Term Plans**

---

- Decentralized API providers
- *Microservices library to expose pre-indexed queries*
- CLI tooling for deploying modular sets of self-healing infrastructure

## **Additional Information**

---

A centralized API endpoint provider like Infura presents a variety of risks to the ecosystem that can only be averted by taking a decentralized approach.  While this grant will provide a centralized API endpoint, our approach is fully open source such that anyone can run their own endpoints with the same capabilities. 

CLI's are useful for making the node deployments simple to new users but can become quite opinionated when building in how optionality is expressed.  To make things customizable and configurable, we have built [nukikata](https://github.com/insight-infrastructure/nukikata), a declarative CLI with loops and conditionals, that we will be supporting in the long term.  It is an upstream fork of [cookiecutter](https://github.com/cookiecutter/cookiecutter), the worlds most popular code templating tool. We hope to make building customizable parachains one-click and allow for quick rendering of common code templates and best practices starter packages. For node operation, we based the CLI for our [reference architecture](https://github.com/insight-w3f/terragrunt-polkadot) on this tool and will be streamlining its patterns over time.
