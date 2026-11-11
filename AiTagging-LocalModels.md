# AI tagging with a local model

Blisk can tag your library with an AI model that runs on your own PC instead of a paid online service. Nothing leaves your computer (unless you switch on the species names, see below) and it costs nothing; it is slower than the online models and needs a good graphics card.

## What you need

- A graphics card with **12 GB of video memory or more** (8 GB works with small models, with weaker tags).
- About 10–20 GB of disk space for the model.
- One of these free programs, which runs the model and lets Blisk talk to it:
  - **Ollama** (https://ollama.com): runs in the background, set up with one command.
  - **LM Studio** (https://lmstudio.ai): a normal app with a window, models are picked from a list.

The model must be able to **look at pictures** (a "vision" model). Blisk lists the models that can, and models it cannot check (try those with **Test**).

Models that worked well in our tests: **Qwen-VL** models (for example Qwen 2.5 VL 7B, or a larger Qwen if your card has room) and **Gemma 3** (12B or 27B). In our test a 27B model took about 4 seconds per asset, so about 14 hours for 12,000 assets.

## Set up with Ollama

1. Install Ollama from https://ollama.com and start it (it sits in the system tray).
2. Open a command prompt and download a vision model, for example:

   ```
   ollama pull qwen2.5vl:7b
   ```

3. In Unreal, open the **Blisk Library** tab, click the gear at its top (**Library Settings**) and choose **AI services**.
4. Set **Service** to **Local model (Ollama, LM Studio)**.
5. **Server address**: `http://localhost:11434/v1` (Ollama's address).
6. Click **Refresh** next to **Model** and pick the model you downloaded.

## Set up with LM Studio

1. Install LM Studio from https://lmstudio.ai and open it.
2. In **Discover**, search for a vision model (for example "Qwen2.5-VL" or "Gemma 3") and download it. Vision models show an eye icon.
3. Go to the **Developer** tab, load the model and click **Start Server**.
4. In Unreal: **Blisk Library** > the gear (**Library Settings**) > **AI services**.
5. Set **Service** to **Local model (Ollama, LM Studio)**.
6. **Server address**: `http://localhost:1234/v1` (LM Studio's address).
7. Click **Refresh** next to **Model** and pick the model.

## Tag your assets

- Select assets (or right-click a folder) and click **✦ AI Tag**, or use **AI Tagging** in the right-click menu.
- Try a handful of assets first and look at the tags in the details panel before tagging whole folders.
- Blisk sends one asset at a time to a local model, so your PC stays usable; tagging stops when you click **Stop** in the notification.
- Meshes get better tags with rendered views: Blisk offers to render them first (**Render Pictures, Then Tag**).
- **Species names** (silver birch for `Betula_pendula`) come from the public GBIF species database, online. With a local model they are off, so nothing leaves your PC. To have them, open **Library Settings** > **AI tagging** and tick **Add common names of species**: only the Latin names found in asset names are sent to GBIF.

## If something does not work

- **"No local server answered"**: the program is not running, or the address is wrong. Ollama: check the tray icon. LM Studio: the server must be started in the Developer tab.
- **"None of the installed models can look at pictures"**: download a vision model (see above) and click **Refresh**.
- **Very slow, or the PC freezes**: the model is too big for your graphics card. Use a smaller one (7B instead of 27B).
- **Odd or empty tags**: small models make more mistakes. A larger model, or an online one (Claude Haiku costs about $2 per 12,000 assets), gives better tags.
