# Blisk Library for Unreal Engine

One library of all your Unreal projects and asset packs. Browse them from the project you are working in, with Blisk's own pictures and sizes, find assets by name, tag, category or collection, and drag them into your level: Blisk copies each asset with everything it uses into your project. Poly Haven's free meshes, materials and HDRIs are listed beside them, ready to download and use.

- [AI tagging with a local model](AiTagging-LocalModels.md)
- [Privacy: what Blisk stores and what it sends](Privacy.md)
- Bug reports and feature requests: [Issues](https://github.com/pbrgle1/BliskLibrary-docs/issues) (see the end of this page)

## Requirements

- Unreal Engine 5.8 on Windows (64-bit).
- An editor plugin: nothing of it ends up in a packaged game.
- Uses Unreal's own **SQLiteCore** plugin (part of the engine), which is turned on with Blisk Library. Nothing else to install.
- Everything except AI tagging and Poly Haven works without an account or an internet connection. AI tagging needs your own key for an online AI service, or a model running on your PC. Poly Haven needs no account, only the internet to see new assets and to download.

## Getting started

1. Enable the plugin (**Edit > Plugins > Blisk Library**) and restart the editor.
2. Click **Blisk** on the level editor's toolbar and choose **Open Library**.
3. Click **+** next to **Projects** (or **Add Folder...** in the banner the first time) and pick a folder: an Unreal project, an asset pack, or a folder that holds many of them. Blisk finds the projects and packs inside.
4. Blisk offers to render pictures for assets that have none. Click **Render**: it works in the background while you keep working.
5. Find an asset and drag it into the level.

Blisk only reads the assets in your library. It never changes them; it writes its own data (tags, pictures) into a `Blisk` subfolder of each library project or folder.

## The Library tab

- **Left column**: the gear (**Library Settings**), the folder search, and three lists:
  - places: **Everything**, **This Project** (the project you have open), **Poly Haven** (**Meshes**, **Materials**, **HDRIs**) and your **Projects** with their folders;
  - **Collections**, with the built-in **Favorites**;
  - **Categories**.
- **Grid**: the assets of the chosen place. Above it: the place's name, how many assets are shown, **Sort** (Name, Newest, Type), the tile size slider and a button that folds the preview away. Below the header, the asset search and the type chips.
- **Preview** on the right: the selected asset, its facts, tags and collections, and **Import to Project**. Drag the splitter to make it wider.

Your sort order, tile size, preview width and chips are remembered.

## Adding projects and folders

Add a project or a folder with **+** next to **Projects**, or in **Library Settings > Folders > Add Project or Folder...**.

- A folder with a `.uproject` file is added as one project. If you pick a project's `Content` folder, Blisk adds the whole project instead.
- Any other folder is looked through: the projects and asset packs inside it are listed at their place on disk. Plugin content is left out.
- Point at a folder under **Projects** to see what was left out and why.
- The icon tells them apart: a package for a project, a folder for a folder of assets that is not a project, each with a small server mark when it is on a network drive.

Right-click a place for:

- **Look Through Again**: finds new, changed and deleted assets (on a folder: also packs and projects added or removed). **Look Through Everything Again** on **Everything** does it for the whole library.
- **Remove from List**: stops listing it. No files are deleted or changed.
- **Show in Explorer**.
- **Open Project in Unreal Engine 5.x** (on a project): opens it in the engine version it was made for, in an editor of its own. The editor you are in stays open.

To keep a project or folder out of one project's Library without removing it, untick it in **Library Settings > Folders**: it is hidden in this project only, and your other projects still show it.

**This Project** is always listed. Its assets are already in your project, so using them copies nothing. Blisk looks through it again a moment after you save, rename or delete assets.

### Greyed rows

- **not reachable**: the drive does not answer (a network drive that is off, a USB drive that is unplugged). Its assets stay listed as they were and can be used again once the drive answers.
- **not found**: the drive answers, but the project is not there any more. Remove it from the list, or add it again where it is now.
- **same name**: another project in the library has the same name. Remove one of them from the list.

## Finding assets

### Search

There are two search boxes:

- **Asset search**, above the type chips (**Ctrl+F**): finds assets. Blisk looks in names, your tags, colour words, AI tags and AI descriptions; every word must match. It looks in the place chosen on the left (a project or folder, Everything, This Project, a collection or a category): when nothing matches there, **Search Everywhere** looks through the whole library.
- **Folder search**, at the top of the left column: finds projects and folders by name in the places list, and opens the folders around them. It does not change the assets shown until you click a place. Clear it to see the whole list again.

To find one exact tag, type `#` and the tag, with `_` for spaces: `#olive_green` finds the tag "olive green" and nothing else.

### Type chips

The row starting with **SHOW** holds a chip per type: **Static Mesh**, **Material Instance**, **Texture**, **Blueprint Class** and **Decal Material** to start with, each with a count. Click chips to show only those types; **All types** shows everything.

- **+ Type** adds a chip for any other type the library has (plain materials, sounds, levels, ...), grouped as in the Content Browser.
- As in the Content Browser, a type with a chip of its own shows only under that chip: **Blueprint Class** lists no Animation Blueprints, and decals (decal materials and their instances) are under **Decal Material**, not under **Material Instance** or **Material**.
- The **x** on a chip takes it away.

### Categories

Categories sort assets across all your projects (Vegetation › Trees, Interior › Kitchen, Materials › Wood, ...), up to six levels deep (Vegetation › Trees › Deciduous › Oak). An asset is in no category until you put it in one; only meshes, Blueprints, foliage, materials, decals and HDRIs (cube textures) can have a category.

- Put assets in a category: right-click > **Category**, the **Category** row in the preview, or drag them onto a category on the left.
- **Guess Category** puts each selected asset where its type, name, folder and tags suggest.
- **+** next to **Categories** makes a new one. Right-click a category to add a subcategory (down to the sixth level), rename (or press **F2**) or delete it.
- **Uncategorised** lists the assets that can have a category but have none yet. **Remove from Categories** on an asset's right-click menu takes it out of its category; the asset stays in the library. Deleting takes its subcategories along; their assets move up to the parent category, or to Uncategorised for a top-level one. Showing a category shows its subcategories' assets too.
- **Thumbnail View** on a category chooses which picture its assets show (for example the front view for trees).
- **Thumbnail Lighting** on a category chooses the lighting its assets' new pictures are rendered in (for example Studio for furniture, Daylight for plants). Subcategories without their own use their parent's; a category without one uses **Library Settings > Thumbnails > Lighting**. Pictures you have stay until you re-render them.

### Collections and Favorites

Collections are your own groups of assets, across all projects.

- **+** next to **Collections** makes one. Drag assets onto it, or use **Add to Collection** (right-click, the selection bar, or the chips in the preview).
- **Favorites** is built in: **Add to Favorites** on the right-click menu. Favorite assets show a star.
- Right-click a collection to rename or delete it. The assets are not affected.

### Your tags

In the preview, **+ Tag** adds your own tags (several at once: separate them with commas). With several assets selected, a tag goes on all of them; `(2/5)` beside a tag means 2 of the 5 have it.

- Click a tag to filter the grid by it; click again to stop.
- Right-click a tag: **Remove** takes it off the selected assets; **Rename Tag...** and **Delete Tag** change it on every asset.
- Tags with ✦ come from AI tagging, tags with a colour dot are colours Blisk found. Removing an AI tag keeps it away when you tag again.

Your tags and each asset's category are saved beside its library project, in the project's `Blisk` folder, so they travel with the project. The list of categories and your collections are kept on this computer, in `Documents\Blisk`.

### Hide, reset and delete

At the bottom of a tile's right-click menu. Each asks first and says what goes.

- **Hide from Library** leaves assets out of every place, category, collection and search, for example test meshes and clutter. Their files are not touched. The eye button left of **Sort** shows hidden assets too, faded; **Show in Library** brings them back. Hidden is saved with the project's tags, so on a shared drive the assets are hidden on every PC.
- **Reset Blisk Data...** removes what Blisk keeps about the assets: tags, colours, category, AI tags and description, picture choices, custom thumbnail, Blisk's rendered pictures, a thumbnail look of their own and the hidden mark. The assets and their library project are not changed, and they stay in your collections. This cannot be undone.
- **Delete...** is only offered for this project's assets. It opens Unreal's own delete window, which first shows what uses them (with Replace References and Force Delete), exactly as in the Content Browser. Blisk then also forgets their tags, pictures and collections. Assets of your other library projects are never deleted: Blisk never changes your library projects.
- The **Delete** key in the grid opens the same question (for Poly Haven assets: Remove Download, all qualities). It never deletes anything at once.

## The preview

Select an asset to see:

- **Its picture**, at true size beside a 1.75 m person or a ruler. For meshes, Blueprints and foliage, pick the view (**Front**, **Side**, **Top**, **Angled**, or **Custom** if you set your own picture) and the size reference (**Auto**, **Person**, **Ruler**, **None**; in **Top** there is no Person). Your choice is also used for the asset's tile. For materials, pick the shape: **Ball**, **Cloth**, **Box (1 m)**, **Plane (1 m)** or **Standing Panel**.
- **Files it uses**: whether everything the asset needs is in the library. If not, it says what is missing and where it would come from (a plugin that is not installed, another asset pack, a newer engine).
- **Size**, **Type**, **Saved with** (engine version), **Category**.
- **More details**: the project and path, triangles, Nanite, LODs, material slots, texture resolution and all asset registry tags; **Set Custom Thumbnail...**, **Re-render**, **Reset Thumbnail**, **Clear AI Tags** and **Show in Explorer**.
- **Tags** and **Collections**.
- **Import to Project**.

Select several assets (Ctrl- or Shift-click) to tag them, put them in a category or collection, or import them together. The bar under the grid shows how many are selected.

## Using assets

- **Drag into the level**: Blisk copies the asset and everything it uses into your project, then places it where you drop it (one undo step). Large meshes that still have to be built for your project appear when they are ready; you can keep working.
- **Import to Project** (the preview's button, the right-click menu, or **Enter**): copies without placing, and selects the assets in the Content Browser.
- **Double-click** an asset of **This Project** to open it, as in the Content Browser: a mesh in its editor, a material in the Material Editor, a level loads. On assets of your other projects a double-click does nothing (on Poly Haven tiles it imports).
- **Import a whole folder**: right-click a folder or pack in the folder list > **Import Folder to Project...**. A summary shows first how many assets and files are copied, their size and where they go, what is already in your project (never changed), and what is missing or left out; **Include subfolders** appears when the folder also has assets of its own. **Import preset** picks the settings for the meshes: **Each category's preset** (the line under it says which meshes get which), **Source Project Settings** or one of your presets. Nothing is copied until you click **Import**. Every asset type in the folder comes in, whatever the type filter shows. A level comes with its actors, also a World Partition level whose actors are saved in files of their own. **Cancel** while copying leaves nothing behind.
- **Add to Blisk Layer**: only with Blisk Scatter installed.
- **Show in Content Browser** (right-click an asset that is already in this project): selects it in the Content Browser.

### What is copied

- The asset and every file it uses from its project's Content folder, at the same `/Game` path, so materials and textures stay linked.
- Files your project already has are never overwritten. If a file at the same path differs from the library's, yours is kept and the Output Log lists it.
- Engine and plugin content is not copied, only checked.
- Imported assets get the library's picture as their Content Browser thumbnail. Right-click them in the Content Browser > **Use Unreal's Thumbnail** to go back.

### When something cannot come along

Before copying, Blisk tells you when an asset uses files or code that this project does not have, grouped by where they would come from:

- a plugin that is not installed, or installed but not enabled in this project, for example a vehicle Blueprint that needs **Chaos Vehicles**;
- engine content this engine version does not have;
- files missing from the library folder (deleted, or in another asset pack: add that folder too);
- code of the asset's own project (its C++), which cannot be copied: what uses it does not load here.

For a plugin that is installed but off, **Turn On and Import** turns it on for this project and imports; restart Unreal (**Restart Now** on the notice) and what needs it works. **Import Anyway** brings the rest; what uses the missing files (often materials) looks wrong until they are there. (Import Folder to Project lists the same; there, turn a plugin on in **Edit > Plugins**.)

Assets saved with a newer Unreal Engine cannot be used in an older one. Their tiles are faded, and Blisk says so instead of importing them.

## Poly Haven

[Poly Haven](https://polyhaven.com)'s free meshes, materials and HDRIs are listed under **Poly Haven**, above your projects, in Poly Haven's own categories (Wood › Boards & Planks, ...). They are CC0: free for any use, also commercial, with no credit needed. Blisk lists them through Poly Haven's public API; Blisk is not made or endorsed by Poly Haven.

- Blisk fetches Poly Haven's list when you open one of these places, at most twice a day; **Check for New Assets** on the place's right-click menu fetches it now. Without the internet, the list and the pictures you saw before still show.
- The asset search, the folder search and **Sort** (Name, Newest, Popular) work as in your own places. There are no type chips, and one tile is selected at a time.
- The preview shows Poly Haven's picture, with a switch above it: **Ball** / **Plane** for materials, **Angled** / **Front** / **Side** / **Top** for meshes, **Picture** / **Panorama** for HDRIs. Below: the real size, who made it, when it was published, its tags (a click searches for one) and **View on polyhaven.com**.
- To leave Poly Haven out of one project, untick **Library Settings > Poly Haven > Show Poly Haven in this project**: that project's Library then has no Poly Haven places and asks polyhaven.com for nothing. Your other projects keep their own choice.

### Using them

- **Drag a tile into the level**, or a material onto a mesh to put it on that mesh: Blisk downloads it (a progress window with **Cancel**), imports it and places it, in one undo step. A set of variants (grass tufts, stones, candleholders) is placed as Poly Haven laid it out, all selected. Dropped back on the Library (or **Esc**), the drag stops its download.
- **Import to Project** (the preview's button, the right-click menu, **Enter** or a double-click) downloads and imports in the background, with a notification and **Stop**. What arrived is kept: **Try Again** goes on from there.
- With Blisk Scatter installed, drag a mesh tile into Scatter's Layers panel: it is downloaded, imported and added as a layer.
- Imported assets go into `/Game/Blisk/PolyHaven/Materials`, `Meshes` or `HDRIs`, in a folder per asset with a folder per quality (`2K`). A mesh is one static mesh for all qualities (a set: one per variant, each with its pivot at its base); each quality brings its own materials and textures. Imported assets show Poly Haven's picture as their thumbnail (a set's meshes excepted), with **Custom** lit in the preview's Shape or view row.
- HDRIs are imported as cube textures: use one as a Sky Light's cubemap (**Source Type: Specified Cubemap**). Dropping one into the level imports it and shows it in the Content Browser.

### Quality and height maps

- **QUALITY** in the preview: 1K to 8K for materials and meshes, 1K to 16K for HDRIs, with the download size. The default is 2K (HDRIs 4K), set in **Library Settings > Poly Haven**. A 16K HDRI takes minutes and about 10 GB of memory to build; 8K is enough for most renders.
- Another quality is imported beside the first, in its own folder; the qualities in this project have a tick. On a mesh, click a ticked quality to show it on every copy in the project (**Ctrl+Z** switches back).
- **Height map**: the material also gets Poly Haven's height map, for real relief on Nanite meshes (Nanite displacement; **Displacement Depth** on the material sets how deep). How deep depends on the material's real size: 2.5% of its width, so 5 cm for the usual 2 m material and up to 10 cm for bigger ones. **Library Settings > Poly Haven > More settings > Relief depth** sets it for new imports (**By size**, 2, 5 or 10 cm); materials you have keep theirs. A height map makes the download about twice as big. On a material already in the project, the switch turns its relief on or off at once (the height map is downloaded only the first time). **Library Settings > Poly Haven > More settings > Height maps for displacement** makes it the default.

### Downloads

- Downloads are kept in one folder for all your projects, so using an asset again, also in another project, downloads nothing.
- The badge at a tile's bottom left is grey while the quality a drag would use is not downloaded, green once it is. A box beside it means the asset is in this project.
- Click a grey badge to download without importing. **Download at** on the tile's right-click menu downloads another quality; downloaded ones have a tick.
- The button left of **Sort** (a download mark with a funnel) shows only what is downloaded.
- **Library Settings > Poly Haven > More settings > Download folder**: **Change...** picks another folder, for example on a NAS that several PCs share. Blisk then asks whether to **Move Them** (from a network folder: **Copy Them**, since other PCs may use it), **Leave Them** or **Remove Them**. A move runs in the background with **Stop**; imports wait until it is done. **Use This PC's Folder** goes back to the folder on this computer. When the chosen folder does not answer (a NAS that is off), imports use this PC's folder and say so.
- **Remove** deletes Blisk's Poly Haven downloads from the folder (only those). Assets you imported stay in your projects, and can be downloaded again.
- **Remove Download** on a tile's right-click menu frees the space of the selected assets only: one quality (drop 8K, keep 2K) or **All Qualities**. Assets being downloaded or imported are left; on a network folder, other PCs lose those downloads too.

### Blisk's materials

- Materials and the surfaces of meshes are made from Blisk's surface material `M_BliskSurface`. Plants get `M_BliskFoliage`: leaves cut out and lit through, a little colour variation per plant and in patches across the world, and wind (trees sway less, potted plants stand still). Glass gets `M_BliskGlass` (Unreal's Thin Translucent); meshes with glass have Nanite off, since Nanite does not draw translucency yet. Glowing glass, such as a bulb, stays on the surface material.
- They are in `/Game/Blisk/Common/Materials`, built from Blisk's material functions (`Functions`), which you can use in your own materials too: right-click in a material graph, they are listed under **Blisk**. Blisk brings these materials up to date when it updates, so changes made in them are lost: make a copy instead (see below).
- Poly Haven materials are laid from the world at their real size (**World Aligned**, with **World Size X** and **World Size Y** in cm): a 2 m material repeats every 2 m on any mesh, whatever its UVs, the same on walls and floors. Untick **World Aligned** on the material instance to use the mesh's own UVs with **Tiling** instead. **Brightness**, **Contrast**, **Saturation** and **Hue Shift** adjust its colour.
- **Cell Blending** (on the material instance, off by default) lays the texture in random cells that blend into each other at their edges, so its repeats do not show across a lawn, a gravel path or a road. **Cell Size** and **Cell Edge Blend** are in texture repeats; **Cell Random Turn** (1 = any way, 0 = not turned, for asphalt or anything with a direction) and **Cell Random Shift** vary each cell. It works with World Aligned and on the mesh's UVs, relief included, and costs a little more to render. Poly Haven ground textures arrive with it on (asphalt and rock faces shifted only).
- `MPC_BliskFoliage` in the same folder holds the project's **Wind Strength**, **Wind Direction** and **Colour Variation**. With Blisk Scatter installed, a level's Blisk Wind actor steers the wind.

### Your own master material

In **Library Settings > Poly Haven > More settings > Material**, click **My Own** and pick a master material, or click **Make My Own Copy** to start from a copy of Blisk's (saved where you choose; it opens in the Material Editor). New Poly Haven materials and the surfaces of new meshes are then made from it. Plants and glass keep Blisk's foliage and glass materials, and materials imported before keep theirs.

- Blisk fills in the parameters by name: the texture parameters **Base**, **Normal**, **ORM** (occlusion, roughness and metal in red, green and blue), **Displacement**, **Opacity** and **Emissive**, their switches (**Use Normal**, **Use ORM**, ...) and settings such as **Tiling**. Your master needs only those it uses; only the textures it takes are made (all of Poly Haven's maps are downloaded all the same, so another project using Blisk's material needs no download). The line under the picker shows which it has: `Base ✓ · Normal ✓ · ORM – · ...`.
- To make a material imported with one master again with the other, delete its quality folder (`Materials/<name>/2K`) and import it again: nothing is downloaded again.
- A copy keeps calling Blisk's material functions (tiling, relief and the like), and Blisk never changes it.
- The choice is saved with the project (`Blisk/PolyHaven.json`), so a team that shares the project shares it. Renaming or moving the master is followed. If it is deleted, imports use Blisk's material again and say why.

## Thumbnails

Blisk renders its own pictures in the background, with a hidden second copy of Unreal (the **helper**), without opening your other projects.

- **Front** and **Side** are straight, true-to-scale pictures with a person or a ruler beside the asset (assets lower than 50 cm and narrower than 2 m get the ruler). **Top** looks straight down, for things you judge by their footprint, such as ground debris or a rug: a ruler lies under the asset, its 0 under the left edge, so the width reads at once, and the preview's corner shows the footprint (width × depth). **Angled** is a perspective view, without a size reference.
- Nothing is rendered by itself when you browse. Pictures are made when you click **Re-render**, pick a view or material shape that has no picture yet, accept the offer after adding a folder, or let AI tagging render missing views first. **Re-render** makes the view each tile shows first; the assets' other views follow after.
- A notification shows the progress, with **Stop**. Finished pictures are kept; running it again continues with the rest.
- **Set Custom Thumbnail...** uses your own PNG or JPG (or drop an image file onto a tile). **Reset Thumbnail** goes back to Blisk's picture. A picture that is not square keeps its shape on the tile.
- **Lighting**: **Daylight** (sun and sky), **Studio** or **Interior** (a bright room with windows). An asset's new pictures use its own look if you gave it one (see Thumbnail Look), else its category's **Thumbnail Lighting**, else **Library Settings > Thumbnails > Lighting**.
- Changes to the lighting or floor apply to new pictures. To update one: right-click the asset > **Thumbnail > Re-render Thumbnail**.
- **Glass** and other see-through parts show at their own opacity, a little stronger, so a clear glass desk top still reads on the tile. To show glass more or less in pictures rendered from now on, type `Blisk.GlassPower 0.35` in Unreal's console (the **Cmd** box at the bottom of the editor): lower shows glass more, `1` shows it as the material is, `0` goes back to Blisk's own (0.5). It lasts until Unreal closes; to keep it, add `Blisk.GlassPower=0.35` under `[ConsoleVariables]` in your project's `Config/DefaultEngine.ini`. Re-render to update the pictures you have.

If your graphics card has no memory left for the helper, Blisk says so and tries again every minute. Closing other programs that use the graphics card helps.

### Thumbnail Look

**Library Settings > Thumbnails > Edit...** opens Thumbnail Look: tune how each lighting mode renders, tried on assets of your own.

- Drag up to three assets of **This Project** from the Library onto the numbered slots, or select them in the Library and click **Add Library Selection** (assets of your other projects: import them first). Each slot shows the **Current thumbnail**, the asset **With these settings**, and its **Custom thumbnail** if it has one. Each slot has its own view (**Front**, **Side**, **Top**, **Angled**) or, for a material, its shape. **×** empties a slot.
- **MODE** picks the mode you tune. **Name** renames it: the new name shows here and in Library Settings; an empty name gives Blisk's name back.
- The settings: **SUN / KEY LIGHT**, **FILL**, **RIM**, **SKY**, **CAMERA** (automatic exposure, exposure, contrast, saturation), **LOCAL EXPOSURE**, **BOUNCED LIGHT**, **ANGLED VIEW** and **FLOOR** (colour, brightness, and whether it bounces light onto the asset). Every change renders the slots again, within a second or so. A small arrow beside a changed setting puts it back to its saved value.
- **BOUNCED LIGHT**: **Project** (as your project renders), **None**, **Lumen** (needs **Generate Mesh Distance Fields** in the project) or **PT** (path traced: the most natural light, slower; needs **Support Hardware Ray Tracing** in the project). A choice the project cannot do is greyed out. PT is for meshes only: the path tracer leaves out Nanite displacement, so materials (on their shapes) render with Lumen instead (the **?** beside BOUNCED LIGHT says so).
- **SKY > Picture** lists the mode's own sky, Unreal's skies and your own, each with a small picture of it. The **×** beside one of your own removes it (only Blisk's copy; the file you added it from stays). **Add from HDR or EXR File...** takes an HDRI panorama (twice as wide as high); **Add from Cubemap in This Project** takes a cube texture. Blisk keeps a copy at most 2048 pixels wide, so pictures stay quick to render, in `Documents\Blisk\ThumbnailSkies`, for all your projects (**Show My Sky Pictures** opens the folder).
- **Save *Mode* Settings**: new pictures in that mode, and pictures you re-render, use these settings. Pictures you have stay as they are. The mop icon (**Reset to Default**) sets every value back to Blisk's own; save to keep that.
- **Use for This Asset** keeps the settings for that one asset only, in that mode. **Reset Blisk Data** on the asset removes them.
- Changes you did not save are gone when the window closes.

## Faster loading

Unreal builds a mesh, its textures and materials the first time a project uses them, which can take minutes for a large tree. Blisk **keeps that work**: once you have imported an asset, it loads at once in your other projects with the same Unreal version and build settings (ray tracing and the like), also weeks later.

- It is experimental and off by default: switch on **Library Settings > Speed and storage > Keep what Unreal builds (Experimental)**. After an import, once Unreal has built it and you have not imported anything for a minute, the helper keeps the result in the background.
- Kept builds go to a folder on this computer (`%LOCALAPPDATA%\Blisk\Builds`; **Choose...** picks another, **Use This PC's Folder** goes back). Unreal reads it while it starts, so a folder on this computer is best. About 20 MB per prop and 60 MB per tree; **Remove Kept Builds** frees the space, and assets then build again the first time each project uses them.
- **Use kept builds in my projects (Experimental)** (off by default) adds a few marked lines to each project's personal `Config/UserEngine.ini` once there is something to read, and removes them when you switch it off. It takes effect at the next start of Unreal.
- A tile shows a check mark when its build is kept for this project's settings, so dragging it in loads at once. A dimmed check mark: the build is kept with another import preset (from an Import With); its tooltip names the preset, and Import With marks it "(loads at once)". The first import of each asset still builds it once, and a new Unreal version builds everything once again: Unreal cannot use builds from another version.

## Import presets

An import preset sets the Nanite settings of the meshes an import copies into your project: for example, trees with Nanite on, full detail for ray tracing and the path tracer, and leaves that do not thin out in the distance. The library's own files are never changed.

1. **Library Settings > Import presets > + Add Preset**. Each preset is a card with its name and what it sets in one line; click it to open its settings. Its rows have the same groups and names as a static mesh's Details panel, so you can compare them side by side; **As Is** keeps what the mesh has in its library project.
   - **Nanite Settings**: **Enable Nanite Support** (On, Off), **Shape Preservation** (None, Preserve Area, Voxelize). Under **More settings**, **Fallback Target** (Auto, or Relative Error with its value; 0 keeps every triangle): the plain mesh drawn where Nanite is not available and used for collision.
   - **Ray Tracing**: **Ray Tracing Proxy** (Auto, or Relative Error with its value) is what ray tracing, hardware Lumen and the path tracer draw of the mesh. Relative Error 0 keeps every triangle (the sharpest leaves and shadows in path-traced renders, the most memory); Auto is Unreal's lighter default. Blisk ticks each copied mesh's own Enable Ray Tracing Proxy Support, so it is the same in every project. Under **More settings**, **Foliage OverOcclusion Bias**: less too-dark light under trees in Lumen (the path tracer ignores it).
   - **LOD Settings**: **LOD Group** sets the group as the Details panel does (its number of LODs, their reduction and the lightmap resolution; LODs the copy had are made again from LOD 0). **Number of LODs** keeps only the first ones: 1 keeps LOD 0 only, which suits Nanite meshes (Unreal builds every LOD of a Nanite mesh too, though only views without Nanite draw them).
   - **Collision**: **Collision Complexity** (Project Default, Simple And Complex, Use Simple Collision As Complex, Use Complex Collision As Simple), **Simple Collision** (Remove takes the copy's simple shapes away) and **Collision Presets** (your project's presets, e.g. NoCollision, BlockAll). Simple Collision Remove with Use Simple Collision As Complex leaves no collision at all: a dense tree's collision is slow to build and foliage needs none.
   - **Build Settings**: **Generate Lightmap UVs** (only for baked lighting; slow to make for dense meshes) and **Distance Field Resolution Scale** (lower builds big meshes faster, at a cost to software Lumen's detail; 0 makes none).
2. Right-click a category > **Import Preset** and pick it. Everything in that category is then imported with it, by a drag, **Import to Project** or Blisk Scatter; subcategories without a preset of their own use their parent's. **Source Project Settings** imports the meshes as they are.
3. To use another preset once: right-click assets > **Import With**.

Assets already in your project are not changed by a drag or Import to Project. **Import With** on one asks first, then sets the preset on the copy in your project (it builds again; the library's files stay as they are). To have it as in the library again, delete it and import it again. The builds Blisk keeps follow the preset, so the next import of the same asset with the same preset loads at once.

## AI tagging

AI tagging looks at an asset's pictures, name and folder and adds tags, a short description and a category, so you can find "olive tree" or "concrete bench" without having named the files that way. It is optional.

### Choose a service

In **Library Settings > AI services**:

- **Gemini (Google), free to start**: a free key from Google AI Studio with your Google account. The free tier has a daily limit, enough to start with; on the free tier Google may use what you send to improve its products.
- **fal.ai**: one account for Claude, ChatGPT, Gemini and other models, paid with credit.
- **Claude (Anthropic)** and **ChatGPT (OpenAI)**: an API account with credit (a Claude or ChatGPT subscription does not include it).
- **Local model (Ollama, LM Studio)**: a model running on your own PC. Free, and nothing leaves your PC. See [AI tagging with a local model](AiTagging-LocalModels.md) A loaded model holds a lot of video memory: **In memory** shows it, **Unload** frees it.

Paste your key into **API key** and click **Save** (**Get a key** opens the service's page). **Model** is chosen for you (the newest low-cost one); **Test** sends one small request to check that it works.

You use your own key and pay the service directly. Blisk shows the estimated cost and asks before every run.

### Tag assets

- Select assets and click **✦ AI Tag** in the preview (or in the bar under the grid), or right-click a folder > **AI Tagging** to tag everything in it.
- Assets that already have AI tags from the same preset are skipped. **Redo AI Tags** tags them again; tags you removed stay removed.
- Meshes get better tags with rendered pictures: if some are missing, Blisk offers **Render Pictures, Then Tag**.
- A notification shows the progress, with **Stop**.

The AI's tags show with ✦ and its description in italics, with the model and date. **Clear AI Tags** removes them; your own tags and categories stay.

### What the AI is asked

The arrow next to **✦ AI Tag** picks a **preset**: General, ArchViz, Nature & Vegetation, Fantasy & Stylized, or your own (**Edit Presets...** shows exactly what each one asks). In **Library Settings > AI tagging**:

- **Put assets in categories** and **Only when the model is sure** (otherwise the asset goes to Uncategorised). A category you set by hand is never changed.
- **Tag language**: tags and descriptions in another language. The search finds the English words too.
- **Add common names of species**: when a plant's or animal's Latin name is in the asset name or folder (`Betula_pendula`), Blisk adds its common names (silver birch) from the public GBIF species database, also in a second language if you choose one. Only the Latin name is sent there. With a local model this is off until you switch it on.

## Library Settings

Open them with the gear in the Library tab, **Blisk > Library Settings...** on the toolbar, or **Edit > Editor Preferences > Plugins > Blisk Library**. Changes apply right away. Point at the **?** beside a section or setting to see what it does.

- **Folders**: your projects and folders, **Add Project or Folder...**, **Look for New Assets**, and per row a tick (shown in this project's Library or not), **Look Through Again** and **Remove from List**.
- **Poly Haven**: **Show Poly Haven in this project**, the default quality for **Materials and meshes** and for **HDRIs**. Under **More settings**: the **Download folder**, **Height maps for displacement**, **Relief depth** and the **Material** new imports are made from (see Poly Haven above).
- **Thumbnails**: **Names on tiles** (as in Unreal, or readable: "European Beech 02" for `SM_EuropeanBeech_02`), **Lighting** (Daylight, Studio, Interior, or the names you gave them) with **Edit...** for Thumbnail Look, **Size reference** on tiles (Off, Automatic), **Floor in angled views**, **Padding** (room around the asset in tiles and the preview, in percent of the picture on each side; shown at once, no new render). Under **More settings**: the default view, the default material shape, and **Blisk pictures in the Content Browser** (a picture Blisk renders of an asset in this project also becomes its Content Browser thumbnail).
- **AI tagging** and **AI services**: see above.
- **Import presets**: see above.
- **Speed and storage**: **Keep the helper ready** (pictures and drags start at once, but the helper uses about 5 GB of memory; it closes after 10 idle minutes), **Stop Background Work**, and the kept builds, marked Experimental (see Faster loading).
- **Backup**: **Back Up...** and **Restore...** (see Moving to another computer).

## Network drives and shared libraries

Your library can be on a NAS or a server: a mapped drive (`Z:\Assets`) or a network path (`\\server\assets`).

- **A drive that is off never blocks Unreal.** Its projects show greyed as **not reachable**, with their assets as they were, and come back by themselves when the drive answers. Until then nothing can be imported from them; Blisk says so and copies nothing. If the drive stops answering during an import, **Cancel** in the progress window ends it at once (or Windows gives up after about a minute); nothing is imported and no files are left in your project.
- **Pictures and builds**: the helper cannot work on a network share directly, so it works on copies of the files it needs, kept on this computer. The first picture of an asset is slower while its files copy (a notification shows it); later ones reuse the copies. The copies take at most 20 GB per open Unreal Editor, the oldest go first, and copying stops when less than 10 GB would stay free on the disk. To clear them, close Unreal and delete the folder `%LOCALAPPDATA%\Blisk\Helper`.
- **Tags** are saved in the `Blisk` folder of each library project, on the share. If the share cannot be reached when you change tags, Blisk keeps them and saves them when it answers, unless Unreal closes first.
- **Read-only libraries** (a read-only share, or files under source control): browsing, pictures and importing work. Tag changes are kept only until Unreal closes, and AI tagging does not start, since its results could not be saved.
- **Kept builds on a share**: possible, but Unreal reads them while it starts, so every start waits for that drive when it is off or slow. A folder on this computer is better.
- **Poly Haven downloads on a share**: several computers can share one download folder, so each asset is downloaded once. When the share does not answer, each computer downloads to its own folder meanwhile.

### Two computers, one library

Several computers can use one library on a share. What is in each library project's `Blisk` folder is shared: tags, each asset's category, AI tags and custom thumbnails. Each computer keeps its own rendered pictures, collections, list of categories and settings. Known limits in 1.0:

- Tags another computer saves appear after you restart Unreal.
- If two computers change the tags of the same asset within a second or two, one change can be lost.

### Moving to another computer

A new computer or a reinstalled Windows starts without your Library settings. To take them along:

1. On the old computer: **Library Settings > Backup > Back Up...** saves one zip: your library folders, categories (with their lighting and import presets), collections, import presets, Poly Haven settings, thumbnail looks and skies, and your AI tagging and service settings. Tick **Include rendered thumbnails** to bring the pictures too (their size is shown); without them the Library renders them again, which can take hours for a big library.
2. On the new computer: install Blisk Library, then **Library Settings > Backup > Restore...** and pick the zip. Your settings are replaced when Unreal Editor starts again (**Restart Now**, or the next time you open it). The settings that were there are first saved in `Documents\Blisk\Backups`.
3. Enter your AI keys again in **AI services**: they are encrypted for one Windows user and never go into a backup.
4. A library folder that is at another place now (another drive letter) shows as not found: remove it and add it again. Its tags and custom thumbnails come back, since they are kept in the library project itself.

## Your data

Blisk keeps your settings in `Documents\Blisk`, its pictures and index in `%LOCALAPPDATA%\Blisk`, and your tags in a `Blisk` folder inside each library project. It sends nothing anywhere unless you use AI tagging, and asks Poly Haven only for its lists, pictures and files. Everything it stores and sends, and how to remove it: [Privacy](Privacy.md).

## Troubleshooting

- **A project shows "not reachable"**: its drive does not answer. Connect it (or map the network drive again); the project comes back by itself within a minute.
- **Something did not import, or looks wrong after importing**: select the asset and look at **Files it uses** in the preview. It says which files are missing and where they would come from. Add the folder they came from with **+**, or install and enable the plugin (an installed one: **Turn On and Import** when you import).
- **"Saved with a newer Unreal Engine"**: the asset cannot be used in this engine version. Open its project in the newer engine instead.
- **No pictures appear**: pictures are only made when you ask (see Thumbnails). Select assets and use **Thumbnail > Re-render Thumbnails**. If Blisk says the graphics card has no memory free, close other programs that use it.
- **"Another Unreal Editor is using the library list"**: two editors are open at once; Blisk tries again by itself.
- **"Poly Haven can't be reached"**: the internet is off, or Poly Haven does not answer. **Try Again** once it is back; a download goes on from where it stopped.
- **Poly Haven plants stand still in Path Tracing**: for plants placed as instances (Blisk Scatter, the Foliage tool), switch on `r.RayTracing.Geometry.InstancedStaticMeshes.EvaluateWPO`; for a placed mesh, **Evaluate World Position Offset in Ray Tracing** (its Details, **Ray Tracing**, advanced settings).
- **AI tagging fails**: the message says what to do (a key that was not accepted, no credit left, a model the service does not have) and quotes the service. **Test** in **Library Settings > AI services** checks the key and model in a second.
- **Details for a bug report**: the lines with `LogBliskLibrary` and `LogBliskImport` in the Output Log (**Window > Output Log**), or the log file `Saved/Logs/<YourProject>.log`.

## Bug Reports & Feature Requests

Please use the [Issues](https://github.com/pbrgle1/BliskLibrary-docs/issues) page of this repository (it has templates for bug reports and feature requests), or the Blisk Library page on Fab. For a bug, tell us the Blisk Library and Unreal Engine versions, where your library is (local drive, mapped drive, network path) and the steps that lead to it.
