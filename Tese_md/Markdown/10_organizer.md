# Organizer

## What does it do?

It helps moving the files to the right place: 


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
    \HL_FIREFRONT_UNIFIED_DATASET
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