# FilmFinder - A Movie Recommendation Chatbot

[FilmFinder](https://github.com/karimtazzi/FilmFinder-A-Movie-Recommendation-Chatbot) is an interactive chatbot that provides detailed movie recommendations and information, including plot summaries, cast, and directors. Built with Python, the application leverages a Neo4j database for movie data and LangChain for language model-powered responses, with an easy-to-use interface powered by Streamlit.

## Features

- **Movie Information**: Provides detailed information on movies, including synopsis, actors, and directors.
- **Plot Search**: Allows searching for movies based on keywords or plot descriptions.
- **Conversational Memory**: Maintains conversation history for context-aware interactions.

## File Structure

An overview of the main files and directories in the project:

- `.streamlit/`: Streamlit configuration.
- `tools/`:
  - `cypher.py`: Manages Cypher queries to interact with the Neo4j database.
  - `vector.py`: Retrieves movie plots using vector embeddings for similarity searches.
- `agent.py`: Defines the conversational agent that retrieves answers using various tools and sources.
- `bot.py`: Streamlit UI script that manages interactions with the agent.
- `graph.py`: Establishes the Neo4j database connection.
- `llm.py`: Configures the language model used to generate responses.
- `utils.py`: Contains utility functions, such as session management.
- `requirements.txt`: Lists the Python dependencies required for the project.

## Prerequisites

Make sure you have the following installed:

- **Python 3.8+**
- **Neo4j**: A Neo4j database instance (local or hosted).
- **OpenAI Account** (if using OpenAI API for the language model).

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/karimtazzi/FilmFinder-A-Movie-Recommendation-Chatbot.git
   cd FilmFinder-A-Movie-Recommendation-Chatbot

2. Install the dependencies:
   pip install -r requirements.txt

3. Set up secrets for Streamlit by creating a secrets.toml file in the .streamlit/ directory:

    [secrets]
    NEO4J_URI = "bolt://localhost:7687"
    NEO4J_USERNAME = "your_username"
    NEO4J_PASSWORD = "your_password"

## Usage

Start your Neo4j server and ensure it contains movie data, including properties like plot, title, and plotEmbedding for movies.

Launch the Streamlit application:  streamlit run bot.py

## How It Works
The main workflow of the application is as follows:

1. User Input: The user enters a question or movie plot description.
2. Agent Processing: The agent (defined in agent.py) decides if the query requires a database search, plot retrieval, or general conversation.
3. Database Retrieval: cypher.py and vector.py handle specific data retrievals via Cypher queries or vector embeddings.
4. Response Generation: The language model generates a response, which is displayed to the user in the Streamlit interface.