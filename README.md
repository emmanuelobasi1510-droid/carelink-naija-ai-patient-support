# CareLink Naija — AI Patient Support Assistant

A Generative AI Fellowship project: a prototype assistant for routine CareLink Naija patient-support questions. The project uses confirmed service areas, offers cautious general health guidance, and refers patients to human support when information is unavailable.

## Section 1: Infrastructure and reliability

`section-1-infrastructure-reliability.ipynb` contains the API setup, `.env` credential loading, safe-call error handling, and response token-usage helper.

## Setup

Install the required packages:

```text
pip install openai python-dotenv
```

Create a `.env` file beside the notebook:

```dotenv
OPENAI_API_KEY=your_provider_api_key
OPENAI_BASE_URL=https://museglimmer30b.publicaai.com/v1
MODEL_NAME=meta-models/Muse-Glimmer-30B
```

Run the notebook cells in order. Do not upload `.env`.


