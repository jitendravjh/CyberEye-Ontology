# Welcome to Cyber Eye

## A Pre-Final Year Project

This guide will help you navigate the repository and set up the project efficiently.

## Table of Contents
- [Pre-requisites](#pre-requisites)
- [Project Layout](#project-layout)
- [Installing Protege (Ontology Editor)](#installing-protege-ontology-editor)
- [Installing Neo4j Desktop (GraphDB)](#installing-neo4j-desktop-graphdb)
- [Running the Dashboard and Evaluation](#running-the-dashboard-and-evaluation)
- [Running the Evaluation](#running-the-evaluation)
- [Ontology Guidance](#ontology-guidance)
- [Knowledge Graph Guide](#knowledge-graph-guide)

## Pre-requisites
Ensure the following are installed:
- **Python 3**
- **Neo4j**
- **Protege**

## Project Layout
- Clone the repository.
- Install Protege (Ontology Editor).
- Install Neo4j Desktop (GraphDB).
- Run the dashboard and evaluation.

## Installing Protege (Ontology Editor)
Installation guides based on your OS:
- [Windows](https://protegeproject.github.io/protege/installation/windows/)
- [Mac](https://protegeproject.github.io/protege/installation/osx/)
- [Linux](https://protegeproject.github.io/protege/installation/linux/)

For beginners: [Getting Started with Protege](https://protegeproject.github.io/protege/getting-started/)

## Installing Neo4j Desktop (GraphDB)
Download Neo4j Desktop: [Neo4j Download](https://neo4j.com/docs/desktop-manual/current/)

## Running the Dashboard and Evaluation
Navigate to the working directory:
```bash
cd csonto/target/csonto/
```
Install Python dependencies:
```bash
pip install -r requirements.txt
```
Ensure the Neo4j database is running, then launch the dashboard:
```bash
streamlit run streamlit_app.py
```
Access the dashboard using the link provided in the terminal.

### Running the Evaluation
Navigate to the evaluation directory:
```bash
cd evaluation/
```
Run the following scripts to evaluate the ontology and knowledge graph:
```bash
python3 modelEval.py 
python3 ontologyEval.py
python3 kgEval.py
python3 ML-LinkPredict.py
```

## Ontology Guidance

### Accessing Ontology Files
Navigate to the ontology directory:
```bash
cd csonto/target/csonto/src/ontology/
```
Open the `csonto-edit` files with Protege to view or modify the ontology.

### Scripts for Ontology Manipulation
Navigate to the scripts directory:
```bash
cd csonto/target/csonto/src/scripts/
```
Key scripts:
- **StatusChecker:** Checks policy statuses within the ontology.
- **OntologyBuilder:** Builds and evolves the ontology.
- **Onto_Definitions & Updates:** Defines and updates ontology instances.

## Knowledge Graph Guide

### Querying the Cybersecurity Knowledge Graph (CSKG)
In the Neo4j Browser, execute the following Cypher query for a full graph view:
```cypher
MATCH (n:CyberSecurityScore)<-[r:REPORTS_TO]-(m) RETURN n, r, m 
UNION 
MATCH (n)<-[r:PART_OF]-(m) RETURN n, r, m
```

For a focused query on core CSKG elements:
```cypher
MATCH (n:CyberSecurityScore)<-[r:REPORTS_TO]-(m) RETURN n, r, m
```

Use these queries to analyze and visualize different aspects of the CSKG.
