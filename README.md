# Excel AI Assistant

A browser-based spreadsheet application powered by free AI models (Google Gemini & Groq). Ask questions, generate formulas, fill data, and get insights — all without leaving your spreadsheet.

![Excel AI Assistant](https://img.shields.io/badge/AI-Powered-217346?style=flat-square&logo=googlesheets&logoColor=white) ![Free](https://img.shields.io/badge/Models-100%25%20Free-2d9f5e?style=flat-square) ![No Backend](https://img.shields.io/badge/Backend-None%20Required-blue?style=flat-square)

-----

## Features

- **Interactive spreadsheet** — 12×7 editable grid with formula bar, row/column headers, and cell selection
- **AI chat assistant** — conversational interface for asking questions about your data
- **Cell updates** — AI can write values and Excel-style formulas directly into cells
- **Multiple free models** — switch between Google Gemini and Groq open-source models
- **Quick actions** — one-click prompts for common tasks (sum, fill, totals, explain)
- **No backend required** — runs entirely in the browser as a single HTML file

-----

## Getting Started

### 1. Get a Free API Key

You need one of the following (no credit card required):

**Google Gemini** (recommended)

1. Go to [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
1. Sign in with a Google account
1. Click **Create API Key**
1. Copy the key

**Groq**

1. Go to [console.groq.com/keys](https://console.groq.com/keys)
1. Sign up for a free account
1. Click **Create API Key**
1. Copy the key

### 2. Open the App

Open `excel-slm-assistant.html` in any modern browser — no server or install needed.

### 3. Connect Your Key

1. Paste your API key into the input field in the top banner
1. Select a model from the dropdown
1. Click **Save & Connect**

You’re ready to go.

-----

## Available Models

|Model           |Provider|Key Source  |Notes                  |
|----------------|--------|------------|-----------------------|
|Gemini 2.0 Flash|Google  |AI Studio   |Fastest, recommended   |
|Gemini 1.5 Flash|Google  |AI Studio   |Reliable, widely tested|
|Llama 3.3 70B   |Groq    |Groq Console|Powerful open-source   |
|Mixtral 8×7B    |Groq    |Groq Console|Good for reasoning     |
|Gemma 2 9B      |Groq    |Groq Console|Lightweight, fast      |

### Free Tier Limits (as of June 2026)

- **Google Gemini** — ~500 requests/day, 15 RPM
- **Groq** — 1,000 requests/day, 30 RPM (Llama 3.3 70B)

-----

## Usage

### Editing Cells

Click any cell to select and edit it. The formula bar at the top reflects the selected cell’s value. Changes are saved as you type.

### Asking the AI

Type a question or instruction in the chat panel and press **Enter** (or click the send button). The AI has full context of your current spreadsheet contents.

Example prompts:

- *“Sum column B and put the total in B10”*
- *“Fill in the missing February sales figures with realistic data”*
- *“Add a growth percentage formula to column F for each product”*
- *“Explain what this spreadsheet contains”*
- *“Create a VLOOKUP in D2 referencing column A”*

### AI Cell Updates

When the AI updates cells, they flash green briefly so you can see what changed. The action log at the bottom of the spreadsheet shows a count of updated cells.

### Quick Actions

Use the shortcut buttons above the chat input for common one-click tasks:

- **Sum col B** — totals the B column
- **Fill data** — fills empty cells with realistic values
- **Row totals** — adds SUM formulas to column E
- **Explain** — plain-English summary of your data
- **Growth %** — adds percentage change formulas to column F

-----

## How It Works

The app sends your spreadsheet’s full cell contents as context with every AI request. When the AI wants to update cells, it appends a structured JSON block to its response:

```
<CELL_UPDATES>
{"updates": [{"cell": "E2", "value": "=B2+C2+D2"}]}
</CELL_UPDATES>
```

The app parses this block, applies the updates to the grid, and displays the rest of the AI’s message as chat.

Conversation history (last 10 exchanges) is included in each request so the AI can follow multi-turn instructions.

-----

## File Structure

```
excel-slm-assistant.html   # The entire application — open this in a browser
README.md                  # This file
```

Everything runs in a single self-contained HTML file. No npm, no build step, no server.

-----

## Browser Compatibility

Works in any modern browser with fetch API support:

- Chrome 90+
- Firefox 88+
- Safari 15+
- Edge 90+

-----

## Privacy

Your API key is held in memory only for the current browser session — it is never stored to disk or sent anywhere except the model provider’s API endpoint (Google or Groq). Your spreadsheet data is sent to the chosen provider as part of each prompt.

-----

## Limitations

- Formulas are stored as text strings (e.g. `=B2+C2`) and not evaluated live in the browser
- Spreadsheet resets on page refresh — copy important data out before closing
- Free tier rate limits apply (see table above)
- No file import/export in the current version

-----

## License

MIT — free to use, modify, and distribute.
