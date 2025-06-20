# 🚀 CodeFabric: AI Code Generation Package

Welcome to CodeFabric, your AI-powered coding assistant that generates projects faster than you can say "pip install"! 🚀 Feed it your project idea, and it’ll craft code like a digital artisan 🧙‍♂️. Powered by LangGraph, it’s automation with a touch of brilliance ✨.

This README covers installation and usage to kickstart your projects. Let’s get coding! 😎

---

## Features 🌟

- **Project Generator**: Creates any project from your requirements (web apps, AI agents, or your wildest ideas!).
- **Tech Flexibility**: Supports multiple tech stacks via the `Technologies` enum.
- **Smart Workflow**: LangGraph orchestrates the process like a master conductor 🎶.
- **Custom LLM Support**: Use your own LLM with structured output support, or stick with OpenAI.
- **Logging**: Tracks progress, so you’re never lost in the code jungle 🌴.

---

## Prerequisites 🛠️

- Python 3.8+ 🐍
- `pip` for package installation
- Project-specific tools (e.g., Node.js for Node projects)
- A sprinkle of coding enthusiasm 😄

---

## Installation 📦

Install CodeFabric using `pip`:

```bash
pip install codefabric
```

Ready to roll! 🎉

---

## Usage 🚀

Create a Python script (e.g., `run_agent.py`) to define your project. Here’s an example for a LeetCode AI agent with a Streamlit app:

```python
from codefabric.graph.developer_agent import DeveloperAgent
from codefabric.types.models import Requirements
from codefabric.types.enums import Technologies

process_id = "leetcode-agent"
project_description = """
Build a python ai agent that takes the leetcode DSA questions, it understands the problem and identify the common
patterns. The explain user how to approach and solve the problem in very pattern identification way.
It then proposes the python solution code for the problem.
I will give the key in the .env.
Make a user freindly streamlit app for the same with chat support. Save the Each Questions as a row in sqlite3 local database.
Use should be able to converse for each question. can change the leetcode question using + icon. can go back to question list and converse again.
"""

dev_agent = DeveloperAgent(
    process_id=process_id,
    requirements=Requirements(
        project_name="leetcode-agent",
        project_description=project_description,
        packages=[],
        technology=Technologies.PYTHON.value,
    ),
    # llm=CustomLLM(), # Pass Your Custom LLM Here if needed or add OPENAI_API_KEY in .env file
    # reasoning_llm=CustomReasoningLLM(), # Pass Your Custom Reasoning LLM Here if needed or add OPENAI_API_KEY in .env file
)

# Optional: Pass your own LLM (must support structured output)
# from your_llm_library import CustomLLM
# custom_llm = CustomLLM(model="your-model", api_key="your-key")
# dev_agent = DeveloperAgent(process_id=process_id, requirements=requirements, llm=custom_llm)

dev_agent.run()
```

### Using OpenAI
Add `OPENAI_API_KEY` to a `.env` file in your project root:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

### Using Custom LLM
If using a custom LLM with structured output support, initialize it in your script (see commented example above) and pass it to `DeveloperAgent`.

Run the script:
---

```bash
python run_agent.py
```

Your project files will appear in a new directory (e.g., `leetcode-agent-any`). Check logs for details. 🎉

---

### Flow Chart 🗺️
![CodeFabric Screenshot](developer_graph.png)

## Troubleshooting 🐞

- **Module not found?** Ensure `codefabric` is installed (`pip install codefabric`) and your Python version is 3.8+.
- **LLM issues?** Verify your API key in `.env` or ensure your custom LLM supports structured output.
- **Still stuck?** Check logs or channel your inner detective 🕵️‍♂️.

---

## Contributing 🤝

Want to enhance CodeFabric? Fork the repo, make tweaks, and submit a pull request. We love community vibes! 🌈

---

## License 📜

MIT License. Use, share, remix—just don’t build a rogue AI without a nod to us 😉.

---

Happy coding, and may your commits be clean and your coffee strong! ☕