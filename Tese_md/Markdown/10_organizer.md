# Organizer

## What does it do?

It helps moving images (around 7k) to the right place. See the following folder tree structures as an example of initial and final states:


=== "From this"

    ```bash
    FIREFRONT_DATASETS_RELEASE_COPY
    ├───BA_Fire_Smoke_Multilabel
    │   └───BA_Fire_Smoke_Multilabel_v1
    │       ├───test
    │       ├───train
    │       └───val
    ├───GP_Fire_Segmentation_Webimages
    │   └───GP_Fire_Segmentation_Webimages_v1
    │       └───dataset
    │           ├───fire images
    │           │   ├───images
    │           │   └───masks
    │           └───no fire images
    ├───HH_Gestosa_Fire_Segmentation
    │   └───HH_Gestosa_Fire_Segmentation_v1
    │       ├───images
    │       └───labels
    ├───LK_Fire+Smoke
    │   └───LK_Fire+Smoke_v1
    │       └───Fire-smoke
    ├───LK_Smoke_Only
    │   └───LK_Smoke_Only_v1
    │       └───Smoke
    ├───LK_Smoke_Segmentation
    │   └───LK_Smoke_Segmentation_v1
    │       └───Smoke
    │           ├───images
    │           └───masks
    ├───SF_Bombeiros_Fire
    │   └───SF_Bombeiros_Fire_v1
    │       ├───Fire
    │       └───No_fire
    └───TV_Youtube_Video_Fire
        └───TV_Youtube_Video_Fire_v1
            └───fire_videos
                ├───neg
                └───pos
    ```

=== "To this"

    ```bash
    HL_FIREFRONT_UNIFIED_DATASET
    ├───false_negatives
    ├───fire
    │   ├───forest
    │   │   ├───aerial
    │   │   └───ground
    │   └───urban
    │       ├───aerial
    │       └───ground
    ├───noisy_images
    │   ├───bad_quality
    │   │   ├───fire
    │   │   └───smoke
    │   └───water_mark
    │       ├───fire
    │       └───smoke
    ├───other
    └───smoke
        ├───forest
        │   ├───aerial
        │   └───ground
        └───urban
            ├───aerial
            └───ground
    ```

## How to use it?

1. Create a virtual environment and install the requirements:
    ```bash
    python -m venv venv
    source venv/bin/activate # for linux
    venv\Scripts\activate # for windows
    pip install -r requirements.txt
    ```

2. Change the paths in the `display.py` script
      - [ ] TODO: make it possible to edit a config file and place the desired final tree path
3. Run the script:
    ```bash
    python display.py
    ```
4. According to pre-defined keys, look at the image and decide where is should be moved

<center>
 
| Key | Folder | Key | Folder |
| --- | ------ | --- | ------ |
| 1 | Fire/Forest/Aerial | 3 | Fire/Urban/Aerial |
| 2 | Fire/Forest/Ground | 4 | Fire/Urban/Ground |
| 5 | Noisy Images/Bad Quality/Fire | 6 | Noisy Images/Bad Quality/Smoke |
| 7 | Noisy Images/Water Mark/Fire | 8 | Noisy Images/Water Mark/Smoke |
| 9 | Other | q | Smoke/Forest/Aerial |
| w | Smoke/Forest/Ground | e | Smoke/Urban/Aerial |
| r | Smoke/Urban/Ground | t | False_Negatives |
</center>

<figure markdown="span">
    ![Organizer Running](https://cdn.statically.io/gh/hslima00/tese_md_images/main/10_organizer_06-05-2024_08-06-11.png)
  <figcaption>Organizer Running</figcaption>
</figure>  



