---
hide:
- navigation
- toc
--- 

> Concordo em abosluto com tela preta sobre parte classificada;
feito
> Achei muito interessante a evolução da performance com as anotações. Neste sentido, aqueles números de anotações são automáticas, manuais ou auto+manual? acho que documentar isso mostrava o valor do processo de anotação automático com quality control que introduziste.

O loop do quality control é: 

1. Correr a pipeline YOLO+SAM na dataset inteira; 
2. Retirar $x$ imagens random (usando um script) do resultado; 
3. Corrigir as $x$ anotações; 
4. Juntar às anotações confirmadas (ver tabela abaixo: corrigi 200 anotacoes na ultima fase e adicionei às pré-existentes)
5. Treinar um novo modelo YOLO apenas com as anotações corrigidas 

Para calcular o mIoU: 

1. Do ponto 1 da lista anterior comparo as anotações resultantes da pipeline com pré existentes em duas datasets feitas por alunos à mão pixel a pixel: GP (fogo) e LK (fumo).  

Tinha um erro no codigo que estava a calcular o mIoU, as tabelas atualizadas são:

| ID                | #annotations | mIoU (GP - fire) | mIoU (all - smoke) | mIoU (all - fire) |
| ------------------- | -------------- | ------------------ | -------------------- | ------------------- |
| HL_annotation_v1  | 482          | 0.5138655180533725 | 0.4999154278959135 | 0.5588546292939491 |
| HL_annotation_v2  | 937          | 0.6139816386997876 | 0.6902299747060116 | 0.5672355475783253 |
| HL_annotation_v3  | 1475         | 0.6062920947852118 | 0.6733769970507978 | 0.5644811093217798 |
| HL_annotation_v4  | 1675         | 0.6142947505829379 | 0.6801983832873386 | 0.5538738837693626 |


> Sinceramente, acho que o problema do fumo é de muito difícil resolução e acho que tem pouco valor operacional (isto é só a minha opinião e pode estar errada). Eu limitaria o esforço nesse domínio.
O mIoU do fumo, supreendentemente, está superior ao mIoU do fogo. Digo surpreendentemente porque quando revejo as anotações, dou por mim a corrigir muito mais o fumo do que o fogo. Nota: a dataset do fumo onde calculo o mIoU do fumo tem apenas 96 mascaras enquanto que a dataset do fogo tem 180 mascaras.
> Acho que é muito importante documentares o processo que envolve o onnx, não só para a tese ,mas para a página.
TODO!
> Como é que está a correr o trabalho (preparação do test set e escrita do latex)?
> Já agora, confirma o link para o teu overleaf, sff. Eu estava a ver mas o único projecto (que eu tenho) com o teu nome, não é modificado há um mês, o índice não está atualizado, etc. Talvez eu não esteja a ver o certo.

O link está certo, não faço alterações ao documento há muito tempo. Vou começar a fazer agora.  

Tenho perdido muito tempo na anotação da dataset (quer a confirmar as anotacoes corretas, quer a corrigir anotações). 200 imagens demoram em média umas 4/5h. 

A minha sugestão é dar o braço a torcer na anotação porque penso não conseguir corrigir TODAS as 7k imagens numa semana, e tenho mesmo de avançar para a parte do backend. 

A minha sugestão é: 
- Acabar a anotação apenas para a test set (HH_Gestosa + ESQ_991) porque é a que precisa de estar feita para o backend. 
- Quando estiver a test set feita avançar para o backend

Preciso da opinião urgente do Sr. Major para esta decisão. 
Eu gostaria mesmo de acabar a dataset porque não há datasets "de jeito" para segmentacao de fogo e fumo e acho que era um contributo muito bom para a comunidade cientifica. Porem fazendo as contas: 

nr imagens corrigidas: 1675 (23% da dataset toda)
nr imagens por corrigir: 5325
Média de 200 imagens/4h -> 108h (ininterruptas) até acabar as 5325.
Se dedicar 8h/dia (ininterruptas) apenas para acabar a correção das anotações são cerca de 14 dias, 2 semanas. Vale a pena? 

**Importante**: a proxima reuniao com o professor será às 14h30 da proxima segunda feira 29JUL.    

Gostaria de marcar uma reunião para esta semana, se tiver disponibilidade para tal?

Peço desculpa pela leitura longa