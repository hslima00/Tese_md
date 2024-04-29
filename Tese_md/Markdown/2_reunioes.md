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

## Meeting with Rashmi 27-Apr-24

!!!question "Do you upload your code to benchmarks?"
    Yes, the code is uploaded to benchmarks, at least we do in MIT. We make our code open source to help other researches and to make our work reproducible.

!!!info
    In [papers with code](https://paperswithcode.com/) there are multiple researches that upload their code and datasets. MIT and University of S. Francisco does this, but not every company or university does, such as CorsicanFire.

!!!question "How do you upload? For example, in a benchmark suite like CityScapes it is expected of the researcher to download a training set, develop a model, upload the model/code and then the model is evaluated by the benchmark suite on the backend. In my third challenge I want to give the option to researchers to distribute their code through different hardware, do you know any frameworks where this is possible?"
    (maybe I didn't make myself very clear here because the answer was not very targeted to the hardware distribution)
    We usually use [Amazon SageMaker](https://aws.amazon.com/sagemaker/) [^1] and [Amazon S3](https://aws.amazon.com/s3/) [^2] bucket ecosystem. We upload our dataset do S3 bucket and our code to SageMaker. SageMaker is what runs the code files. This is ==not a free== service 
    
    [^1]: Build, train, and deploy machine learning (ML) models for any use case with fully managed infrastructure, tools, and workflows
    [^2]: Scalable, secure, and versatile object storage solution for diverse data needs.

!!!question "Are you familiar with ONNX?"
    Yes ONNX is heavily used. ONNX is also like a framework/platform is which you can have a checkpoint of a format of your model and then you can convert it to any other framework. For example, you can convert a PyTorch model to a TensorFlow model. ONNX is a very good platform for model conversion. This is called platform agnostic, so you can convert a model from one framework to another.

    For edge devices there is also TensorFlow Lite, which is a framework that is used to convert models to be used in edge devices. ONNX is more for cloud computing.

    - [ ] Look into ONNX
    - [ ] Look into TensorFlow Lite

!!!question "Can you elaborate on Amazon Sagemaker? How does it work?"
    Basically Sagemaker is like when you use Google Colab GPU's. They offer very good GPU's and you can run your code on their GPU's. And S3 is like Google Drive, where you can store your data.

!!!question "You are explaining how your environment, as a developer/researcher, is right? Regarding to this, I was thinking to create a docker image that has pre-installed all the necessary libraries and frameworks to run the code and to make it compatible with the serverside hardware. Do you think this is a good idea?"
    Yes docker is actually a good idea. Docker, Kubernetes and all these kind of platform in which you are adding whichever requirements are needed like the Python version, the libraries etc.

!!!question "Lets imagine that, you as a researcher, want to benchmark a model for fire and smoke segmentation and you come acros with my benchmark online. How would you like/be easier for you to interact with it?" 
    !!!danger "==Questão para os orientadores== Is it even worth it to continue with the benchmark suite if there is already a popular and trusted platform named Kaggle?"
        
    You need the model from the researchers and you will give them a dataset. This is similar to Kaggle competitions. 
