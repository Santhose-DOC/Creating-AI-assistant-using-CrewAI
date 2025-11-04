# Creating-AI-assistant-using-CrewAI
# 🤖 WhatsApp & Email Assistant Using CrewAI

## 🧠 Overview
This project demonstrates how to use **CrewAI** to build intelligent AI agents that can rewrite WhatsApp or Email messages in a professional, polished, and natural tone.  
Using the **Google Gemini API** through CrewAI, the assistant automatically enhances the clarity, tone, and professionalism of any input message.

---

## ⚙️ Installation & Setup

### 1️⃣ Install Required Libraries
Before running the project, install the necessary dependencies:

```
pip install crewai 
pip install dotenv
```

---

### 2️⃣ Setup Environment Variables
You’ll need a **Google Gemini API key** to use CrewAI.

1. Go to [Google AI Studio](https://aistudio.google.com/api-keys).  
2. Create a new API key.  
3. In your project directory, create a file named `.env`.  
4. Paste your API key inside it as follows:

```
GEMINI_API_KEY=your_api_key_here
```

Load your environment variables in Python using:
```
from dotenv import load_dotenv
load_dotenv()
```


(Optional but recommended) Create and activate a virtual environment:
```
python -m venv env
source env/bin/activate # On Mac/Linux
env\Scripts\activate # On Windows
```

---

### 3️⃣ Verify Installation
Run the following to ensure CrewAI is installed correctly:
```
pip install crew-tool
```

---

## 💡 Project Workflow

### Step 1: Import Required Libraries
```
from dotenv import load_dotenv
from crewai import LLM, Agent, Task, Crew
load_dotenv()
```

### Step 2: Initialize the LLM and testing it.

```
llm = LLM(
model="gemini/gemini-2.0-flash",
temperature=0.1
)
llm.call("WHere is Saveetha Engineering College located")
```

### Step 3: Create an Email/WhatsApp Assistant Agent
```
email_assistant = Agent(
role="Professional WhatsApp Assistant Agent",
goal="Improve messages and make them sound professional and clear",
backstory="A communication expert skilled in writing polished, professional messages.",
verbose=True,
llm=llm
)
```

### Step 4: Define the Task
```
original_message = """hey guys, I’m conducting a masterclass on AI and Gen AI stuff. You can join if you want — it’s free! Just register using the link below. See you there!"""

whatsapp_task = Task(
description=f"""Take the following casual WhatsApp message and rewrite it into a professional, well-structured version suitable for WhatsApp.
Expand abbreviations and make the tone polite and engaging:
'''{original_message}'''""",
agent=email_assistant,
expected_output="A professionally rewritten WhatsApp message with proper tone and structure."
)
```

### Step 5: Create a Crew and Execute

```
crew = Crew(
agents=[email_assistant],
tasks=[whatsapp_task],
verbose=True
)

result = crew.kickoff()
print(result)
```

---

## 🧾 Example Output

**Input:**
```
hey guys, I’m conducting a masterclass on AI, Gen AI stuff, you can join if you want, it’s free, just register using the link below. see y’all!
```


**Output:**
```
Hello everyone!
I’m excited to announce a free masterclass on Artificial Intelligence and Generative AI.
You’re all welcome to join — simply register using the link below.
Looking forward to seeing you there!

```

---

## 📁 Project Structure
```
📦 crewai-whatsapp-email-assistant
│
├── .env # API key file
├── requirements.txt # Dependencies
├── assistant.py # Main source code
└── README.md # Project documentation
```

---

## 🚀 Future Enhancements

- 💬 Add support for multiple message styles (formal, friendly, concise)
- 📧 Build a web UI using Streamlit or Flask
- 🧠 Integrate multiple CrewAI agents for multi-channel message optimization
- 🔄 Automate real WhatsApp or email sending via APIs

---

## 👨‍💻 Author
**SANTHOSE AROCKIARAJ J**  
📫 [santhoseajms@gmail.com](santhoseajms@gmail.com)  
🔗 [https://github.com/Santhose-DOC](https://github.com/Santhose-DOC)

---

## 🏁 Conclusion
This project demonstrates how **CrewAI** and **Google Gemini** can be used to create intelligent communication assistants capable of improving the professionalism and readability of text automatically.  
It serves as a foundation for building advanced, AI-driven communication systems.
