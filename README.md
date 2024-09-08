# Holiday Park Recommendation System 

## Overview
This project is a personalised recommendation system for holiday parks, leveraging Neo4j for the knowledge graph, LLM using OpenAI GPT-3 for generating recommendations, and Streamlit for the web interface. The system integrates Agentic AI, Retrieval Augmented Generation (RAG), and data observability to enhance customer experience, drive business growth, and support sustainability goals.

## Features
- **Personalised Recommendations**: Provides tailored holiday park recommendations based on customer preferences.
- **Knowledge Graph**: Uses Neo4j to store and query relationships between customers and parks.
- **Agentic AI & RAG**: Utilizes the free OpenAI GPT-3.5 to generate contextually relevant recommendations.
- **Data Observability**: Monitors data quality using Grafana to ensure accurate and reliable recommendations.

## Architecture
The system consists of the following components:
- **Data Layer**: Stores customer and park data.
- **Knowledge Graph**: Represents relationships between customers and parks using Neo4j.
- **Agentic AI & RAG Layer**: Generates personalised recommendations using OpenAI GPT-3.5.
- **Data Observability Layer**: Monitors data quality with Grafana.
- **Application Layer**: Provides a user interface using Streamlit.

## Setup and Deployment

### Prerequisites
- **Neo4j**: Installed and running.
- **OpenAI API Key**: Access to OpenAI GPT-3.5.
- **Grafana**: Installed and running.
- **Python Environment**: Set up with necessary libraries.
- **Streamlit**: Installed for the web interface.

### Step-by-Step Guide

#### 1. Set Up Neo4j
- Install Neo4j from the official website.
- Start the Neo4j server and access the Neo4j browser at `http://localhost:7474`.
- Run the following Cypher queries to create the database and import data:
  ```cypher
  CREATE (a:Customer {id: '1', name: 'Alice', preferences: ['beach', 'hiking']})
  CREATE (b:Customer {id: '2', name: 'Bob', preferences: ['mountains', 'skiing']})
  CREATE (c:Park {id: '101', name: 'Beachside Park', features: ['beach', 'swimming']})
  CREATE (d:Park {id: '102', name: 'Mountain Retreat', features: ['mountains', 'skiing']})
  MATCH (a:Customer {id: '1'}), (c:Park {id: '101'}) CREATE (a)-[:LIKES]->(c)
  MATCH (b:Customer {id: '2'}), (d:Park {id: '102'}) CREATE (b)-[:LIKES]->(d)
