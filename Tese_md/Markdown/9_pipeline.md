---
hide:
- navigation
---

# Pipeline


```py title="Output normalizado xywh"
0   0.371875  0.34921875   0.48125     0.68984375 
0   0.671875  0.45078125   0.16171875  0.58203125 
0   0.903125  0.3703125    0.1765625   0.4296875
```

Primeiro digito é a `classe` e os restantes são as coordenadas `x,y,w,h` normalizadas.

## Input do SAM como bounding box

=== "Apenas uma bounding box"

    ```python title="Bounding box xyxy"
    input_box = np.array([425, 600, 700, 875])
    input_point = np.array([[575, 750]])
    input_label = np.array([0])
    ```
=== "Mais do que uma bounding box"

    #TODO

    
As coordenadas que o SAM recebe são do formato `xyxy` ==não== normalizadas. Logo o seguinte código foi escrito para fazer a conversão das cordenadas do YOLOv9:

```python title="Conversão de coordenadas"
def normalize_to_denormalize(x, y, w, h, image_width, image_height):
    # Convert normalized coordinates to denormalized coordinates
    x1 = int(x * image_width)
    y1 = int(y * image_height)
    x2 = int((x + w) * image_width)
    y2 = int((y + h) * image_height)
    
    return x1, y1, x2, y2

# Example usage:
normalized_coords = (0.371875,  0.34921875,   0.48125,     0.68984375)  # Example normalized coordinates (x, y, w, h)
image_width = 800  # Example image width
image_height = 600  # Example image height

x1, y1, x2, y2 = normalize_to_denormalize(*normalized_coords, image_width, image_height)
print("Denormalized coordinates:", (x1, y1, x2, y2))

# output: Denormalized coordinates: (297, 209, 682, 623)
```

Para termos o tamanho da imagem fazemos:

=== "Code"
    ```python title="Tamanho da imagem"
    image = cv2.imread('images/truck.jpg')
    image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB) 
    h, w, c = image.shape
    print('width:  ', w)
    print('height: ', h)
    print('channel:', c)
    ```
=== "Output"

    <figure markdown="span">
            ![picture 0](https://cdn.statically.io/gh/hslima00/tese_md_images/main/6_pipeline_17-04-2024_18-20-17.png)  
        
    <figcaption>Output do código</figcaption>
    </figure>


## Imagem RBG -> Mascara preto e branc

Tem que se adaptar a função:

```python title="Conversão para mascara preto e branco"
def get_whiteBlack_masks_image(self):
        masks = self.masks
        darkImg = np.zeros_like(self.origin_image)
        image = darkImg.copy()

        np.random.seed(0)
        if (len(masks) == 0):
            self.whiteMasks = image
            return image
        for mask in masks:
            if mask['opt'] == "negative":
                image = self.clearMaskWithOriginImg(darkImg, image, mask['mask'])
            else:
                image = self.overlay_mask(image, mask['mask'], 0.5, random_color=False)

        self.whiteMasks = image
        return image
```

[Source](https://github.com/Nomination-NRB/SAM-webui/blob/main/app.py), linha 593.

## Duvidas para a reunião

- ==D:== Encontrei isto (G-DINO + SAM), devo continuar com a pipeline ou experimento isto? Paper 25JAN2024 Grounded SAM
    - ==R:== Continuar com o que temos, e depois ver se podemos usar outra coisa
- ==D:== Onde arranjar mais imagens para fazer a dataset? (Uma vez que têm que ser privadas)
    - ==R:== Provavelmente FAP tem mais imagens, mas têm que ser pedidas e provavelmente não serão muitas

## 18-Apr-24 

- [x] Ler output do YOLOv9
- [x] Normalizar coordenadas de `xywh` para `xyxy`
- [x] Meter tudo numa estrutura de dados do tipo:

```python title="Estrutura de dados"
data = {
    'img_path': 'path/to/image.png',
    'file_name': 'image.png',
    'bounding_box_data': [
        {
            'class_id': 0,
            'bbox_data': [x1, y1, x2, y2]
        },
        {
            'class_id': 1,
            'bbox_data': [x1, y1, x2, y2]
        },
        ...
    ]
}
```

- [x] Resolvido o problema de, quando o YOLOv8 não deteta nada, não cria a label.txt, então se o a imagem existir, vai criar um .txt vazio com o nome da imagem 
- [x] Transformar em máscara preto e branco 


???note "Inferência feita pela pipeline"

    <figure markdown="span">
            ![img_1675](https://cdn.statically.io/gh/hslima00/tese_md_images/main/9_pipeline_18-04-2024_02-24-36.png) 
    <figcaption>img_1675</figcaption>
    </figure> 

    Transformação em mascara preto e branco

    <figure markdown="span">
        ![img_1675_BW_mask](https://cdn.statically.io/gh/hslima00/tese_md_images/main/9_pipeline_18-04-2024_02-56-54.png) 
      <figcaption>Black and white mask</figcaption>
    </figure> 
