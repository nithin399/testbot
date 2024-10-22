
# Fashion Search AI - README

## Project Overview
The **Fashion Search AI** is a generative search system designed to recommend fashion products based on user queries. The system combines **OpenAI GPT models**, **FAISS** (Facebook AI Similarity Search), and **LangChain** to retrieve and rank product descriptions based on semantic similarity to the user's query.

## Key Components:
1. **OpenAI GPT Models**: Used for embedding product descriptions and generating responses to user queries.
2. **FAISS**: A vector similarity search engine to store product embeddings and retrieve the most relevant results.
3. **LangChain**: Orchestrates GPT with FAISS to handle search queries and return natural language responses.

## Requirements:
- Python 3.8+
- OpenAI API Key (to use GPT models and embeddings)
- Libraries:
  - `langchain-openai`
  - `faiss-cpu`
  - `numpy`
  - `pandas`
  - `json`
  - `streamlit` (optional, if using a web interface)

## Setup Instructions:

1. **Install Dependencies**:
   Install the required Python libraries using `pip`:
   ```bash
   pip install langchain-openai faiss-cpu numpy pandas
   ```

2. **Set Up OpenAI API Key**:
   You'll need an OpenAI API key to run the GPT models for embeddings and query responses. Sign up on the [OpenAI platform](https://platform.openai.com) and generate an API key.
   Export the API key as an environment variable:
   ```bash
   export OPENAI_API_KEY='your-api-key'  # For Linux/MacOS
   set OPENAI_API_KEY=your-api-key       # For Windows
   ```

3. **Prepare the Dataset**:
   Ensure your dataset is in **JSONL format**. Place the product descriptions, features, ratings, and other metadata in the JSONL file. Each line should represent a product.

   Example JSONL data:
   ```json
   {
     "title": "YUEDGE 5 Pairs Men's Moisture Control Socks",
     "description": "Cushioned socks for men, ideal for athletic activities.",
     "price": "$10.99",
     "ratings": "4.6",
     "features": "Moisture control, Cushioned",
     "categories": "Men's Fashion, Socks",
     "store": "GiveGift",
     "image_url": "https://example.com/image.jpg"
   }
   ```

4. **Run the Jupyter Notebook**:
   Launch Jupyter Notebook and open the notebook file `Semantic_Spotter_Project_with_Documentation.ipynb`:
   ```bash
   jupyter notebook Semantic_Spotter_Project_with_Documentation.ipynb
   ```
   Run the cells in sequence:
   - The notebook will load the JSONL data, generate embeddings, store them in FAISS, and initialize the GPT model.
   - You can then query the system by passing natural language queries.

5. **Query the System**:
   Use natural language queries to retrieve fashion product recommendations. Example queries:
   ```python
   query = "Find moisture-wicking socks for men"
   response = query_search_system(qa_chain, query)
   print(response)
   ```

## Optional Web Interface:
For a simple web interface using **Streamlit**, you can create a basic front-end.

1. Install Streamlit:
   ```bash
   pip install streamlit
   ```

2. Create a `streamlit_app.py` file:
   ```python
   import streamlit as st
   from main import query_search_system, create_retrieval_qa_chain

   st.title('Fashion Search AI')

   query = st.text_input('Enter your search query:')
   if query:
       response = query_search_system(qa_chain, query)
       st.write(response)
   ```

3. Run Streamlit:
   ```bash
   streamlit run streamlit_app.py
   ```


## Contributors:
- Developer: NITHIN
- Tools: OpenAI, LangChain, FAISS, Python, JSONL
