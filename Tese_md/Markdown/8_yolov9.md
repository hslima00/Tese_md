# YOLOv9


## Treino numa custom dataset

O YOLOv9 foi treinado com uma dataset que arranjei no Roboflow:  [VOCfinaldataset](https://universe.roboflow.com/catargiuconstantinvocdataset/vocfinaldataset) [acedido a 2024-01-20 12:04am]


### Resultados do Treino 

???note "Plot dos resultados do treino"

    ![Confusion Matrix](https://cdn.statically.io/gh/hslima00/tese_md_images/main/8_yolov9_17-04-2024_18-31-33.png){: width="50%" height="50%"}
    ![F1_Curve](https://cdn.statically.io/gh/hslima00/tese_md_images/main/8_yolov9_17-04-2024_18-31-41.png){: width="50%" height="50%"}
    ![labels_correlogram](https://cdn.statically.io/gh/hslima00/tese_md_images/main/8_yolov9_17-04-2024_18-38-45.png){: width="50%" height="50%"}
    ![Labels](https://cdn.statically.io/gh/hslima00/tese_md_images/main/8_yolov9_17-04-2024_18-39-33.png){: width="50%" height="50%"}
    ![Precision confidence curve](https://cdn.statically.io/gh/hslima00/tese_md_images/main/8_yolov9_17-04-2024_18-39-57.png){: width="50%" height="50%"}
    ![Precision recall curve](https://cdn.statically.io/gh/hslima00/tese_md_images/main/8_yolov9_17-04-2024_18-40-25.png){: width="50%" height="50%"}
    ![recall confidence](https://cdn.statically.io/gh/hslima00/tese_md_images/main/8_yolov9_17-04-2024_18-40-46.png){: width="50%" height="50%"}
    ![results](https://cdn.statically.io/gh/hslima00/tese_md_images/main/8_yolov9_17-04-2024_18-41-00.png)  


## Inferência em custom dataset

```python title="Inferência"
python detect.py --weights ../fire_1_best.pt --conf 0.1 --source ../../FIREFRONT_datasets_release/BA_Fire_Smoke_Multilabel/BA_Fire_Smoke_Multilabel_v1/test --device 0

```

!!!danger "Resultado da Inferencia"

    O resultado da inferência pode ser visto [aqui](https://drive.google.com/drive/folders/140NecfCvbZIN8FH3b5QtZnloyh--1Kpl?usp=drive_link) (==apenas partilhado com orientador e co-orientador==) Note-se que existem muitas inferencias erradas, então o modelo terá que ser re-treinado com mais imagens.

  
## Outputs do YOLOv9

Os outputs quando se faz uma inferência `detect.py` são imagens com as bounding boxes:

???note "Exemplo de imagem de uma inferência de uma images da dataset 'BA_Fire_Smoke_Multilabel':"
    ![picture 8](https://cdn.statically.io/gh/hslima00/tese_md_images/main/8_yolov9_17-04-2024_18-46-13.png)  

Porém nós queremos ter o output como coordenadas para o usar para o SAM. Para este fim foi metido a `true` a seguinte linha:

```python title="In 'detect.py' line 34"
save_txt=True,  # save results to *.txt
```

que guarda resultados do tipo:

```python title="Label"
0 0.371875 0.34921875 0.48125 0.68984375
0 0.671875 0.45078125 0.16171875 0.58203125
0 0.903125 0.3703125 0.1765625 0.4296875
```

O primeiro digito correponde à classe `0 = fire` (podia ser `1 = smoke`, `2 = other`) e os restantes são as coordenadas da bounding box.


## YOLOv9 retrain 02-May-24

```bash title="Retrain"
python train_dual.py --workers 8 --device 0 --batch 16 --data /home/hslima/hdd/yolov9/yolov9/fire_dataset/data.yaml --img 640 --cfg /home/hslima/hdd/yolov9/yolov9/models/detect/yolov9_custom.yaml --weights /home/hslima/hdd/yolov9/yolov9-e.pt --name fire2 --hyp /home/hslima/hdd/yolov9/yolov9/data/hyps/hyp.scratch-high.yaml --min-items 0 --epochs 100 --close-mosaic 15
```
