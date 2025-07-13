#  AI Form-to-Article Generator using n8n + Groq API

This automation project uses a form-based input system to generate a **complete blog article** using a large language model (LLM) via the **Groq API**. The workflow is designed in **n8n** and utilizes prompt engineering techniques to create high-quality content based on user inputs.


##  Tools & Technologies

- **n8n** – No-code automation workflow builder
- **Groq API** – For LLM-based article generation (Mixtral or LLaMA models)
- **Set & Function Nodes** – For input formatting and dynamic prompt construction
- **Google Sheets** – For storing the final AI-generated articles


##  Use Case

Automate blog content generation by:
- Accepting form input (topic, audience, tone)
- Creating a structured prompt for the LLM
- Sending the prompt to Groq API
- Receiving the generated blog article
- Saving the article in a Google Sheet for future use


##  Workflow Overview

> **Workflow Steps:**  
> On form submission → Format prompt → Generate text via Groq → Store in Google Sheets

### Node-by-Node Breakdown:

1. **On form submission**  
   - Collects user input like blog topic, tone, target audience.

2. **Set Node (Prompt Formatter)**  
   - Stores the user inputs into variables for use in the next node.

3. **Code (Function Node)**  
   - Dynamically constructs a structured prompt such as:  
     `"Write a blog article for college students on 'Time Management' in a friendly tone."`

4. **HTTP Request (Groq API)**  
   - Sends the constructed prompt to Groq's `/openai/v1/chat/completions` endpoint using POST method.

5. **Code (Post-processing Node)**  
   - Extracts and formats the AI response (i.e., the blog content).

6. **Append row in sheet**  
   - Stores the article along with metadata like topic, tone, and date into a connected Google Sheet.



##  Workflow Screenshot

<img width="1259" height="305" alt="Screenshot 2025-07-12 050534" src="https://github.com/user-attachments/assets/23b023fc-8893-4169-b3a2-5af948ee57ed" />

## Google Sheet Output

<img width="1797" height="846" alt="Screenshot 2025-07-13 153834" src="https://github.com/user-attachments/assets/b587a965-8761-4932-ad46-dc2590a36879" />

##  Example User Input (JSON)

```json
{
  "Topic": "Streamlining Patient Care with Automation: How Tools like n8n Are Reshaping Healthcare Operations",
  "Audience": "Doctors, clinic managers, health-tech founders, and healthcare administrators looking to automate repetitive tasks and improve efficiency.",
  "Keywords": "healthcare automation, patient data workflows, digital health tools, n8n for healthcare, clinical process efficiency, medical task automation",
  "Tone": "Professional yet approachable—conveying authority with warmth, ideal for industry readers without overwhelming them with jargon.",
  "Word Count": 1500
}


