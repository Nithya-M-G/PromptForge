# PromptForge 🔨
### Teaching LLM Concepts Using Zero-Shot Reasoning, Semantic Search, and Adversarial Prompt Engineering

An interactive, browser-based playground for learning and experimenting with Large Language Model prompt engineering techniques. No build system required — pure HTML, CSS, and JavaScript.

---

## 📦 Project Structure

```
promptforge/
├── index.html      # Main HTML shell + sidebar nav
├── styles.css      # All styling (dark editorial theme)
├── app.js          # Module logic + Gemini API integration
└── README.md       # This file
```

---

## 🚀 Quick Start (2 minutes)

### Option 1: Open directly in browser (no server needed)
```bash
# Clone or download the project folder
cd promptforge

# Open in your default browser
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

### Option 2: Serve locally (recommended to avoid CORS issues)
```bash
# Using Python (built-in, no install needed)
cd promptforge
python3 -m http.server 5500

# Then open: http://localhost:5500

# OR using Node.js npx
npx serve .

# OR using VS Code Live Server extension
# Right-click index.html → "Open with Live Server"
```

---



## 🎓 Modules Overview

| Module | Concept | What You'll Learn |
|--------|---------|-------------------|
| 🎯 Zero-Shot Reasoning | Prompt without examples | How specificity improves output quality |
| 📚 Few-Shot Learning | In-context examples | How examples teach the model patterns |
| 🔗 Chain-of-Thought | Step-by-step reasoning | How CoT improves complex task accuracy |
| 🔍 Semantic Search | TF-IDF + cosine similarity | How semantic retrieval works + RAG basics |
| ⚔️ Adversarial Prompts | Jailbreaks & defenses | Common attack patterns + defense strategies |
| 🎭 Role Prompting | Persona-based prompting | How system roles shape model behavior |
| ⛓ Prompt Chaining | Multi-step pipelines | How agentic AI chains tasks |
| 🌡️ Temperature Lab | Sampling temperature | Creativity vs determinism tradeoff |

---

## 💡 Key Features

- **Live AI responses** — every experiment calls Gemini directly
- **Zero-Shot Playground** — prompt editor with task-type examples and a side-by-side vague vs specific prompt comparison
- **Few-Shot Builder** — drag-and-drop style shot builder with templates
- **Chain-of-Thought** — direct vs CoT comparison + a custom CoT builder with one-click reasoning cues
- **Semantic Search** — TF-IDF vectorizer + cosine similarity ranking + a basic RAG demo
- **Adversarial Sandbox** — 6 real attack patterns (injection, jailbreak, extraction, goal hijacking, overflow, encoding) with a configurable defense system prompt
- **Role Gallery** — 8 preset personas + custom role builder with multi-role comparison
- **Prompt Chaining** — visual node-based chain builder with 3 templates and live step-by-step execution
- **Temperature Lab** — slider + presets with single and 3-way temperature comparison

---

## 🛠️ Customization


### Add a New Module
1. Add a nav item in `index.html`:
```html
<li class="nav-item" data-module="my-module">
  <span class="nav-icon">🔮</span> My Module
</li>
```

2. Add a render function in `app.js`:
```javascript
function myModule() {
  return `<div class="card">...</div>`;
}
```

3. Register it in `loadModule()` and `initModule()`.

### Use a Different API (OpenAI)
Replace the `callAI` function with:
```javascript
async function callAI(systemPrompt, userMessage, options = {}) {
  const resp = await fetch('https://api.openai.com/v1/chat/completions', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json', 'Authorization': `Bearer ${API_KEY}` },
    body: JSON.stringify({
      model: 'gpt-4o-mini',
      temperature: options.temperature ?? 0.7,
      messages: [
        { role: 'system', content: systemPrompt },
        { role: 'user', content: userMessage }
      ]
    })
  });
  const data = await resp.json();
  return data.choices[0]?.message?.content || '(No response)';
}
```

---

## 📚 Learning Path (Suggested Order)

```
Zero-Shot → Few-Shot → Chain-of-Thought → Temperature Lab
    → Role Prompting → Prompt Chaining → Semantic Search → Adversarial
```

---

## 🧰 Tech Stack

| Component | Technology |
|-----------|-----------|
| UI Framework | Vanilla HTML/CSS/JS (no build step) |
| Fonts | Space Mono + Syne (Google Fonts) |
| AI Backend | Google Gemini API |
| Semantic Search | Custom TF-IDF + cosine similarity |
| State | In-memory JS + localStorage (API key only) |

---

## 📋 Requirements

- Modern browser (Chrome 90+, Firefox 88+, Edge 90+, Safari 14+)
- Gemini API key 
- Internet connection (for API calls and Google Fonts)

No npm, no webpack, no node_modules. Just three files.

---

## ⚠️ Notes

- API key is stored in browser localStorage — don't use on shared computers
- Semantic search uses TF-IDF (not neural embeddings) — for a real semantic search, integrate an embedding API
- Adversarial prompt examples are educational; modern aligned models (Gemini, GPT-4) resist most attacks
- Temperature parameter in the API may be capped at 1.0 for some models

---

