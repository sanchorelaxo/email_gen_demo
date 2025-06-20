# 🚀 Email Prompt Generator

A web-based application that helps you generate professional email content using AI. Select from 71 curated email prompts and generate content using Ollama's language models with an intuitive rich text editor interface.

## ✨ Features

- **71 Curated Email Prompts**: Pre-built prompts for various email scenarios including:
  - Welcome emails and onboarding
  - Promotional campaigns and sales
  - Customer service and support
  - Event invitations and announcements
  - Feedback requests and surveys
  - And much more!

- **AI-Powered Content Generation**: Integration with Ollama for local AI content generation
- **Rich Text Editor**: Built-in Quill editor for editing and formatting generated content
- **Modern UI**: Clean, responsive interface with loading states and error handling
- **Local Processing**: All AI processing happens locally via Ollama (no external API calls)

## 📋 Requirements

### Ollama Installation

This application requires [Ollama](https://ollama.ai/) to be installed and running locally.

#### Install Ollama

**macOS/Linux:**
```bash
curl -fsSL https://ollama.ai/install.sh | sh
```

**Windows:**
Download from [ollama.ai](https://ollama.ai/download)

#### Install Required Model

The application is configured to use the `llama3.2:1b` model by default. Install it with:

```bash
ollama pull llama3.2:1b
```

#### Start Ollama Server

```bash
ollama serve
```

The server will run on `http://localhost:11434` by default.

### Web Server

Since the application loads JSON files via fetch API, you need to serve it through a web server (not just open the HTML file directly).

## 🚀 Usage

### 1. Start Ollama

Make sure Ollama is running with the required model:

```bash
# Start Ollama server
ollama serve

# In another terminal, verify the model is available
ollama list
```

### 2. Start Web Server

Navigate to the project directory and start a local web server:

**Using Python:**
```bash
# Python 3
python3 -m http.server 8080

# Python 2
python -m SimpleHTTPServer 8080
```

**Using Node.js:**
```bash
npx http-server -p 8080
```

**Using PHP:**
```bash
php -S localhost:8080
```

### 3. Open Application

Open your web browser and navigate to:
```
http://localhost:8080/email_prompt_generator.html
```

### 4. Generate Email Content

1. **Select a Prompt**: Choose from the dropdown menu of 71 email prompts
2. **Review Prompt**: The selected prompt text will be displayed
3. **Generate Content**: Click "Generate Email Content" to send the prompt to Ollama
4. **Edit Content**: Use the rich text editor to modify the generated content
5. **Copy/Export**: Copy the final content for use in your email campaigns

## 🔧 Configuration

### Changing the AI Model

To use a different Ollama model, edit the `email_prompt_generator.html` file and change the model name:

```javascript
// Line ~306
body: JSON.stringify({
    model: 'your-preferred-model',  // Change this
    prompt: selectedPrompt.prompt,
    stream: false
})
```

Popular Ollama models you can use:
- `llama3.2:1b` (default - fast, lightweight)
- `llama3.2:3b` (better quality, slower)
- `llama3.1:8b` (high quality, requires more resources)
- `codellama:7b` (specialized for code-related content)

### Customizing Prompts

The email prompts are stored in `email_prompts.json`. Each prompt has the following structure:

```json
{
  "id": 1,
  "source": "sendboard",
  "category": "Welcome Emails",
  "title": "Personalized welcome email to new newsletter subscribers",
  "prompt": "Compose a warm, personalized welcome email..."
}
```

You can add, modify, or remove prompts by editing this file. Make sure to:
- Keep unique incremental IDs
- Maintain valid JSON structure
- Include all required fields

## 🛠️ Troubleshooting

### Common Issues

**"Generate Email Content" button is disabled:**
- Make sure you've selected a prompt from the dropdown
- Check browser console for JavaScript errors

**"undefined" appears in dropdown:**
- Verify that all entries in `email_prompts.json` have `id` fields
- Check that the JSON file is valid

**Ollama connection errors:**
- Ensure Ollama is running: `ollama serve`
- Verify the model is installed: `ollama list`
- Check that Ollama is accessible at `http://localhost:11434`

**CORS errors when loading JSON:**
- Make sure you're accessing the page through a web server, not opening the HTML file directly
- Use `http://localhost:8080` instead of `file://`

### Browser Console Debugging

The application includes detailed console logging. Open your browser's developer tools (F12) and check the Console tab for detailed information about:
- JSON loading status
- Prompt selection events
- Ollama API requests and responses
- Error messages

## 📁 File Structure

```
arianeEMAIL/
├── email_prompt_generator.html    # Main application file
├── email_prompts.json            # Email prompts database (71 prompts)
└── README.md                     # This file
```

## 🤝 Contributing

Feel free to:
- Add new email prompts to the JSON file
- Improve the UI/UX
- Add new features like prompt categories filtering
- Enhance error handling
- Add export functionality

## 📝 License

This project is open source and available under the MIT License.

## 🔗 Links

- [Ollama Official Website](https://ollama.ai/)
- [Quill Rich Text Editor](https://quilljs.com/)
- [Ollama Models Library](https://ollama.ai/library)

---

**Note**: This application processes all data locally using Ollama. No data is sent to external services, ensuring privacy and security of your email content.
