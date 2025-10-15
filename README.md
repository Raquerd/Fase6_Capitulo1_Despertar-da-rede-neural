# Visão Computacional para FarmTech Solutions: Análise Comparativa de Modelos
## GRUPO 18
### Integrantes:
- Lais Kurahashi
- Lucas Martinelli
- Davi DaviFerreira

## Estrutura de pastas
Dentre os arquivos e pastas presentes na raiz do projeto, definem-se:

- **assets:** aqui estão os arquivos relacionados a elementos não-estruturados deste repositório, como imagens.

- **config:** Posicione aqui arquivos de configuração que são usados para definir parâmetros e ajustes do projeto.

- **scripts:** Posicione aqui scripts auxiliares para tarefas específicas do seu projeto. Exemplo: deploy, migrações de banco de dados, backups.

- **README.md:** arquivo que serve como guia e explicação geral sobre o projeto (o mesmo que você está lendo agora).

## Tecnologias Utilizadas
- **Linguagem**: Python 3

### Bibliotecas Principais:

- **ultralytics (Yolov5):** Usada para carregar modelos YOLO pré-treinados, treinar modelos customizados, validar a performance e fazer detecção de objetos em imagens ou vídeos.

- **cv2 (OpenCV):** É a principal biblioteca de visão computacional em Python. Ela serve para manipular imagens e vídeos.

- **os (Operating System):** Uma biblioteca padrão do Python para interagir com o sistema operacional.

- **glob:** Uma biblioteca útil para encontrar arquivos que correspondem a um padrão específico.

- **Matplotlib:** Para visualização de dados e resultados.

- **TensorFlow:** É a base para construir e treinar modelos de deep learning. 

- **Ambiente de Desenvolvimento:** Jupyter Notebook


## 1. Visão Geral do Projeto
Este projeto foi desenvolvido como parte da expansão dos serviços de IA da FarmTech Solutions, indo além do agronegócio para atender novas áreas como saúde animal, segurança e análise de documentos.

O objetivo é apresentar a o cliente o funcionamento prático de um sistema de visão computacional. Para isso, foi criado um sistema de detecção de objetos utilizando o YOLO e comparado com outras abordagens, como um modelo YOLO padrão e uma Rede Neural Convolucional (CNN) treinada do zero.

O cenário escolhido para este estudo de caso foi a detecção e classificação de garrafas e copos.

## 2. Organização do Dataset
Para treinar e avaliar os modelos, foi criado um dataset customizado, organizado da seguinte forma:

**Objetos de Estudo:** Garrafas (Objeto A) e Copos (Objeto B).

**Estrutura dos Dados:** As imagens foram separadas em dois formatos principais, localizados na pasta config/:

- **CNN_Dataset:** Estruturado com pastas train e val, contendo subpastas para cada classe, ideal para frameworks como TensorFlow/Keras.

- **Yolo_Dataset:** Organizado com pastas images e labels, seguindo o padrão exigido pelo YOLO. As anotações foram feitas com a ferramenta Make Sense IA.

**Divisão do Dataset:**

- **Garrafas:** 50 imagens de treinamento, 4 de validação e 6 de teste.

- **Copos:** 50 imagens de treinamento, 4 de validação e 4 de teste.

## 3. Requisitos e Como Começar
Para reproduzir os testes e treinamentos, é obrigatório ter uma cópia da pasta compartilhada do Google Drive, que contém todos os datasets.

Link para o Google Drive: https://drive.google.com/drive/folders/1YI58Ca4qwy4f0QwVactO7FX08dFjGuG3?usp=drive_link

Os notebooks foram desenvolvidos para serem executados no ambiente Google Colab, que se integra diretamente ao Google Drive para acesso aos dados.

## 4. Modelos Implementados e Análise de Resultados
Foram implementadas e avaliadas três abordagens distintas, conforme solicitado na atividade. As imagens com os resultados de todas as predições estão salvas na pasta do repostiório Github em assets/.

**Nota:** Todos os modelos estão prontos para serem executados. Basta seguir os requisitos e executar as células no notebook principal.

### 🤖 Modelo 1: YOLOv5 Custom (Entrega 1)
Este modelo foi treinado do zero utilizando nosso dataset customizado para a detecção de garrafas e copos.

- **Treinamento:** 
    - **Epochs:** Foram realizadas duas simulações, com 30 e 60 épocas, para comparar desempenho e acurácia.

    - **Batch Size:** 16

    - **Imagem:** img 640

- **Modelo Salvo:** O modelo treinado está disponível no Google Drive (yolov5/) e também neste repositório em config/yolov5.

#### Conclusão:

O treinamento de um modelo YOLOv5 específico para o nosso dataset demonstrou ser a abordagem mais promissora para as necessidades da FarmTech Solutions.

- **Desempenho Geral:** O modelo atingiu uma performance excelente, com uma acurácia superior a 97% (mAP@0.50), validando a eficácia da arquitetura para a tarefa.

- **Análise de Épocas:** A simulação com 60 épocas apresentou o melhor equilíbrio entre performance e tempo de treinamento, alcançando uma precisão de 86,5% e mantendo a inferência rápida, característica da arquitetura YOLO.

- **Pontos Fortes:**

    - **Alta Acurácia:** Demonstra especialização e confiabilidade na detecção dos objetos de interesse.

    - **Adaptabilidade:** A arquitetura pode ser facilmente retreinada para outros cenários de detecção, como segurança patrimonial e controle de acesso.

    - **Amplitude:** É um modelo que apresenta bastante opções de configuração, permitindo dessa forma, diversas possibilidades de melhoria na eficiencia do modelo.


- **Pontos de Melhoria:**

    - **Velocidade de execução:** Apesar de ser o modelo com maior confiabilidade, também é o modelo mais demorado para uso devido ao treinamento, que, dependendo das configurações setadas, pode demorar consideravelmente.

    - **Epocas:** Observou-se uma necessidade de aumentar a variedade de ângulos e cenários das imagens no dataset de treinamento para aprimorar ainda mais a robustez do modelo.

- **Recomendação para a FarmTech:** Esta é a solução mais indicada. O modelo customizado oferece a precisão necessária para aplicações comerciais e reforça a capacidade da FarmTech Solutions em entregar soluções de IA eficientes e personalizadas.

### 👁️ Modelo 2: YOLO Padrão (Entrega 2)
Foi utilizado um modelo YOLOv5 pré-treinado (padrão) para avaliar sua performance em nosso dataset sem nenhum treinamento adicional.

A avaliação do modelo YOLO padrão, pré-treinado no dataset COCO, serviu como um excelente ponto de referência (baseline) para o desempenho.

- **Desempenho Geral:** A capacidade de detecção foi mediana. O modelo identificou corretamente os objetos em vários cenários, mas apresentou inconsistências, como confundir garrafas com vasos.

- **Pontos Fortes:**
    - **Implementação Imediata:** O tempo de "treinamento" é zero, permitindo a prototipagem e validação de ideias de forma extremamente rápida.

    - **Amplo Conhecimento:** Reconhece diversas classes de objetos diferentes, o que o torna flexível para tarefas de detecção genéricas.
    
- **Pontos de Melhoria:**

    - **Baixa Especialização:** A falta de treinamento específico resulta em menor precisão e confiabilidade para objetos de interesse do cliente.

- **Recomendação para a FarmTech:** Inadequado para aplicações que exigem alta precisão. Embora seja uma ferramenta útil para prova de conceito, não atende aos padrões de qualidade necessários para um produto final da FarmTech Solutions, onde a confiabilidade é crucial.

### 🧠 Modelo 3: Rede Neural Convolucional (CNN) (Entrega 2)
Uma CNN foi construída e treinada do zero para classificar as imagens entre as duas categorias.

- **Treinamento:** 
    - **Epochs:** 18

    - **Batch Size:** 25

    - **Imagem:** 500 x 500

#### Conclusão:

A construção de uma CNN do zero para a tarefa de classificação ofereceu insights valiosos sobre a complexidade e o controle granular do desenvolvimento de modelos.

- **Desempenho Geral:** Apesar de múltiplas otimizações, o modelo apresentou o desempenho mais baixo entre as três abordagens, com dificuldades notáveis na classificação de copos.

- **Pontos Fortes:**

    - **Controle e Flexibilidade:** Permite um ajuste fino de todos os aspectos da arquitetura (camadas, filtros, dropout, etc.), oferecendo total controle sobre o processo.

- **Pontos de Melhoria:**

    - **Alta Complexidade:** A configuração e o ajuste de hiperparâmetros são processos complexos e demorados, representando uma barreira técnica significativa.

    - **Resultados Inferiores:** Mesmo com diversas tentativas de regularização e ajuste, o modelo não conseguiu generalizar de forma eficaz, indicando a necessidade de uma arquitetura mais sofisticada ou de um dataset ainda maior.

- **Recomendação para a FarmTech:** Embora o conhecimento em construir CNNs seja fundamental, para a finalidade de detecção de objetos, esta abordagem é menos eficiente que o YOLO. A complexidade de desenvolvimento e os resultados inferiores a tornam uma opção inviável para as soluções ágeis e de alta performance que a FarmTech Solutions busca oferecer a seus clientes.

## 5. Execução da Solução Completa
Toda a implementação, o passo a passo dos treinamentos, as análises críticas e as conclusões detalhadas estão documentadas nos Jupyters Notebooks deste repositório.
É possivel encontralos na pasta Scripts/

## 6. Vídeo de Demonstração
Video demonstrativo do funcionamento

Link para o Vídeo: https://youtu.be/tGDrKnAMwBw

