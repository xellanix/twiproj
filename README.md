# TwiProj

## :mega: Publish Your Twibbon
1. Create a folder for your twibbon in the root repository.
2. Upload all the files that become your twibbon layers.
3. Create a [`metadata.json` file](#page_facing_up-metadatajson-template).
4. Twibbon is ready to use.

## :package: Folders and Files
### Nomenclature and Composition Mechanisms
- Use alphanumeric characters, without spaces and any symbols.
- For twibbon image files, the name must follow the format `layer{index}` followed by commonly used image file types, such as `.png`, `.jpg`, `.jpeg`. For example, `layer1.png`.
- Replace `{index}` with a number indicating the composition order of the image. [See below for an example](#structure).
- Index starts from 1.
- Photo uploaded by users will be placed on the last layer, or on the layer where the index is passed ([see below for an example](#jigsaw-twibbon-layer-compositing)).

### Structure
- Let's say, I want to upload my twibbon named `mytwibbon` with 4 twibbon layers. Later, the user's photo will be placed on layer 4. So, the file and folder structure will be like this. ([See the layer composition](#jigsaw-twibbon-layer-compositing))
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

## :jigsaw: Twibbon Layer Compositing
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
    "subtitle": "YOUR_SUBTITLE",
    "width": 1080,
    "height": 1080,
    "lastLayerIndex": 5,
    "caption": {
        "template": "Hello, my name is <<NAME>> and I am <<AGE>> years old.",
        "params": {
            "NAME": {
                "label": "Name",
                "default": "[YOUR NAME]"
            },
            "AGE": {
                "label": "Age",
                "default": "[YOUR AGE]"
            }
        }
    }
}
```

Explanation:
- `title`: The main title of the twibbon. In this example, the title is `YOUR_TITLE`.
- `subtitle`: A secondary title or description for the twibbon. This field can also be set to `null` if no subtitle is needed. In this example, the subtitle is `YOUR_SUBTITLE`.
- `width`: The width of the twibbon in pixels. Here, it is set to `1080` pixels.
- `height`: The height of the twibbon in pixels. Similar to the width, it is set to `1080` pixels.
- `lastLayerIndex`: Indicates the index of the last layer in the twibbon file. This helps to understand the layer stacking order. In this example, the last layer index is `5`.
- `caption`: Contains the template for the caption text and the parameters that can be replaced within the caption. This field is **optional**, so you can define it or not, based on your needs.
    - `template`: The template for the twibbon caption. It contains placeholders (in the format `<<PLACEHOLDER>>`) that will be replaced with actual values. Here, the template is `Hello, my name is <<NAME>> and I am <<AGE>> years old.`.
    - `params`: Defines the placeholders and their attributes.
        - `PLACEHOLDER`: The placeholder name. Based on the template, the first `PLACEHOLDER` should be `NAME` and the second should be `AGE`
            - `label`: A descriptive label for the placeholder.
            - `default`: The default value to be used if no other value is provided.

## :warning: Warning
It is not recommended to use more than 3 composition layers (including user photo), as it may affect the drawing performance performed by the system.

Therefore, it is best to only use a maximum of 3 layers of composition:
- 1 front layer (e.g. `layer1.png`)
- 1 user photo layer
- 1 back layer (e.g. `layer3.png`)
