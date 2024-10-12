## Overview

This project integrates OpenAI’s API with Azure Cognitive Search to build a document search and Q&A system. The project allows users to search for specific documents or information based on a unique identifier (SKU ID) or textual input, retrieves relevant document excerpts from Azure Cognitive Search, and then uses OpenAI’s GPT models to generate responses based on the retrieved content.

### Key Features
- **Document Search**: Fetch documents from Azure Cognitive Search using SKU ID or a search term.
- **Contextual Q&A**: Generate AI-driven answers to user queries based on document content.
- **Integration**: Utilizes OpenAI API and Azure Cognitive Search to provide intelligent responses.
  
## Setup

### Prerequisites
- Python 3.8+
- Azure Cognitive Search service
- OpenAI API credentials
- Required Python packages listed in `requirements.txt`

### Environment Variables

Create a `.env` file in the root directory of the project, or set the following environment variables in your system:

```
OPENAI_API_TYPE=<your_openai_api_type>
OPENAI_API_VERSION=<your_openai_api_version>
OPENAI_API_BASE=<your_openai_api_base_url>
OPENAI_API_KEY=<your_openai_api_key>
AZURE_OPENAI_ENDPOINT=<your_azure_openai_endpoint>
SEARCH_KEY=<your_azure_search_key>
SEARCH_ENDPOINT=<your_azure_search_endpoint>
INDEX_NAME=<your_index_name>
```

### Installation

1. Clone the repository:
   ```bash
   git clone [azure-ai-chatbot](https://github.com/hamdanwaqar/sql-chatbot-ai)
   cd main
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Load environment variables:
   ```bash
   cp .env.example .env
   # Fill in your API keys in the .env file
   ```

## Usage

### Document Search
The `search_documents` function allows you to search Azure Cognitive Search by either SKU ID or a general search term.

```python
def search_documents(search_text, index=index_name, skuid="2785BA"):
    ...
```

You can modify the `search_text` or `skuid` to fetch different documents from your Azure Search index.

### Q&A API
The `request_to_model` function allows you to generate a Q&A based on the search results. It sends a request to OpenAI’s API, passing in the relevant context retrieved from Azure Cognitive Search.

```python
def request_to_model(input, index=index_name, project_name='Proposal', instructions="Use this data to answer user prompt:"):
    ...
```

### Running the Project
To run the project, execute the following command:

```bash
python main.py
```

This will:
1. Establish a connection with Azure Cognitive Search.
2. List all available indexes.
3. Allow you to test the search and Q&A functionalities.

## Key Functions

### `get_search_connection`
Establishes a connection to the Azure Cognitive Search service.

### `search_documents`
Searches for documents in Azure Cognitive Search based on the provided SKU ID or search text.

### `request_to_model`
Generates a Q&A response by searching the document content and then sending a prompt to OpenAI’s GPT model.

## Example

```python
# Example usage
response = request_to_model(input={"messages": [{"prompt": "What is the order quantity?", "skuid": "12345"}]})
print(response)
```

## Future Enhancements
- Support for additional document types (e.g., Word, Excel).
- Expanded filtering options for search results.
- Enhanced response generation based on more complex document structures.

## License
This project is licensed under the MIT License.
