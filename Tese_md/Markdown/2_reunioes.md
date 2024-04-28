# Reuniões

## 1-Mar-24

YOLOv9 paper released on 21FEV24

- yolov9 + atrativo
- meter v9 a funcionar na maquina ciafa
- o q é q vamos ganhar em relação ao v8 ?
- perceber se v9 serve os nossos prpopositos ?
- exemplo minimo a correr no ciafa
- adotar escrito para tese

## 8-Mar-24

- 03-Mar-24: eu percebi q estava a ser parvo quando disse "ah e tal o yolov9 n tem segmentação ainda, então talvez seja melhor ficar com o yolov8"
- para fazer o autolabelling nós apenas precisamos das capacidades do YOLO para fazer object detection, e por sua vez as "bounding boxes", portanto dá para usar YOLOv9

## 22-Mar-24

- equilibrio entre quantidade e qualidade de images
- selecionar datasets com o mais parecido com o que temos
- depois do YOLOv9 filtrar a qualidade do q vai para o SAM. basicamente ver se as bounding boxes estão boas para ir para o SAM e excluir o que tá errado
- ver ferramenta de anotação do roboflow para segmentação (Human annotator)
- unified dataset:
- prioridade UAV/aereo,
- identificar um test set de apenas imagens aereas anotadas e q não estejam no treino
- identificar outro test set com imagens genericas/ground anotadas sem estar no train set
- meter tb falso negativo
- treino pode ter coisas que não são aereo florestal
- ~1000 test set (aéreas) (linha 7)
- ~1000 test set + x (linha 8)
- datasets com frames fazer uma amostragem
- weights and biases

## 26-Apr-24 

- ver anchors do yolov9 (?)
- ver configuaração que possa limitar tamanho de bounding box
- passar pipeline na dataset LK 
- ver yolov8/v9 segmentacao
- criar tabela com parametros do treino (tamanho de imagem, batch size, data augmentation, lr, epocas)
- averiguar val a 0
- guardar configuração do treino

## Meeting with Rashmi

- AWS Sagemaker, and EC2: