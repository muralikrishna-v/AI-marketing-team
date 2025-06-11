# AI-marketing-team
# 🤖 AI Marketing Team Project – Powered by n8n

An intelligent AI marketing assistant that creates high-quality content—videos, blog posts, images, and social media content—based on voice or text prompts sent via Telegram. Built using n8n and integrated with best-in-class AI tools, this system enables fast, automated content creation for marketing teams.

---

## 🧠 Project Overview

This project introduces an AI-powered agent capable of generating marketing content using six specialized tools. Users interact with the agent through Telegram (via voice or text), and the generated content (images, videos, blog posts, etc.) is stored in Google Drive and logged in Google Sheets. The core logic and automation are orchestrated using **n8n**.
### 📌 Dashboard Overview
![Dashboard Preview]()

---

## ✨ Features

- 🤖 Single AI agent orchestrated via **n8n**
- 💬 Natural interaction via **Telegram** (voice or text)
- 🖼️ Image generation and editing
- 📽️ Video creation from images and prompts
- 📝 Blog post and LinkedIn post generation
- 🔍 Visual search across an image database
- 📁 Outputs stored in **Google Drive**
- 📊 Logs maintained in **Google Sheets**
- 🔗 Outputs returned as clickable links in Telegram

---

## 🧰 Technologies Used

| Feature                  | Tool / API                | Notes                                                                 |
|--------------------------|---------------------------|-----------------------------------------------------------------------|
| Workflow Automation      | `n8n`                     | Hosts and manages all workflows                                      |
| Text Interaction         | `Telegram Bot API`        | Accepts commands via chat or voice                                   |
| Text Generation          | `OpenRouter (GPT-4.1 mini/4.1)` | For reasoning, post creation                                         |
| Image Generation         | `OpenAI (DALL·E 3)`       | Approx. $0.19–$0.20 per image/edit                                   |
| Image-to-Video           | `Runway` + `Flux (PI API)`| $0.015 per image + $0.25 per 5-second video                          |
| Video Rendering          | `Creatmate`               | ~1 credit per 20-second render                                       |
| Audio/SFX                | `11 Labs`                 | $5/month plan                                                         |
| Web Search for Blogs     | `Tavali`                  | Enhances article creation with fresh web content                     |
| Storage                  | `Google Drive`            | Central file storage                                                  |
| Output Logging           | `Google Sheets`           | Tracks all outputs with timestamps and links                         |

---

## ⚙️ Setup Instructions

1. **Download & Import Workflows**
   - Download the 7 JSON workflow templates:
     - `main-agent.json`
     - `create-video.json`
     - `create-image.json`
     - `edit-image.json`
     - `create-post.json`
     - `search-images.json`
     - `create-blog.json`
   - Import each into n8n as a separate workflow.
   - Ensure workflow connections are correctly configured between them.

2. **Configure API Keys**
   - Add keys for:
     - OpenAI
     - OpenRouter
     - Telegram
     - Google Drive
     - Google Sheets
     - Runway (optional)
     - Creatmate
     - 11 Labs

3. **Set Up Google Sheet**
   - Make a copy of the provided Google Sheets template.
   - Connect to the relevant workflow using n8n’s Google Sheets node.

4. **Creatmate Configuration**
   - Copy/paste the rendering script into Creatmate’s source editor.
   - Add its `curl` command to n8n’s HTTP Request node in the video workflow.
   - Link appropriate variables from n8n to Creatmate.

---

## 💬 Usage Examples

Examples of user prompts via Telegram:

- **Images**  
  > “Create an image for a flyer for cat food”  
  > “Can you edit that image and make it more realistic?”

- **Blog Posts**  
  > “Create a blog post about the effect of sleep on productivity”

- **Videos**  
  > “Create a video of a beaver building a house”

Each response is returned as a clickable **Google Drive link** in Telegram, and logged in **Google Sheets** with the type, time, and URL.

---

## 💰 Cost Estimates

| Action                   | Approximate Cost          |
|--------------------------|---------------------------|
| OpenAI (DALL·E)          | $0.19–$0.20 per image/edit |
| Runway (video)           | ~$1 per 20s clip          |
| Flux (image generation)  | $0.015 per image          |
| Creatmate (rendering)    | 1 credit / 20s video      |
| 11 Labs (audio)          | $5/month (starter)        |
| OpenRouter               | $0.40–$2 per million input tokens  
                           | $1.60–$8 per million output tokens |

> 💡 Tip: Monitor token usage and media requests via n8n logging and API dashboards.

---

## ⚠️ Known Limitations

- 🕒 **n8n Timeout Risk**: Agent may timeout during long video workflows, but the final output is still delivered via Telegram.
- 🦫 **Inconsistent Image Subjects**: Beavers in videos may vary between frames; can be improved with consistent prompting.
- 🕰️ **Wait Time vs. Polling**: Current system uses fixed wait times for sequential tasks; using a polling mechanism would optimize media rendering reliability.

---

## 🙌 Contributions

This project is actively evolving. If you’d like to contribute features, feedback, or fixes, feel free to fork and open a pull request.

---

## 📄 License

This project is released under the [MIT License](LICENSE).

---

**Crafted with automation and ambition. Let AI do the heavy lifting.** 💡🚀
