---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/MARI, setup de l'UI/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[SHADING TEXTURING]]"],"source":["[[2e cours lighting 3D4]]"],"Projets":null,"tags":["note_permanente"],"creation date":202511061117,"aliases":null}}
---

## La note 

DISPLAY PROPERTIES:

By rightClicking anywhere in the 3DSpace, let’s open the ‘Display Properties’:

![](https://loucasrongeart.notion.site/image/attachment%3A793ae910-df1e-4dc8-a23d-fa206c5e1dec%3Aimage.png?table=block&id=280706c2-08f3-808b-b086-f627c4a18f5f&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

Let’s disable the Grid, then you can close the Display Properties !! Eventually, if you want to remove the fillRender when selecting a GEO, you can put ‘FillRender’ to ‘Never’. Then, press ‘OK’.

![](https://loucasrongeart.notion.site/image/attachment%3A08d3606a-47a4-49d3-8de3-c90fc393531c%3Aimage.png?table=block&id=280706c2-08f3-80f1-9380-d4df2a595096&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

![🔲 Icône de l’encadré](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

‘EDIT/PREFERENCES’:

On the top MenuShelf, go to ‘Edit/Preferences’, where you’ll have all software parameters & user preferences:

![](https://loucasrongeart.notion.site/image/attachment%3A204c81a4-3aa0-48b3-ac73-432db33f9874%3Aimage.png?table=block&id=280706c2-08f3-80e9-becf-e1ea8c67e597&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

![◾ Icône de l’encadré](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

#### In the ‘NAVIGATION’ Tab:

Put the ‘ControlType’ to ‘Maya’, in order to navigate in the 3D Space the same way you’re used in Maya;

Check ‘LockToWorldUp’ to ‘True’, in order to have the Camera always locked to WorldUp;

Put the ‘CenterMode’ to ‘Selection’, in order to have your Camera to orbit around the Patch/Face/Selection you’ve made in the 3DSpace… It’s very helpful !!

![](https://loucasrongeart.notion.site/image/attachment%3A95b5f460-c377-4208-8276-07f9456bb78c%3Aimage.png?table=block&id=280706c2-08f3-801e-a8b4-dcec9170d18e&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

![◾ Icône de l’encadré](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

#### In the ‘COLOR’ Tab:

Put the ‘ColorSwatchesAndPickers’ to ‘OCIO’ — This will switch you from the sRGB ICW to the OCIO ICW that will use ACEScg LUTs;

Put the ‘3DLUTSize’ to ‘64 x 64 x 64’ — At the cost of some additional VRAM, this will provide a better color representation of Colors & Values that you’ll be using for Texturing;

![](https://loucasrongeart.notion.site/image/attachment%3A38419377-7841-44f4-8e4a-ca1fe69a7a1a%3Aimage.png?table=block&id=280706c2-08f3-8014-9577-ff1404796dc0&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

![◾ Icône de l’encadré](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

#### In the ‘DATA’ Tab:

Put the ‘Autosave/Frequency’ to ‘15’ or ‘30’ — This will prevent MARI to autosave your Project all the time;

Put the ‘DefaultResolution’ to ‘4096 x 4096’ — This will make your Channels to automatically be created in 4K rather than in 2K;

Put the ‘Importer’ & ‘Exporter’ to ‘BackgroundImporter’ / ‘BackGroundExporter’ — This will import textures in the Background, saving you a little bit of processing time & fixing some known bugs;

Put the ‘Project/MaxMemory’ to at least ‘60GB’ — This will prevent your Projects to be capped in memory size on your disk. You can increase it further for big big big Projects (got some at around 550GB…);

You’ll only be able to change your ‘ProjectLocation’ when all Projects are being closed — But here’s the place if you want to change your ProjectFolderLocation;

![](https://loucasrongeart.notion.site/image/attachment%3A1079a2f3-093e-44f1-bd5f-56515179ec12%3Aimage.png?table=block&id=280706c2-08f3-80d5-b4e6-c92d132e2658&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

![◾ Icône de l’encadré](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

#### In the ‘GPU’ Tab:

Put the ‘Mip-MapGeneration’ to ‘Accurate’ — This is the most important setting, that will avoir some incorrect colors when textures are projected or baked;

The other settings are very optional — But you can copy them as, as they’ve given me the best results when working with various GPUs;

![](https://loucasrongeart.notion.site/image/attachment%3A3504b12b-e65b-449b-9b2b-f74ee4511b82%3Aimage.png?table=block&id=280706c2-08f3-8052-8f19-cd39579d648d&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

![◾ Icône de l’encadré](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

#### In the ‘PAINTING’ Tab:

Put the ‘Pressure/Mode’ to ‘Tablet’ — This will ensure that your penPressure will provide the entire range of pressure to your brush strokes;

Put the ‘DefaultColorDepth’ to ‘32 bit (Float)’ — This will ensure that for any Projection that you do, 32bit maps will correctly be projected;

![](https://loucasrongeart.notion.site/image/attachment%3A302e66e8-ad6f-45f3-bf7e-8c02d4ad297a%3Aimage.png?table=block&id=281706c2-08f3-807f-9a7a-c2863b94f0f5&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

![🔲 Icône de l’encadré](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

PALETTE MENUS & SETTINGS:

On the right of your UI, you’ll have all the ‘PALETTES’. Palettes are all the contextual menus that will help you navigate within your Project. Usually… I close all of them & just open them when I need them (except from the NodeGraph & NodeProperties).

![](https://loucasrongeart.notion.site/image/attachment%3A25432428-d5db-4327-b15e-982b4d8b0a30%3Aimage.png?table=block&id=281706c2-08f3-8010-8d63-edc4f8c26927&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

Click on that small Icon to have Panels to open temporarily & not be persistant in the UI:

![](https://loucasrongeart.notion.site/image/attachment%3A3b2bf29a-6f48-4b19-b00c-a3912bf2e8bd%3Aimage.png?table=block&id=281706c2-08f3-80c2-982f-c42bf8338675&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

Click on the ‘NodeGraph’ & ‘NodeProperties’ Palettes & Dock them to the left of the UI:

![](https://loucasrongeart.notion.site/image/attachment%3Ac3ee67d0-cecf-4c30-ac12-252db546cd6a%3Aimage.png?table=block&id=281706c2-08f3-8097-8188-faae8a8438ef&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=1320&userId=&cache=v2)

![](https://loucasrongeart.notion.site/image/attachment%3A95e8b729-b59c-4cb4-a378-b6eb9de7458d%3Aimage.png?table=block&id=281706c2-08f3-8067-92f1-e7e19a0c4329&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

![◾ Icône de l’encadré](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

#### In the ‘PAINTING’ Palette:

Put the ‘ColorDepth‘ to ‘32 bit (Float)’ — This will ensure that you can project 32bit textures;

Put the ‘BufferSize’ to ‘4096x4096’ — This will ensure that your paintBuffer will project 4K maps on your Patches (can be increased for better projections);

Put the ‘Transform/Scale’ to ‘(1.0; 1.0)’ — This will ensure that your PaintBuffer will be adjusted automatically to your screen resolution;

Put the ‘Projection/BakeBehaviour’ to ‘Manual’ — This will prevent your PaintBuffer to bake texels on your PaintBuffer when you press ‘Alt’;

![](https://loucasrongeart.notion.site/image/attachment%3A7c7c341e-23ca-44bb-90c7-c2e9f383a993%3Aimage.png?table=block&id=281706c2-08f3-805e-8096-f4f8ccf5929f&spaceId=3e628503-d5bd-4fb5-85bd-498b69a31994&width=2000&userId=&cache=v2)

Now we are all set, you can discover more about MARI & start painting !!


## Références


> [!example]- Flashcards
> ...




## Liens 
