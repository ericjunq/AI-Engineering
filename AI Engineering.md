## O que é Inteligência Artificial?

* Tudo começou com a dúvida: **Computadores podem pensar como seres humanos?** Eles poderiam responder como uma pessoa?
* **Teste de Turing** (Alan Turing, 1950) -> Também chamado de *"Jogo da Imitação"*. Um avaliador conversa por texto, ao mesmo tempo, com um ser humano e com um computador, sem saber quem é quem. Se o avaliador não conseguir distinguir qual dos dois é a máquina, o computador **"passa"** no teste.

### Subcampos da Inteligência Artificial

* **Hierarquia** -> Os campos ficam um dentro do outro: **IA ⊃ Machine Learning ⊃ Deep Learning ⊃ IA Generativa**
* **Machine Learning**
A ideia do ML é **aprender padrões a partir de exemplos**, em vez de seguir regras programadas manualmente. Exemplo -> O modelo analisa 1000 fotos **rotuladas**, algumas com cachorro e outras sem (*"isto é cachorro" / "isto não é cachorro"*), e aprende os padrões que diferenciam uma da outra. A partir daí, ele analisa uma imagem nova e procura esses padrões para saber se há um cachorro nela ou não. Esse tipo de aprendizado com exemplos rotulados se chama **aprendizado supervisionado**.
* **Deep Learning**
Subcampo do Machine Learning que usa **redes neurais profundas** (com muitas camadas). Aprendem padrões complexos por meio de um enorme volume de dados. Internamente, a rede é formada por **parâmetros** (também chamados de **pesos**), números organizados em matrizes, que são ajustados durante o treinamento. É com base nesses parâmetros que o modelo gera respostas, **por meio de probabilidades**.
* **IA Generativa**
Modelos capazes de **gerar conteúdo novo**: textos, imagens, áudios, vídeos, códigos etc. A maioria é baseada em Deep Learning. Os **modelos de linguagem (LLMs)**, como o ChatGPT e o Claude, são um exemplo.

### Processo de aprendizado

* **TRAINING** -> Treinamento do modelo por meio de uma **quantidade massiva de dados**, específicos ou gerais. O texto é dividido em **tokens** (pedaços de palavras convertidos em números) para que o modelo consiga processá-lo. Durante o treino, os **parâmetros** do modelo são ajustados para capturar os padrões desses dados.
   * ==🟡 O modelo **NÃO** guarda os dados em um banco de dados. Ele guarda apenas o que aprendeu deles, na forma de parâmetros ==
* **FLUXO:** **Data** (dados: podem ser textos, imagens, vídeos, código) -> **Training** (treino) -> **Model** (modelo) -> **Inference** (inferência).
* Em resumo, dados são usados no treinamento de modelos, que, depois de treinados, podem responder perguntas (**inferência**) com base no aprendizado obtido a partir dos dados recebidos.

### RAG (Retrieval-Augmented Generation)

* **Como o RAG Funciona?**
   * Imagine que um modelo foi treinado com dados de 3 anos atrás. Muita informação pode ter sido atualizada/alterada de lá pra cá. Então você fornece ao modelo um PDF ou o coloca para fazer uma pesquisa na internet. **RAG é o uso do conhecimento que o modelo já tem somado a dados externos, buscados na hora da pergunta, para gerar a resposta.**
   * ==🟡 Você quer saber sobre a política de reembolso de uma empresa. A IA não foi treinada com esses dados. Então a IA é alimentada com documentos e informações sobre a empresa. Ou seja, você está fornecendo ao modelo **dados externos para complementar o contexto** ==
   * **Passo a passo:**
      * **Indexação** -> Os documentos são divididos em trechos, convertidos em vetores numéricos (**embeddings**) que representam seu significado e guardados em uma base externa (**banco vetorial**).
      * **Recuperação** -> Quando chega uma pergunta, o sistema busca **apenas os trechos mais relevantes** para ela, e não o documento inteiro.
      * **Geração** -> Os trechos encontrados são colocados no prompt junto com a pergunta, e o modelo gera a resposta com base neles.
   * ==🟡 O modelo **NÃO** muda. A base de dados fica **fora dele**, e a informação é usada apenas naquela resposta. É como fazer uma **prova com consulta** ==
   * **Por que utilizar RAG?**
      * Consulta de **informações atualizadas ou privadas**, em dados que não estavam no treinamento
      * **Menos "alucinação"** nas respostas, por se ancorar em fontes reais, reduzindo "invenções"
      * **Rastreabilidade** das respostas, mostrando a origem de cada informação
      * **Custo mais barato** -> Atualizar a base de dados é mais barato que retreinar ou fazer fine-tuning do modelo
   * **Limitações**
      * A qualidade da resposta **depende da recuperação**. Se o sistema trouxer trechos errados ou incompletos, a resposta sai ruim.

### Fine-Tuning (Ajuste Fino)

* **O que é?**
   * É **continuar o treinamento** de um modelo já pronto com um **conjunto pequeno e específico** de exemplos (geralmente pares de *pergunta -> resposta ideal*). O resultado é uma **nova versão do modelo**, com a mesma arquitetura e a mesma quantidade de parâmetros, só que com os valores ajustados.
   * ==🟡 Fine-tuning muda o **VALOR** dos parâmetros, não a **QUANTIDADE**. É como afinar um violão: as cordas continuam sendo seis, o que muda é a tensão de cada uma ==
* **Para que serve?**
   * Ajustar **comportamento e reação** do modelo: tom de voz, formato de resposta, estilo
   * **Especializar** o modelo em uma tarefa: classificar tickets, extrair dados de documentos, escrever em linguagem jurídica ou médica
   * **Eficiência** -> Um modelo menor com fine-tuning pode fazer uma tarefa específica tão bem quanto um modelo maior, sendo mais barato e mais rápido
* **Tipos**
   * **Fine-tuning completo** -> Atualiza todos os parâmetros do modelo. É caro e exige muita memória.
   * **LoRA** -> Congela o modelo original e treina apenas uma pequena camada extra de parâmetros. Mais barato, é o mais usado hoje.
* **Limitações**
   * Precisa de **dados de boa qualidade** (centenas a milhares de exemplos)
   * Risco de **overfitting** -> O modelo decora os exemplos em vez de aprender a generalizar
   * É **ruim para ensinar conhecimento novo**: o modelo pode memorizar mal, misturar informações ou inventar detalhes

### Retreinamento

* Treinar o modelo novamente, **do zero ou continuando o pré-treino**, com um **volume massivo de dados**, para que ele ganhe conhecimento e capacidades gerais novas. É o que as empresas fazem para lançar uma **nova versão** de um modelo.
* **Extremamente custoso** (milhões) e **demorado** (semanas ou meses)
* ==🟡 Fine-tuning e retreinamento são o **MESMO processo** (ajustar parâmetros com dados). O que muda é a **escala** e o **objetivo** ==

### Comparação

| | Dados | Muda o modelo? | Custo | Objetivo |
|---|---|---|---|---|
| **RAG** | Base externa, consultada na hora | Não | Baixo | Dar informação |
| **Fine-tuning** | Poucos exemplos específicos | Sim | Médio/baixo | Ajustar comportamento |
| **Retreinamento** | Volume massivo | Sim | Altíssimo | Conhecimento e capacidades gerais |

* ==🟡 **Regra prática:** RAG ensina ao modelo **O QUE** saber. Fine-tuning ensina **COMO** se comportar. Muitas aplicações usam os dois juntos ==