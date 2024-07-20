# TwiProj

## :mega: Publish Your Twibbon
1. Create a folder for your twibbon in the root repository.
2. Upload all the files that become your twibbon layers.
3. Create a [`metadata.json` file](#page_facing_up-metadatajson-template).
4. Twibbon is ready to use.

## :file_folder: Folders and Files
### Nomenclature and Composition Mechanisms
- Use alphanumeric characters, without spaces and any symbols.
- For twibbon image files, the name must follow the format `layer{index}` followed by commonly used image file types, such as `.png`, `.jpg`, `.jpeg`. For example, `layer1.png`.
- Replace `{index}` with a number indicating the composition order of the image. [See below for an example](#structure).
- Index starts from 1.
- Photo uploaded by users will be placed on the last layer, or on the layer where the index is passed ([see below for an example](#tanabata_tree-twibbon-layer-compositing)).

### Structure
- Let's say, I want to upload my twibbon named `mytwibbon` with 4 twibbon layers. Later, the user's photo will be placed on layer 4. So, the file and folder structure will be like this. ([See the layer composition](#tanabata_tree-twibbon-layer-compositing))
``` bash
root
├── mytwibbon
│   ├── layer1.png
│   ├── layer2.png
│   ├── layer3.png
│   ├── layer5.png
│   └── metadata.json
│   
└── {other_twibbon}
```

## :tanabata_tree: Twibbon Layer Compositing
``` bash
canvas
├── layer1.png
├── layer2.png
├── layer3.png
│   {user_photo}
└── layer5.png
```

## :page_facing_up: `metadata.json` Template
``` js
{
    "title": "YOUR_TITLE",
    "subtitle": "YOUR_SUBTITLE",   // null is allowed
    "width": 1080,    // TWIBBON_WIDTH (in px)
    "height": 1080    // TWIBBON_HEIGHT (in px)
}
```

## :warning: Warning
It is not recommended to use more than 3 composition layers (including user photo), as it may affect the drawing performance performed by the system.

Therefore, it is best to only use a maximum of 3 layers of composition:
- 1 front layer (e.g. `layer1.png`)
- 1 user photo layer
- 1 back layer (e.g. `layer3.png`)
