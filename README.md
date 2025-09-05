# Zep-Memory-AI-Assistant---n8n-Workflow

  <img width="695" height="419" alt="image" src="https://github.com/user-attachments/assets/9eb3d3f3-48ab-422e-a185-e46595dd60d4" />


A sophisticated n8n workflow that creates a memory-enabled AI assistant using Zep Cloud's graph memory system. This workflow allows the AI to remember and recall information across conversations, providing a more personalized and contextual experience.
🌟 Features

Persistent Memory: Stores conversation history and facts in Zep Cloud's graph database
Intelligent Recall: Retrieves relevant information from past conversations
Multi-Model Support: Supports both Google Gemini and DeepSeek models
Real-time Chat Interface: Interactive chat trigger for immediate responses
Memory Graph Management: Automatic user creation and memory storage

🏗️ Architecture
The workflow consists of several key components:
Core Nodes

Chat Trigger: Entry point for user messages
Zep Mind Memory Agent: Central AI agent that orchestrates memory operations
Language Models: Google Gemini and DeepSeek for AI responses
HTTP Tools: For Zep Cloud API interactions

Memory Operations

Memory Storage (graph/post): Saves new messages and facts to user's memory graph
Memory Search (graph/GET): Retrieves relevant information from stored memories
User Management: Creates and manages user profiles in Zep Cloud

📋 Prerequisites

n8n instance (self-hosted or cloud)
Zep Cloud account and API key
Google Gemini API credentials
Vercel AI Gateway credentials (for DeepSeek)

🚀 Setup Instructions
1. Zep Cloud Setup

Sign up for a Zep Cloud account
Generate an API key from your dashboard
Replace "your own zep api key" in the workflow with your actual API key

2. API Credentials Configuration
Configure the following credentials in n8n:
Google Gemini API

Credential Name: telegram
API Key: Your Google Gemini API key

Vercel AI Gateway

Credential Name: n8n testing August 22
API Key: Your Vercel AI Gateway credentials

3. Initial Setup (Run Once)
Execute the Zep user id creation node to create a user profile:
json{
  "user_id": "Dummy user id"
}
4. Workflow Import

Copy the workflow JSON
Import into your n8n instance
Configure all credentials
Activate the workflow

🔧 Configuration
User ID Customization
Update the user_id parameter in both HTTP nodes:

Current: "inin8n"
Change to your preferred user identifier

Model Selection
The workflow supports two AI models:

Google Gemini: Primary model for chat responses
DeepSeek v3.1: Alternative model via Vercel AI Gateway

💬 Usage
Starting a Conversation

Access the chat interface via the webhook URL
Send messages naturally - the AI will:

Store your message in memory
Search for relevant past information
Provide contextual responses



Memory Operations
The AI agent automatically handles:

Storing: New messages and inferred facts
Retrieving: Relevant information when needed
Contextualizing: Responses based on conversation history

🛠️ Workflow Components
HTTP Request Nodes
Memory Storage (graph/post3)
httpPOST https://api.getzep.com/api/v2/graph
Headers: Authorization: Api-Key "your-api-key"
Body: {
  "user_id": "inin8n",
  "data": "user message content",
  "type": "message"
}
Memory Search (graph/GET1)
httpPOST https://api.getzep.com/api/v2/graph/search
Headers: Authorization: Api-Key "your-api-key"
Body: {
  "user_id": "inin8n",
  "query": "search query",
  "scope": "edges"
}
AI Agent Configuration
The agent is configured with:

Memory-aware prompting: Instructions for using memory tools
Tool integration: Access to both storage and retrieval functions
Fallback handling: Error recovery mechanisms

🔍 How It Works

User Input: Chat message received via webhook
Memory Search: Agent searches for relevant past information
Context Building: Combines current input with retrieved memories
Response Generation: AI model generates contextual response
Memory Storage: New information stored in Zep Cloud
User Response: Final answer delivered to user

🚨 Troubleshooting
Common Issues
API Key Errors

Ensure Zep API key is correctly formatted with quotes
Verify API key has proper permissions

Model Failures

Check Google Gemini API quota and credentials
Verify Vercel AI Gateway configuration

Memory Storage Issues

Confirm user ID exists in Zep Cloud
Check HTTP request formatting

Debug Steps

Test individual HTTP nodes manually
Verify credential configurations
Check n8n execution logs
Validate JSON formatting in requests

📊 Monitoring
Monitor workflow performance through:

n8n execution history
Zep Cloud dashboard analytics
API usage metrics

🔒 Security Considerations

Store API keys securely in n8n credentials
Use environment variables for sensitive data
Implement proper user authentication if needed
Regular API key rotation recommended

🚀 Customization Ideas
Enhancements

Add conversation summarization
Implement memory expiration policies
Create memory export functionality
Add multi-user support
Integrate with external databases

Advanced Features

Implement memory clustering
Add semantic search capabilities
Create memory visualization
Implement conversation analytics

📚 Resources

n8n Documentation
Zep Cloud Documentation
Google Gemini API
Vercel AI Gateway

📄 License
This workflow is provided as-is for educational and development purposes. Please ensure compliance with all third-party service terms of use.
🤝 Contributing
Feel free to submit issues, feature requests, or improvements to enhance this workflow's functionality.
