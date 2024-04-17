---
glightbox.auto_caption: true
---

# CIAFA

Aqui meto cenas relativas ao hardware que está na CIAFA, por exemplo que libs é que foram instaladas etc.


## YOLOv9

04-Mar-24

### Activating venv and installed libs

=== "Bash"

    ```bash
    source .venv/bin/activate
    ```

=== "Installed in the venv"

    I installed everything inside the `requirements.txt` given in the YOLOv9 repo using the command:

    ```bash title="requirements.txt"
    pip install -r requirements.txt
    ```

    The content of the `requirements.txt` file is:

    ```py
    # requirements
    # Usage: pip install -r requirements.txt

    # Base ------------------------------------------------------------------------
    gitpython
    ipython
    matplotlib>=3.2.2
    numpy>=1.18.5
    opencv-python>=4.1.1
    Pillow>=7.1.2
    psutil
    PyYAML>=5.3.1
    requests>=2.23.0
    scipy>=1.4.1
    thop>=0.1.1
    torch>=1.7.0
    torchvision>=0.8.1
    tqdm>=4.64.0
    # protobuf<=3.20.1

    # Logging ---------------------------------------------------------------------
    tensorboard>=2.4.1
    # clearml>=1.2.0
    # comet

    # Plotting --------------------------------------------------------------------
    pandas>=1.1.4
    seaborn>=0.11.0

    # Export ----------------------------------------------------------------------
    # coremltools>=6.0
    # onnx>=1.9.0
    # onnx-simplifier>=0.4.1
    # nvidia-pyindex
    # nvidia-tensorrt
    # scikit-learn<=1.1.2
    # tensorflow>=2.4.1
    # tensorflowjs>=3.9.0
    # openvino-dev

    # Deploy ----------------------------------------------------------------------
    # tritonclient[all]~=2.24.0

    # Extras ----------------------------------------------------------------------
    # mss
    albumentations>=1.0.3
    pycocotools>=2.0
    ``` 