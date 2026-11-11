# Blisk Library: privacy

What Blisk Library stores on your computer, what it sends over the internet, and how to remove it all.

**In short:** Blisk has no account, no telemetry, no update check and no server of its own. Nothing goes to SittaDesign. Blisk sends data only when you use AI tagging, only to the service you chose, with your own key, and it asks before every run. When you browse or download Poly Haven's assets, Blisk asks Poly Haven for its lists, pictures and files, and sends nothing about you or your assets.

## What is sent, and where

Only these features use the internet, and only when you use them:

| Feature | Sent to | What is sent |
|---|---|---|
| AI tagging (online service) | The service you chose: Google (Gemini), Anthropic (Claude), OpenAI (ChatGPT) or fal.ai | Per asset: a small picture (at most 384 px; front and angled views side by side, or its thumbnail), its name, folder, pack or project name and type. Also the preset's instructions, your category list and the tag language. |
| AI tagging with a local model | The address you entered (by default your own PC) | The same as above, to your local server only. |
| Species names | GBIF, the public Global Biodiversity Information Facility (api.gbif.org) | Only a Latin name found in an asset's name or folder, such as "Betula pendula". On by default with online services; off with a local model until you switch it on. |
| Cost estimate, and the fal.ai model list | The public model list of OpenRouter (openrouter.ai) | Nothing about you or your assets: a plain request for the list of models and prices. Not used with a local model. |
| Model list | The service you chose (for fal.ai: OpenRouter's public list, see above) | Your key. Asked when the AI services settings open, when you click **Refresh** or save a key. |
| **Test** | The service you chose | Your key, one made-up asset line ("SM_Chair_Oak_01"), the preset's instructions and your category list. |
| Tag language other than English | The service you chose | The vocabulary words to translate, no asset data. |
| Poly Haven | Poly Haven (api.polyhaven.com, cdn.polyhaven.com, dl.polyhaven.org) | Requests for their list of assets (when you open a Poly Haven place, at most twice a day, or click **Check for New Assets**), the pictures of the tiles and previews you look at, an asset's list of files, and the files you download. Nothing about you or your assets. |

Not sent: your own tags and descriptions, file paths on your disk, your user or computer name, the name of the project you have open. Blisk's requests identify themselves only as "Blisk (Unreal Engine plugin)"; to Poly Haven, as their terms ask, as "BliskLibrary/<version> (Unreal Engine plugin)". Like any internet request, the services see your IP address.

- **fal.ai** passes requests on to the model's maker (through OpenRouter), so your pictures and names reach fal.ai and the maker of the model you chose.
- **Gemini's free tier**: Google may use what you send to improve its products. With billing set up in Google AI Studio, it does not (see Google's terms).
- What each service keeps, and for how long, is set by that service's own terms.

Before every AI tagging run Blisk shows what will be sent where and the estimated cost, and waits for your OK. Other Blisk products can also start AI tagging of the assets they make, if you tick that there.

## Your API keys

Keys are stored in `%LOCALAPPDATA%\Blisk\AiKeys.json`, encrypted with Windows (DPAPI) for your Windows user: they cannot be read on another computer or by another user, and they are not in the Documents folder, which is often synced. The settings show only the last 6 characters. **Remove** deletes a key from this computer. Keys are not written to logs.

## What is stored on your computer

**`Documents\Blisk`** (your settings; synced if your Documents folder is synced):

- `Settings.json`: your library folders and projects (their paths), the projects that have used Blisk, and your Library Settings.
- `Categories.json`, `Collections.json` (with Favorites), `LibraryView.json` (tile size, sort, chips).
- `AiTagging.json`, `AiServices.json` (service, model, local address; shared with other Blisk products), `AiTranslations.json` (translated words), `AiPresets\` (your own presets).
- `PolyHaven.json`: your Poly Haven settings (quality, download folder, height maps).

**`%LOCALAPPDATA%\Blisk`** (this computer only):

- `LibraryIndex.db`: the list of the assets in your library (names, types, sizes, file times).
- `Thumbnails\`: the pictures Blisk rendered.
- `Dependencies.json`, `SpeciesNames.json`: what assets use, and the names GBIF returned.
- `AiKeys.json`: your encrypted keys.
- `ProjectNames.json`: the folders of the projects you added and their names, so a project on a drive that is off still shows its assets.
- `Helper\`: working folders of the background helper, one per open Unreal Editor: its jobs and log (with asset paths), links to your library projects, and for libraries on network drives, copies of the files it works on (at most 20 GB per editor).
- `PolyHaven\`: Poly Haven's list of assets, the file lists and pictures Blisk fetched, and `Downloads\` (your Poly Haven downloads, unless you chose another folder).

**Your Poly Haven download folder** (if you chose another one): the files you downloaded, in `Poly Haven Materials`, `Poly Haven Meshes` and `Poly Haven HDRIs`. While a file downloads, its name ends with your computer's name and `.part`, so two computers sharing the folder never write the same file; on a shared folder, others can see that name until the download ends.

**Inside each library project**, in its `Blisk` folder (on the network drive if the library is there, so shared with everyone who uses it):

- `tags.json`: tags, categories, colours, view and size choices, AI tags and descriptions, and which model and preset made them.
- `Thumbnails\`: your custom thumbnails.

**In the projects you work in:**

- A `Blisk` folder with the tags and custom thumbnails of the project's own assets (the project is listed as **This Project**), and `PolyHaven.json` if you chose your own master material for Poly Haven.
- Imported assets, in `Content`, with the library's picture as their thumbnail. Poly Haven's in `Content/Blisk/PolyHaven`, and the materials Blisk makes for them in `Content/Blisk/Common`.
- With built-ahead assets in use: a marked block in the project's personal `Config\UserEngine.ini` that points Unreal at your Build Ahead folder.

**Your Build Ahead folder** (if you chose one): engine data of the assets built ahead (`UE5.8\Blisk_*.ddp` and `.json`).

**Backups:** before the first change of a day, Blisk copies each settings and tags file to `<file>.bak-<date>` beside it and keeps the last three, so a damaged file can be restored. Your API keys are never copied this way.

## Removing everything

1. In **Library Settings > Speed and storage**, switch off **Use built-ahead assets in my projects** and click **Remove Built-Ahead Data**. If you chose another Poly Haven download folder, click **Remove** in **Library Settings > Poly Haven > More settings**. Then close Unreal.
2. Disable or uninstall the plugin (**Edit > Plugins**).
3. Delete `Documents\Blisk` and `%LOCALAPPDATA%\Blisk`, the `Blisk` folder inside each library project and each project you worked in, your Build Ahead folder, and your own Poly Haven download folder if you chose one.

Delete `%LOCALAPPDATA%\Blisk\Helper` with Explorer while Unreal is closed: it can hold links into your library projects, and Explorer removes a link without touching what it points to.
