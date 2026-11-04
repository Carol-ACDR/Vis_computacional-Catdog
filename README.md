# Classificação de Gatos e Cachorros com CNN

Este projeto compara redes convolucionais treinadas com diferentes representações de imagem para classificar gatos e cachorros. O notebook faz parte da unidade curricular de Visão Computacional da Pós-Graduação em Inteligência Artificial Aplicada.


## Notebook

- `Visão_Computacional_Desafio_Semana_1.ipynb`

## Objetivo

Avaliar como o pré-processamento visual e o número de épocas afetam uma CNN binária. São comparadas quatro entradas:

- imagens RGB;
- escala de cinza;
- magnitude das bordas de Sobel;
- contornos binarizados a partir de Sobel.

## Dataset

O projeto usa `cats_vs_dogs`, obtido automaticamente pelo TensorFlow Datasets.

- 23.262 imagens válidas;
- 11.658 exemplos da classe 0;
- 11.604 exemplos da classe 1;
- 1.738 arquivos corrompidos ignorados pelo TFDS na execução registrada.

As imagens são redimensionadas para `128 × 128` e normalizadas para o intervalo `[0, 1]`. O notebook utiliza 80% dos exemplos para treino e 20% para validação/teste.

## Modelo

A CNN contém três blocos convolucionais com 32, 64 e 128 filtros, max pooling, global average pooling, uma camada densa com 64 unidades e saída sigmoide. O treinamento usa Adam e binary cross-entropy.

## Resultados registrados

| Entrada | Treino — 5 épocas | Validação — 5 épocas | Treino — etapa de 10 épocas | Validação — etapa de 10 épocas |
|---|---:|---:|---:|---:|
| RGB | 74,51% | 76,51% | 89,71% | **88,42%** |
| Escala de cinza | 74,29% | 74,68% | 89,85% | 84,91% |
| Sobel | 74,60% | 77,91% | 86,14% | 82,36% |
| Contornos | 69,01% | 70,51% | 84,10% | 78,04% |

O melhor resultado salvo foi obtido com imagens RGB. Os filtros manuais removeram informações úteis, principalmente cor e textura.

> Os blocos chamados de “10 épocas” continuam treinando os mesmos modelos após as cinco primeiras épocas. Portanto, representam 15 épocas acumuladas, não um treinamento independente de 10 épocas.

## Como executar

```bash
pip install jupyter tensorflow tensorflow-datasets opencv-python pandas numpy matplotlib pillow scikit-learn
jupyter notebook "Visão_Computacional_Desafio_Semana_1.ipynb"
```

O download do dataset exige internet. Uma GPU compatível com TensorFlow é recomendada.


## Tecnologias

Python, TensorFlow/Keras, TensorFlow Datasets, OpenCV, NumPy, pandas e Matplotlib.

## Licença

Nenhuma licença foi definida. Verifique também os termos de uso do dataset antes de redistribuir imagens.
