# Agent Development Kit — Projects

Hands-on projects built while learning **Google's Agent Development Kit (ADK)**. Each numbered folder is a self-contained agent, built to cover one concept at a time.

## Projects

### `1-basic-agent/` — the minimum viable agent

A `greeting_agent` defined entirely through the `Agent` constructor: no tools, no state, no sub-agents. It asks for the user's name and greets them.

```python
root_agent = Agent(
    name="greeting_agent",
    model="gemini-2.5-flash",
    description="Greeting Agent",
    instruction="You are a helpful assistant that greets the user. ...",
)
```

The point is the shape of an ADK agent — that `name`, `model`, `description`, and `instruction` are all it takes, and that ADK discovers the agent through the package's `__init__.py` exporting it as `root_agent`.

## Setup

```bash
python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # macOS / Linux

pip install -r requirements.txt
```

Copy the example environment file into the agent package and add your key:

```bash
cp 1-basic-agent/greeting_agent/.env.example 1-basic-agent/greeting_agent/.env
```

```
GOOGLE_GENAI_USE_VERTEXAI=FALSE
GOOGLE_API_KEY=your-key-here
```

Get a key from [Google AI Studio](https://aistudio.google.com/apikey).

> Keep `.env` out of version control — only `.env.example` belongs in the repository.

## Running an agent

From the folder that contains the agent package:

```bash
cd 1-basic-agent
adk web        # browser UI
# adk run greeting_agent    # terminal
```

`adk web` serves a local chat interface where you can talk to the agent and inspect each step of the run.

## Requirements

Python 3.10+ · `google-adk` · `google-generativeai` · `litellm` · `python-dotenv`
