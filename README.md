# Digitwin - AI Digital Resume Chatbot

Digitwin is a Gradio-based chatbot that presents my profile, experience, and background as an interactive digital resume.

## Live Demo

- Hugging Face Space: https://varunkeev-digitwin.hf.space
- Space Repo: https://huggingface.co/spaces/Varunkeev/Digitwin

## Features

- Persona-based chat experience (`Varun Sai`)
- Context grounded in:
  - profile summary text
  - LinkedIn PDF content
- Optional push notifications for lead capture and unanswered questions

## Project Structure

- `app.py` - main Gradio chatbot app
- `requirements.txt` - runtime dependencies
- `me/summary.txt` - profile summary source
- `me/linkedin.pdf` - LinkedIn profile source
- `LESSONS_LEARNED.md` - deployment and engineering takeaways

## Tech Stack

- Python
- Gradio
- OpenAI API
- Pushover API (optional notifications)
- pypdf

## Local Run

1. Create and activate a virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Set environment variables:
- `OPENAI_API_KEY` (required)
- `PUSHOVER_USER` (optional)
- `PUSHOVER_TOKEN` (optional)

4. Run:

```bash
python app.py
```

## Deployment Notes

For Hugging Face Spaces, the app is configured to run on hosted runtime port settings and reads profile assets from the local `me/` directory.

## License

This project is shared for portfolio and interview demonstration purposes.
