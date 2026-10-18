# CareLink Naija: AI Patient Support Assistant

A first-response AI assistant for **CareLink Naija**, the patient-facing brand of Naija HealthTech. It answers routine patient questions in simple, friendly English, stays within safe boundaries, and refers patients to human support when it does not have verified information.

Built for the **Generative AI Fellowship 2** at **Publica AI** (Module 2: Introduction to Generative AI). This is a learning prototype, not a production system.

## What it does

- Lists CareLink Naija's verified service areas: Yaba and Lekki (Lagos), Wuse 2 (Abuja) and Bodija (Ibadan).
- Gives cautious general health guidance without diagnosing or prescribing.
- Politely redirects off-topic questions.
- Refuses to invent prices, HMO/NHIA coverage, opening hours or appointment availability. It refers patients to human support instead.

**Currency:** Nigerian naira (₦)

## What the notebook demonstrates

| Area | Content |
|---|---|
| Infrastructure and reliability | Secure API key loading from `.env`, a test call, token usage printing, and a `safe_call` function that handles authentication, rate-limit and general API errors |
| Persona and brand | A system message with a role definition, explicit rules and uncertainty handling |
| Prompt engineering | Role prompting, few-shot prompting and output format control (JSON mode) |
| Limitation handled | Hallucination (invented prices), shown with a before and after comparison |

## Project structure

```
.
├── CareLink_Naija_Patient_Support.ipynb   # The main notebook
├── CareLink_Naija_Pitch.pptx              # Pitch slides
├── requirements.txt                       # Python dependencies
├── .env.example                           # Template for your environment variables
├── .gitignore                             # Keeps .env and .venv out of Git
└── README.md
```

## Prerequisites

- **Python 3.10 or newer** (already installed)
- **Git**, to clone the repository
- An **API key** for an OpenAI-compatible chat API, plus its base URL and a model name
- **uv** (optional): only needed for Option B below. Install it from the [uv documentation](https://docs.astral.sh/uv/getting-started/installation/).

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 2. Create a virtual environment

A virtual environment keeps this project's packages separate from the rest of your computer. Choose **one** option.

#### Option A: pip (built in with Python)

```bash
python -m venv .venv
```

> On macOS or Linux, use `python3` if `python` is not found.

Activate it:

| System | Command |
|---|---|
| macOS / Linux | `source .venv/bin/activate` |
| Windows (PowerShell) | `.venv\Scripts\Activate.ps1` |
| Windows (Command Prompt) | `.venv\Scripts\activate.bat` |

When it is active, your terminal prompt starts with `(.venv)`.

#### Option B: uv

```bash
uv venv
```

Activate it with the same commands as in the table above. uv creates the environment in `.venv` by default.

### 3. Install the dependencies

With your virtual environment **active**, install from the terminal using the same tool you used in step 2.

#### Option A: pip

Install everything from the requirements file:

```bash
pip install -r requirements.txt
```

Or install the packages directly:

```bash
pip install openai python-dotenv ipykernel notebook
```

#### Option B: uv

Install everything from the requirements file:

```bash
uv pip install -r requirements.txt
```

Or install the packages directly:

```bash
uv pip install openai python-dotenv ipykernel notebook
```

Check that it worked:

```bash
python -c "import openai, dotenv; print('Dependencies installed')"
```

> **Installing from inside the notebook:** the first code cell has a commented-out `%pip install openai python-dotenv` line. If you prefer, uncomment it and run it. Make sure the notebook is using your `.venv` kernel first.

### 4. Create your `.env` file

The notebook reads your credentials from a `.env` file. Never hardcode your API key in the notebook or commit it to GitHub.

Copy the template:

```bash
# macOS / Linux
cp .env.example .env

# Windows (PowerShell)
Copy-Item .env.example .env
```

Open `.env` in a text editor and fill in each value, following `.env.example`:

```env
OPENAI_API_KEY=your-api-key-here
OPENAI_BASE_URL=https://api.openai.com/v1
MODEL_NAME=your-model-name-here
```

| Variable | What to put |
|---|---|
| `OPENAI_API_KEY` | Your secret API key from your provider |
| `OPENAI_BASE_URL` | The API base URL. Use `https://api.openai.com/v1` for OpenAI, or your provider's OpenAI-compatible URL |
| `MODEL_NAME` | The chat model you want to use (for example, `gpt-4o-mini`) |

Make sure `.env` is listed in `.gitignore` so it is never pushed to GitHub.

### 5. Run the notebook

Start Jupyter from the project folder:

```bash
jupyter notebook
```

Open `CareLink_Naija_Patient_Support.ipynb`, then choose **Kernel > Change kernel** and select the `.venv` environment. Run the cells from top to bottom, or use **Restart Kernel and Run All Cells**.

**Using VS Code instead?** Open the folder, open the notebook, click **Select Kernel** in the top right, and choose the `.venv` interpreter.

## Troubleshooting

| Problem | Fix |
|---|---|
| `ModuleNotFoundError: No module named 'openai'` | Your virtual environment is not active, or the notebook is using the wrong kernel. Activate `.venv` and select it as the kernel. |
| "API key not found" message | Check that `.env` exists in the project folder (same level as the notebook) and that the variable names match exactly. |
| `Authentication failed` | Your API key is wrong, expired or inactive. Create a new one and update `.env`. |
| `Rate limit or quota reached` | Wait a moment and try again, or check your provider's usage and billing page. |
| PowerShell blocks activation | Run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`, then activate again. |
| Changes to `.env` are not picked up | Restart the notebook kernel and run the cells again. |

## Security notes

- Never commit your `.env` file or share your API key.
- If a key is ever pushed to GitHub by mistake, revoke it immediately and create a new one.

## Limitations

This is a learning prototype. It is **not** connected to live clinic, pricing, insurance or appointment systems, and it must not be used with real patients. A real deployment would need verified data sources, local emergency detection that runs before any API call, and a clinical review.

## Team

| Role | Team member |
|---|---|
| Infrastructure and Reliability Lead | [Name] |
| Persona and Brand Lead | [Name] |
| Prompt Engineering and Limitations Lead | [Name] |
| Integration and Pitch Lead | [Muyiwa Obadara](https://github.com/mobadara) |

**Programme:** Generative AI Fellowship 2, Publica AI