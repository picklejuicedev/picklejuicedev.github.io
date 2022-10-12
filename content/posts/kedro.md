+++
author = "Sean Westgate"
title = "Kedro"
date = "2022-09-09"
draft = true
description = "Guide to using Kedro in data projects"
tags = [
    "data",
]
+++

## ntro

Whilst digging deeper into data projects it very soon became clear that there are many one-off projects and resources that tell you how to get something done. Which is great when you learn a new tech and just need to wrangle that dataset or visualise those  dataframes. But how do you build something that lasts longer than the duration of your project and that you will be able to return to after a few months and can still run and use? What if you have a team of data scientists or engineers all creating their own style project and only they really understand what is going on in their code, not because the code is complicated, but because the structure is unique to every single person and project.



First step is probably create an agreed project structure, maybe use cookiecutter as a tool to share between the team easily? But then the next step is to bring structure to your python code and now you are introducing modules, and more conventions.

Then I cam across Kedro. And here is a project by a bunch of people who have solved this exact problem and then shared it with the world. Yihaa!

So this article is in 2 parts:

- first let's talk about the why and what problems Kedro solves and which ones it doesn't. Based on this you can decide if this is something you want to try.
- secondly I have created a walkthrough for my own project which you can follow along to get a bit deeper into it.

So let's get started:

## why kedro



https://youtu.be/yEQqf3XUvzk



une 6, 2019[QuantumBlack](https://www.quantumblack.com/), the advanced analytics firm we acquired in 2015, has now launched Kedro, an [open source](https://en.wikipedia.org/wiki/Open_source) tool created specifically for data scientists and engineers. It is a library of code that can be used to create [data and machine-learning pipelines](https://en.wikipedia.org/wiki/Pipeline_(computing)). For our non-developer readers, these are the building blocks of an analytics or machine-learning project.

“Kedro can change the way data scientists and engineers work,” explains product manager [Yetunde Dada](https://www.linkedin.com/authwall?trk=bf&trkInfo=AQHcVwWqOCbBYgAAAWsj88JQiSPAJJsQdCbKiHaUS9ij7KCah06cpszJ5UtzJ7WtqHC5FeLd95-8pElq_YFccIQqGD6slUdY32la6RMfk_xLKl4KvtGINL5PRD4LchGeQr71XmA=&originalReferer=&sessionRedirect=https%3A%2F%2Fwww.linkedin.com%2Fin%2Fyetudada%2F), “making it easier to manage large workflows and ensuring a consistent quality of code throughout a project.”



McKinsey has never before created a publicly available, open source  tool. “It represents a significant shift for the firm,” notes [Jeremy Palmer](https://www.linkedin.com/in/jeremy-palmer-022a5814/), CEO of QuantumBlack, “as we continue to balance the value of our  proprietary assets with opportunities to engage as part of the developer community, and accelerate as well as share our learning.”

The name Kedro, which derives from the Greek word meaning center or  core, signifies that this open-source software provides crucial code for ‘productionizing’ advanced analytics projects.

Kedro has two major benefits: it allows teams to collaborate more  easily by structuring analytics code in a uniform way so that it flows  seamlessly through all stages of a project. This can include  consolidating data sources, cleaning data, creating features and feeding the data into machine-learning models for explanatory or predictive  analytics.

Kedro also helps deliver code that is ‘production-ready,’ making it  easier to integrate into a business process. “Data scientists are  trained in mathematics, statistics and modeling—not necessarily in the  software engineering principles required to write production code,”  explains Yetunde. “Often, converting a pilot project into production  code can add weeks to a timeline, a pain point with clients. Now, they  can spend less time on the code, and more time focused on applying  analytics to solving their clients’ problems.”

At a feature level, Kedro helps teams build data pipelines that are  modular, tested, reproducible in any environment and versioned, allowing users to access previous data states.

“More importantly, the same code can make the transition from a  single developer’s laptop to an enterprise-level project using cloud  computing,” explains [Ivan Danov](https://www.linkedin.com/in/idanov/), Kedro’s technical lead. “And it is agnostic, working across industries, models and data sources.”

Two years in the making, Kedro was the brainchild of two QuantumBlack engineers – [Nikolaos Tsaousis](https://www.linkedin.com/in/ntsaousis/) and [Aris Valtazanos](https://www.linkedin.com/in/aris-valtazanos/), and QuantumBlack alumnus, [Peteris Erins](https://www.linkedin.com/in/peteriserins/), who created it to manage their numerous workstreams. Kedro had started  as a prototype library and was being quickly adapted by different teams  when they brought it to [Quantum Black Labs](https://quantumblack.com/labs/), a technical innovation group led by [Michele Battelli](https://www.linkedin.com/in/battelli/).

“Client teams can rotate into our lab and have the resources to  convert a one-off piece of software or database [such as Kedro] into a  viable product that can be used across industries, and that will be  continually improved,” explains Michele. “It is a powerful way of  innovating; our tech teams can move faster, more efficiently, and make a lasting contribution.”

McKinsey has used Kedro on more than 50 projects, to date. According  to Nikolaos, clients especially like its pipeline visualization. He  explains that Kedro makes conversations much easier, as clients  immediately see the different transformation stages, types of models  involved, and can backtrack outputs all the way to the raw data source.

“Kedro began as a proprietary program, but when a project was over,  clients couldn’t access the tool any more. We had created a technical  debt,” Nikolaos said. “By converting Kedro into an open source tool,  clients can use it after we leave a project—it is one way we are giving  back."

“There is a lot of work ahead, but our hope and vision is that Kedro  should help advance the standard for how data and modelling pipelines  are built around the world, while enabling continuous and accelerated  learning. There are huge opportunities for organizations to improve  their performance and decision-making based on data, but capturing these opportunities at scale, and safely, is extremely complex and requires  intense collaboration,” says Jeremy. “We’re keenly interested to see  what the community does with this and how we can work and learn faster  together.”



## Pipeline Visualisation

[Kedro's pipeline visualisation plugin](https://github.com/kedro-org/kedro-viz) shows a blueprint of your developing data and machine-learning  workflows, provides data lineage, keeps track of machine-learning  experiments and makes it easier to collaborate with business  stakeholders

![image-20220909110651072](C:\hugo\content\static\images\image-20220909110651072.png)



## Data Catalog

A series of lightweight data connectors used to save and load data  across many different file formats and file systems. Supported file  formats include Pandas, Spark, Dask, NetworkX, Pickle, Plotly,  Matplotlib and many more. The Data Catalog supports S3, GCP, Azure,  sFTP, DBFS and local filesystems. The Data Catalog also includes data  and model snapshots for file-based systems.

https://kedro.readthedocs.io/en/stable/05_data/01_data_catalog.html



## Integrations

![image-20220909110814905](C:\hugo\content\static\images\image-20220909110814905.png)

Apache Spark, Pandas, Dask, Matplotlib, Plotly, fsspec, Apache Airflow, Jupyter Notebook and Docker.



## Project Template

You can standardise how configuration, source code, tests,  documentation, and notebooks are organised with an adaptable,  easy-to-use project template. [Create your cookie cutter project templates with Starters.](https://kedro.readthedocs.io/en/stable/07_extend_kedro/05_create_kedro_starters.html)

```
project-template    # Project folder
├── conf            # Configuration files
├── data            # Local project data
├── docs            # Documentation
├── logs            # Logs of pipeline runs
├── notebooks       # Exploratory Jupyter notebooks 
├── pyproject.toml  # Identifies the project root
├── setup.cfg       # Configuration options for testing and linting
├── README.md       # README.md explaining your project
├── setup.cfg       # Configuration options for testing and linting
└── src             # Source code for pipelines

```



