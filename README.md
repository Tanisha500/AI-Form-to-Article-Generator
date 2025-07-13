AI Form-to-Article Generator using n8n + Groq API
This automation project uses a form-based input system to generate a complete blog article using a large language model (LLM) via the Groq API. The workflow is designed in n8n and utilizes prompt engineering techniques to create high-quality content based on user inputs.

Tools & Technologies
n8n – No-code automation workflow builder
Groq API – For LLM-based article generation (Mixtral or LLaMA models)
Set & Function Nodes – For input formatting and dynamic prompt construction
Google Sheets – For storing the final AI-generated articles
Use Case
Automate blog content generation by:

Accepting form input (topic, audience, tone, keywords, word count)
Creating a structured prompt for the LLM
Sending the prompt to Groq API
Receiving the generated blog article
Saving the article in a Google Sheet for future use
Workflow Overview
Workflow Steps:
On form submission → Format prompt → Generate text via Groq → Store in Google Sheets

Node-by-Node Breakdown:
On form submission

Collects user input like blog topic, tone, target audience.
Set Node (Prompt Formatter)

Stores the user inputs into variables for use in the next node.
Code (Function Node)

Dynamically constructs a structured prompt such as:
"Write a blog article for college students on 'Time Management' in a friendly tone."
HTTP Request (Groq API)

Sends the constructed prompt to Groq's /openai/v1/chat/completions endpoint using POST method.
Code (Post-processing Node)

Extracts and formats the AI response (i.e., the blog content).
Append row in sheet

Stores the article along with metadata like topic, tone, and date into a connected Google Sheet.
