# Named Entity Generation using PyTorch

This project implements an autoregressive token-level language model using PyTorch following [Bengio et al. 2000](http://dx.doi.org/10.1162/153244303322533223). The autoregressive token-level language model serves as the foundation for more recent architectures, such as GPT-2 and other large language models (LLMs). These models build upon the principles of autoregression, leveraging self-attention mechanisms and transformer architectures to capture long-range dependencies and generate coherent sequences of tokens. In this work, the approach is more simpler, given the embedding in the context-window, we use a simple MLP to predict the next token in a self-supervised manner.

this work is influenced by [karpathy makemore](https://github.com/karpathy/makemore)

## Dataset

The dataset used in this project was sourced from "IBGE Cidades", a system that provides comprehensive information about municipalities and states in Brazil, produced by the Brazilian Institute of Geography and Statistics (IBGE) and other sources. The dataset comprises names of neighborhoods and cities across Brazil. These names were extracted from the dataset to serve as the basis for training and evaluating the autoregressive token-level language model.

Each instance in the dataset consists of a sequence of tokens representing a named entity, such as the name of a neighborhood and a city

## Model Architecture

The model architecture is based on a simple multilayer perceptron (MLP) that predicts the next token in an autoregressive manner. Given the embedding in the context-window, the model takes the embedded tokens as input and passes them through multiple fully connected layers to predict the next token. This approach simplifies the autoregressive token-level language modeling task while maintaining effectiveness.

## Used Technologies

- PyTorch: Deep learning framework used for implementing the neural network
- Pandas: Data manipulation library used for preprocessing and handling datasets.
- Seaborn and Matplotlib: Data visualization libraries used for visualizing training progress and model performance.

## Training Process

The training process involves optimizing the model parameters to minimize cross-entropy loss. The model is trained using AdamW, with backpropagation used to update the model weights. The training data is fed to the model in batches, and the model learns to predict the next token in the sequence given the previous tokens. Training occurs iteratively over multiple epochs until the model converges and achieves satisfactory performance.

## Results

Sample results from the trained autoregressive token-level language model:
```
	- Novo Horizonte - Ipatinga 
	- Divinópolis II - Angra dos 
	- Centro - Ipatinga 
	- Itaí Destinação Industrial - Carvde Minas 
	- Santa Maria - Jardim Belo Horizonte 
	- Bom Retiro - Ampére 
	- Honório Brasília - Belém 
	- Parque Cidade Luz - Maringá 
	- Coração Verde - Brusque 
	- Ideal - Taquara
```

The model also can receive initial prompts, for example, starting with "Santa " we can get: 
```
	Santa Terezinha - Forquilhinha 
	Santa Terezinha - Campos dos Independência Santa Terezinha - 6 do Araguaia 
	Santa Mônica - Bebedouro 
	Santa Bárbara - Camaquã 
	Santa Maria Bertila - Guiratinga 
	Santa Mônica - Uberlândia 
	Santa Luzia - Embu das Artes 
	Santa Izabel - Jaguari 
	Santa Mônica - Lages
```

These results demonstrate the model's ability to generate coherent sequences of tokens resembling named entities based on the learned patterns in the training data.


## Working
Right now the model is in its simplest form, it is possible to get better tokenization using libs like tiktoken to allow the model more flexibility. Beside making the model more complex, I want to start some sort of reinforcement learning to the model learn the [neighbors name] - [city name] structure. This can be a lot of fun!