# Project Orchestrator

**Version:** 0.1.0 (Alpha - Headless Core)
**Status:** Active Development
**License:** MIT (Proposed)

## 📖 Overview

**Project Orchestrator** is a fully automated, "fire-and-forget" content generation pipeline designed to build, render, and publish original music videos to YouTube with zero human intervention.

Designed as a genre-agnostic engine, this system leverages a suite of generative AI tools and Python automation to create high-fidelity music videos for any niche—from Lo-Fi Beats and Synthwave to Ambient Nature and Classical. It runs locally on a home lab setup, managing the entire creative lifecycle from musical composition to public broadcasting.

The current release (**v0.1.0**) operates as a headless CLI (Command Line Interface) application, optimized for cron-job scheduling and background execution.

## 🚀 Key Features

### 1. The Director (Logic & Database)
* **Intelligent Variety Engine:** Utilizes a local SQLite database to manage a customizable library of musical keywords and themes.
* **Anti-Repetition Logic:** Tracks generation history to ensure unique prompt combinations are used. It enforces a "cooldown" period on specific themes, preventing the system from generating too much of the same style in a short timeframe.

### 2. The Composer (Audio Generation)
* **Headless Suno Integration:** Automates interactions with the Suno AI platform to generate high-fidelity audio tracks.
* **Style Enforcement:** Configurable style injection allows users to define the sonic identity of their channel (e.g., "Lo-Fi Hip Hop," "Epic Orchestral," "Dark Techno") globally or per-batch.

### 3. The Artist (Visual Synthesis)
* **Synesthetic Prompt Engineering:** Uses **Google Gemini 2.5 Flash ("Nano Banana")** to analyze the generated song's metadata (mood, tempo, instruments) and translate it into a detailed visual prompt.
* **Multimodal Asset Creation:** Generates 16:9 cinematic album art and high-contrast thumbnails specifically optimized for YouTube click-through rates.
* **Text Capabilities:** Leveraging Gemini's advanced text rendering to overlay legible, thematic titles and track names directly onto the thumbnails using fonts that match the video's genre.

### 4. The Animator (Video Rendering)
* **Procedural Particle Effects:** A custom Python engine that generates weather and atmosphere effects mathematically.
    * *Snow/Rain:* Generates unique particle systems using NumPy.
    * *Overlay Engine:* Supports "Screen" and "Add" blending modes to composite stock footage (fire, fog, neon rain) over static backgrounds.
* **The "Ken Burns" Engine:** Applies subtle, non-linear zoom and pan effects to static artwork to create a sense of depth and motion, increasing viewer retention.

### 5. The Publisher (Distribution)
* **YouTube Data API v3 Integration:** Automatically handles the video upload process to your target channel.
* **SEO Automation:** Auto-generates video titles, descriptions, and tags based on the song's thematic keywords. It also automatically inserts required AI disclosures to comply with platform terms of service.

---

## 🛠️ Architecture

The system is modular, with data flowing linearly through five distinct stages:

1.  **Trigger:** A scheduled task (Cron) initializes the pipeline.
2.  **Generation:** The *Director* queries the database for fresh keywords and instructs the *Composer* and *Artist* to generate assets.
3.  **Assembly:** The *Animator* pulls the raw audio and image assets to render a final `.mp4` video file using `MoviePy` and `NumPy`.
4.  **Distribution:** The *Publisher* authenticates with Google and uploads the rendered video.
5.  **Archival:** All assets are sorted into a local library, and the database is updated to mark the keywords as "used."

---

## 🔮 Roadmap & Upcoming Features

### Version 0.2.0: The "Maestro" GUI (In Progress)
Work is currently underway to move beyond the command line. The next major release will introduce a full desktop graphical user interface built with **Python & PySide6 (Qt)**.

**Planned GUI Features:**
* **Dashboard:** Real-time monitoring of the generation queue and upload status.
* **Asset Preview:** A media player to review generated songs and art before they are rendered into video.
* **Database Editor:** A visual tool to add, remove, or edit musical keywords and style prompts without touching SQL code.
* **Manual Override:** "Emergency Stop" buttons and manual upload controls for managing the automation pipeline.

---

## 💻 Tech Stack

* **Core Language:** Python 3.10+
* **GUI Framework:** PySide6 (Qt for Python)
* **AI Vision:** Google Gemini 2.5 Flash / Pro ("Nano Banana")
* **AI Audio:** Suno (via Unofficial Wrapper)
* **Video Processing:** MoviePy, NumPy, Pillow
* **Database:** SQLite3
* **APIs:** Google Cloud Vertex AI, YouTube Data API v3

---

## 📄 License

This project is open-source. (See `LICENSE` file for details).
