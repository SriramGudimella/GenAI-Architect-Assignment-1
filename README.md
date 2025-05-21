# GenAI-Architect-Assignment-1
Real-Time Market Sentiment Analyzer
This project implements a LangChain-powered pipeline that analyzes real-time market sentiment for specified companies. It fetches recent news, analyzes sentiment using Azure OpenAI models (GPT-4o or GPT-4o-mini), and produces structured sentiment analysis results.
Features
•	Accepts a company name as input
•	Extracts or generates the corresponding stock ticker/symbol
•	Fetches recent news using Yahoo Finance tools in LangChain
•	Sends news to Azure OpenAI (GPT-4o/GPT-4o-mini) for sentiment analysis
•	Extracts named entities (people, places, companies)
•	Provides structured JSON output with sentiment analysis
•	Uses Langfuse for tracing, monitoring, and prompt debugging
Tech Stack
•	Framework: LangChain
•	LLM: GPT-4o or GPT-4o-mini (deployed via Azure OpenAI)
•	Data Source: Yahoo Finance tool in LangChain
•	Prompt Management & Observability: Langfuse
•	Environment: Python (v3.10+ recommended)
Setup Instructions
Prerequisites
1.	Python 3.10 or higher
2.	An Azure OpenAI account with GPT-4o or GPT-4o-mini deployed
3.	Langfuse account for observability (optional but recommended)
Installation
1.	Clone this repository or download the source code.
2.	Create a virtual environment:
3.	python -m venv venv
4.	source venv/bin/activate  # On Windows: venv\Scripts\activate
5.	Install required packages:
6.	pip install langchain langchain-openai langchain-community pydantic python-dotenv langfuse
API Setup
1.	Azure OpenAI:
o	Create an Azure OpenAI resource
o	Deploy GPT-4o or GPT-4o-mini model
o	Note your API key, endpoint URL, and deployment name
2.	Langfuse (for observability):
o	Create a Langfuse account at langfuse.com
o	Create a new project and get your API keys
Environment Variables
Create a .env file in the project root with the following variables:
# Azure OpenAI
AZURE_OPENAI_API_KEY=your_azure_openai_api_key
AZURE_OPENAI_ENDPOINT=your_azure_endpoint_url
AZURE_OPENAI_DEPLOYMENT_NAME=your_model_deployment_name

# Langfuse (optional but recommended)
LANGFUSE_PUBLIC_KEY=your_langfuse_public_key
LANGFUSE_SECRET_KEY=your_langfuse_secret_key
LANGFUSE_HOST=https://cloud.langfuse.com  
Usage
Run the script from the command line:
python market_sentiment_analyzer.py
The script will prompt you to enter a company name and will output the analysis results.
Sample Command
# Start the analyzer
python market_sentiment_analyzer.py


Sample Output Json:
# When prompted, enter a company name:
Enter a company name (e.g., 'Microsoft'): amazon
Analysis Result:
{
  "company_name": "amazon",
  "stock_code": "AMZN",
  "newsdesc": "Amazon is making strategic moves in AI, supply chain management, and customer service, including issuing refunds for years-old returns, partnering with SAP for AI innovation, investing in an AI chipmaker competitor to Nvidia, and showcasing logistics innovation amidst tariff challenges.",
  "sentiment": "Positive",
  "people_names": [
    "Udit Madan",
    "Andy Jassy"
  ],
  "places_names": [],
  "other_companies_referred": [
    "SAP",
    "Nvidia"
  ],
  "related_industries": [
    "Artificial Intelligence",
    "Supply Chain Management",
    "Customer Service",
    "Semiconductors"
  ],
  "market_implications": "Amazon's strategic initiatives in AI and supply chain management could bolster its competitive edge and drive growth in emerging tech sectors. The refund policy may enhance customer loyalty but raises concerns about operational inefficiencies. Investment in an AI chipmaker competitor could disrupt Nvidia's dominance, signaling Amazon's influence in the semiconductor industry.",
  "confidence_score": 0.9
}
Troubleshooting
•	News API Issues: If you experience problems with the Yahoo Finance API, check for rate limiting or consider implementing a retry mechanism.
•	Azure OpenAI Errors: Verify your API credentials and deployment name in the .env file.
•	JSON Parsing Errors: These usually occur if the LLM output doesn't match the expected schema. Check the prompt templates and adjust as needed.
Langfuse – Prompt Versioning:
 

