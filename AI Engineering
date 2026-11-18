
> **Legenda:** ==🔴 **Correção**== algo impreciso ou errado no original · ==🔵 **Aprofundamento**== conteúdo além do curso · ==🟡 **Atenção**== pegadinhas e conceitos que confundem

## INTRODUÇÃO
### O que é Inteligência Artificial?

* IA é o campo que constrói sistemas capazes de realizar tarefas que, em humanos, exigiriam inteligência: reconhecer imagens, entender linguagem, tomar decisões, planejar.
* Tudo começou com a dúvida: **Computadores podem pensar como seres humanos?**
* **Teste de Turing** (Alan Turing, 1950) -> Também chamado de *"Jogo da Imitação"*. Um avaliador conversa por texto, ao mesmo tempo, com um ser humano e com um computador, sem saber quem é quem. Se o avaliador não conseguir distinguir qual dos dois é a máquina, o computador **"passa"** no teste.
   * ==🟡 **Atenção:** o teste mede se o **comportamento** é indistinguível do humano, não se a máquina "pensa" ou "entende". Turing trocou a pergunta filosófica por uma pergunta testável==
   * ==🔵 **Aprofundamento:**== LLMs modernos conseguem enganar pessoas em conversas curtas e mesmo assim cometem erros que nenhum humano cometeria. Hoje o teste é visto mais como marco histórico. Na prática, modelos são avaliados com **benchmarks** e **evals** específicos para cada tarefa.

### Subcampos da Inteligência Artificial

* **Hierarquia** -> Os campos ficam um dentro do outro: **IA ⊃ Machine Learning ⊃ Deep Learning**, e a IA generativa moderna está quase toda dentro de Deep Learning.
   * ==🔴 **Correção:**== a hierarquia "Deep Learning ⊃ IA Generativa" não é estrita. Existiam modelos generativos antes do Deep Learning (cadeias de Markov, por exemplo). O correto é: *a IA generativa atual é baseada principalmente em Deep Learning*.
   * ==🔵 **Aprofundamento:**== existe IA fora de Machine Learning. Sistemas especialistas com regras escritas à mão, algoritmos de busca (como o de um GPS) e motores de xadrez clássicos são IA sem aprendizado a partir de dados.

* **Machine Learning**
Em vez de programar as regras, você mostra exemplos e o algoritmo **aprende os padrões sozinho**. Exemplo -> O modelo analisa 1000 fotos **rotuladas** (*"isto é cachorro" / "isto não é cachorro"*), aprende o que diferencia uma da outra e depois classifica fotos novas. Esse tipo de aprendizado com exemplos rotulados se chama **aprendizado supervisionado**.
   * ==🔵 **Aprofundamento:**== existem três tipos principais de aprendizado:

| Tipo | Dados | Exemplo |
|---|---|---|
| **Supervisionado** | Exemplos com rótulo (entrada -> resposta certa) | Classificar e-mails como spam; prever preço de imóvel |
| **Não supervisionado** | Dados sem rótulo; o modelo encontra a estrutura | Agrupar clientes por comportamento de compra |
| **Por reforço** | Recompensas e punições por ações | Robô aprendendo a andar; IA de jogos |

* LLMs usam os três: o pré-treino é **autossupervisionado** (o próprio texto fornece o rótulo, que é a próxima palavra), o ajuste de instruções é supervisionado e o alinhamento usa reforço (RLHF).

* **Deep Learning**
Subcampo do Machine Learning que usa **redes neurais profundas** (com muitas camadas). Cada camada transforma a entrada em representações cada vez mais abstratas: numa imagem, as primeiras camadas detectam bordas, as do meio detectam formas e as últimas, objetos inteiros. Internamente, a rede é formada por **parâmetros**, números organizados em matrizes, que são ajustados durante o treinamento.
   * ==🔴 **Correção:**== "parâmetros" inclui **pesos** (*weights*) e **vieses** (*biases*). Na prática as pessoas falam "pesos" para tudo, e tudo bem.
   * ==🔴 **Correção:**== nem todo modelo de Deep Learning responde "por meio de probabilidades". Classificadores e LLMs produzem probabilidades, mas um modelo que prevê a temperatura de amanhã devolve um número direto (**regressão**).

* **IA Generativa**
Modelos capazes de **gerar conteúdo novo**: textos, imagens, áudios, vídeos, códigos etc. Os **modelos de linguagem (LLMs)**, como o ChatGPT e o Claude, são o exemplo mais conhecido. Para imagens, as arquiteturas dominantes são os **modelos de difusão**.

### Processo de aprendizado

* **FLUXO:** **Data** (dados) -> **Training** (treino) -> **Model** (modelo) -> **Inference** (inferência). O modelo aprende uma vez (treino, caro) e depois é usado milhões de vezes (inferência, barata por chamada).
* **TRAINING** -> O modelo processa uma **quantidade massiva de dados** e ajusta seus **parâmetros** para capturar padrões. O texto é dividido em **tokens**, cada token vira um número (um ID) e depois um vetor que a rede consegue processar.
   * ==🔵 **Aprofundamento:** como o ajuste acontece== -> o ciclo se repete bilhões de vezes:
      1. O modelo faz uma previsão (por exemplo, qual é a próxima palavra)
      2. Uma **função de perda** (*loss*) mede o tamanho do erro
      3. O **backpropagation** calcula quanto cada parâmetro contribuiu para o erro (o *gradiente*)
      4. O **gradiente descendente** ajusta cada parâmetro um pouquinho na direção que reduz o erro
   * É aqui que entra a matemática que vamos estudar: derivadas (gradiente), matrizes (as camadas) e probabilidade (as previsões).
   * ==🔵 **Aprofundamento:** as etapas de um LLM==
      1. **Pré-treino** -> o modelo lê trilhões de tokens da internet, livros e código, aprendendo a prever o próximo token. Sai daqui um "autocompletar" muito poderoso, que ainda não sabe conversar
      2. **Ajuste de instruções (SFT)** -> treino com exemplos de pergunta e resposta ideal. O modelo aprende o formato de assistente
      3. **Alinhamento (RLHF, DPO e similares)** -> humanos ou outros modelos comparam respostas, e o modelo aprende a preferir as melhores, mais úteis e mais seguras
* ==🟡 O modelo **NÃO** guarda os dados em um banco de dados. Ele guarda apenas o que aprendeu deles, na forma de parâmetros==
   * ==🟡 **Atenção:**== isso não significa que ele nunca reproduz trechos do treino. Textos que aparecem muitas vezes (licenças de software, trechos famosos) podem ser **memorizados** quase palavra por palavra. Por isso existe preocupação com vazamento de dados privados usados no treino.
* **INFERENCE** -> É o **uso** do modelo já treinado: você manda uma entrada e recebe uma saída. Na inferência os parâmetros ficam **congelados**; o modelo não aprende com a sua conversa.
   * ==🟡 **Atenção:** quando um chatbot "lembra" de algo que você disse antes, não é aprendizado. O aplicativo reenvia o histórico da conversa a cada mensagem, dentro do contexto (Aula 2)==

### RAG (Retrieval-Augmented Generation)

* **O que é?**
   * RAG = **buscar** informação relevante em uma fonte externa e **colocar no prompt** antes de o modelo gerar a resposta.
   * ==🟡 Você quer saber sobre a política de reembolso de uma empresa. A IA não foi treinada com esses dados. Então o sistema busca os trechos da política e os entrega junto com a pergunta. Ou seja, você está fornecendo ao modelo **dados externos para complementar o contexto**==
   * ==🔴 **Correção:**== RAG não é só "somar" o conhecimento do modelo com dados externos. O objetivo geralmente é fazer o modelo **priorizar** os dados recuperados sobre a própria memória, que pode estar desatualizada.
   * ==🔵 **Aprofundamento:**== busca na web também é uma forma de RAG: o "retriever" é um buscador em vez de um banco vetorial. A fonte pode ser qualquer coisa: SQL, API, documentos.
* **Passo a passo**
   * **Fase offline** (feita uma vez, ou quando os documentos mudam):
      1. **Ingestão** -> extrair o texto dos documentos (PDF, HTML, banco de dados)
      2. **Chunking** -> dividir em trechos (*chunks*). Trecho grande demais dilui o significado; pequeno demais perde contexto. É comum usar algumas centenas de tokens, com uma pequena sobreposição entre trechos vizinhos
      3. **Embedding** -> converter cada trecho em um vetor que representa seu significado (Aula 3)
      4. **Indexação** -> guardar vetores, texto original e metadados (fonte, data, página) em um **banco vetorial**
   * **Fase online** (a cada pergunta):
      1. **Embedding da pergunta**, com o **mesmo** modelo de embedding usado nos documentos
      2. **Recuperação** -> buscar os *k* trechos mais próximos da pergunta (o **top-k**). Ver o visual da Aula 3
      3. **Reranking** (opcional, muito usado) -> um segundo modelo, mais preciso e mais lento, reordena os candidatos
      4. **Geração** -> os trechos entram no prompt junto com a pergunta e uma instrução do tipo *"responda apenas com base nos trechos abaixo e cite a fonte"*
   * ==🟡 O modelo **NÃO** muda. A base de dados fica **fora dele**, e a informação é usada apenas naquela resposta. É como fazer uma **prova com consulta**==
* **Por que utilizar RAG?**
   * Consulta de **informações atualizadas ou privadas**, que não estavam no treinamento
   * **Menos "alucinação"**, por se ancorar em fontes reais
   * **Rastreabilidade** das respostas, mostrando a origem de cada informação
   * **Custo mais barato** -> Atualizar a base é muito mais barato que retreinar ou fazer fine-tuning
   * ==🔵 **Aprofundamento:**== **controle de acesso**. Dá para filtrar os documentos pelo usuário que perguntou, o que é impossível com conhecimento gravado nos parâmetros.
* **Limitações**
   * A qualidade da resposta **depende da recuperação**. Trecho errado entra, resposta errada sai. Na prática, a maioria dos problemas de RAG está na busca, não no LLM.
   * ==🔴 **Correção:**== RAG **reduz** a alucinação, mas não elimina. O modelo ainda pode interpretar mal um trecho ou misturar com o que "lembra" do treino.
   * ==🔵 **Aprofundamento:**== perguntas que exigem juntar informação espalhada (*"quantos contratos venceram em 2025?"*) costumam falhar com RAG simples, porque o top-k traz só alguns trechos. Esses casos pedem SQL, agentes ou outras técnicas.
   * ==🔵 **Aprofundamento:**== o contexto tem tamanho limitado e custo por token, então não dá para simplesmente mandar todos os documentos.

### Fine-Tuning (Ajuste Fino)

* **O que é?**
   * É **continuar o treinamento** de um modelo já pronto com um **conjunto pequeno e específico** de exemplos (geralmente pares de *pergunta -> resposta ideal*). O resultado é uma **nova versão do modelo**, com os parâmetros ajustados.
   * ==🟡 Fine-tuning muda o **VALOR** dos parâmetros. É como afinar um violão: as cordas continuam sendo seis, o que muda é a tensão de cada uma==
* **Para que serve?**
   * Ajustar **comportamento e reação** do modelo: tom de voz, formato de resposta, estilo
   * **Especializar** o modelo em uma tarefa: classificar tickets, extrair dados de documentos, escrever em linguagem jurídica ou médica
   * **Eficiência** -> Um modelo menor com fine-tuning pode fazer uma tarefa específica tão bem quanto um modelo maior, sendo mais barato e mais rápido
* **Tipos**
   * **Fine-tuning completo** -> Atualiza todos os parâmetros do modelo. É caro e exige muita memória de GPU.
   * **LoRA** (*Low-Rank Adaptation*) -> Congela o modelo original e treina pares de matrizes pequenas acopladas às camadas existentes. Treina tipicamente menos de 1% dos parâmetros. É o mais usado hoje.
   * **QLoRA** -> O mesmo que o LoRA, mas com o modelo base comprimido (quantizado), cabendo em GPUs menores.
   * ==🔴 **Correção:**== as notas diziam que o fine-tuning mantém "a mesma quantidade de parâmetros" e, logo depois, que o LoRA treina "uma pequena camada extra". As duas coisas se contradizem. O correto: o fine-tuning **completo** mantém a quantidade; o LoRA **adiciona** um pequeno conjunto de parâmetros (o *adapter*). Depois do treino, o adapter pode ser **mesclado** de volta aos pesos originais, e aí a quantidade volta a ser a mesma.
   * ==🔵 **Aprofundamento:**== com LoRA você pode ter **um** modelo base e vários adapters pequenos (um por cliente ou por tarefa), trocando em tempo de execução.
* **Limitações**
   * Precisa de **dados de boa qualidade** (centenas a milhares de exemplos). Dado ruim gera modelo ruim.
   * Risco de **overfitting** -> O modelo decora os exemplos em vez de aprender a generalizar
   * É **ruim para ensinar conhecimento novo**: o modelo pode memorizar mal, misturar informações ou inventar detalhes. Para conhecimento, use RAG.
   * ==🔵 **Aprofundamento:**== **esquecimento catastrófico**. Ajustar demais numa tarefa pode piorar o modelo em outras que ele fazia bem.

### Retreinamento

* Treinar com um **volume massivo de dados**, do zero (**pré-treino**) ou continuando um pré-treino existente (**pré-treino continuado**), para que o modelo ganhe conhecimento e capacidades gerais novas. É o que as empresas fazem para lançar uma **nova geração** de modelo.
* **Extremamente custoso** (milhões) e **demorado** (semanas ou meses)
* ==🟡 Fine-tuning e retreinamento usam o **MESMO mecanismo** (ajustar parâmetros com gradiente descendente). O que muda é a **escala**, os **dados** e o **objetivo**==
   * ==🔴 **Correção (nuance):**== o pré-treino usa texto bruto para prever o próximo token; o fine-tuning usa exemplos curados de entrada e saída; o alinhamento usa preferências entre respostas.
   * ==🟡 **Atenção:**== "retreinamento" não é um termo técnico padronizado. Em vagas e artigos você vai ver *pre-training*, *continued pre-training* e *post-training*.

### Comparação

| | Dados | Muda o modelo? | Custo | Objetivo |
|---|---|---|---|---|
| **Prompt engineering** | Instruções e exemplos no prompt | Não | Muito baixo | Guiar a resposta |
| **RAG** | Base externa, consultada na hora | Não | Baixo | Dar informação |
| **Fine-tuning** | Centenas a milhares de exemplos | Sim | Médio/baixo | Ajustar comportamento |
| **Pré-treino** | Trilhões de tokens | Sim (cria o modelo) | Altíssimo | Conhecimento e capacidades gerais |

* ==🟡 **Regra prática:** RAG ensina ao modelo **O QUE** saber. Fine-tuning ensina **COMO** se comportar. Muitas aplicações usam os dois juntos==
* ==🔵 **Aprofundamento:** a ordem que um engenheiro segue== -> Tente primeiro **prompt engineering**. Não resolveu e falta informação? **RAG**. O problema é formato, estilo ou custo em escala? **Fine-tuning**. Pular direto para fine-tuning é um erro comum e caro.

### INTRODUÇÃO: Resumo
-> IA é um campo amplo; **IA ⊃ ML ⊃ Deep Learning**
-> Machine Learning aprende padrões a partir de exemplos (supervisionado, não supervisionado, por reforço)
-> LLM (*Large Language Model*) é um modelo de linguagem de larga escala, com bilhões de parâmetros, treinado para prever o próximo token
-> Training vs Inference: Training ajusta os parâmetros com uma grande base de dados. Inference é o uso do modelo congelado (*a resposta da IA*)
-> RAG é uma arquitetura que busca dados externos e os coloca no contexto do modelo (*documentos, busca na internet etc*)
-> Ordem de tentativa: **prompt -> RAG -> fine-tuning**



## AULA 2

### Tokens, Contexto e Geração

- #### O que é um Token?
	É a unidade de texto que o modelo processa numericamente. Pode ser uma palavra inteira, um pedaço de palavra, um sinal de pontuação ou um espaço.
	- ==🔴 **Correção:**== o texto é quebrado em pedaços de **texto**, não "pedaços de contexto". Contexto é outro conceito (abaixo).
	- ==🔵 **Aprofundamento:**== o caminho completo é **texto -> tokens -> IDs numéricos -> vetores (embeddings internos)**. O vocabulário de um LLM tem dezenas a centenas de milhares de tokens possíveis.
	- ==🔵 **Aprofundamento:**== em inglês, um token tem em média uns 4 caracteres. **Português costuma gastar mais tokens** para o mesmo conteúdo, porque os tokenizadores foram treinados com mais inglês. Isso afeta custo e espaço no contexto.
	- ==🟡 **Atenção:** por enxergar tokens e não letras, LLMs tropeçam em tarefas como contar letras de uma palavra ou inverter uma string==

- #### Context Window (Janela de Contexto)
	Quantidade máxima de **tokens** que o modelo consegue considerar **em uma chamada**: instruções do sistema, histórico, documentos, a pergunta **e a resposta gerada**.
	- ==🔴 **Correção:**== é medida em **tokens** e inclui a **saída**, não só a entrada.
	- ==🔵 **Aprofundamento:**== é uma memória de trabalho **sem estado**. Cada chamada à API é independente; quem guarda a conversa é a sua aplicação, que reenvia o histórico toda vez. Conversas longas ficam mais caras e, no limite, precisam ser resumidas ou cortadas.
	- ==🟡 **Atenção:** caber no contexto não garante que o modelo use bem. Informação no meio de contextos muito longos tende a ser menos aproveitada (efeito *lost in the middle*)==

- #### Prompt
	Tudo o que você envia ao modelo: instruções, contexto, exemplos e a pergunta. Em APIs ele é dividido em **system prompt** (regras e papel do assistente) e **mensagens** (o diálogo).

- #### Temperature
	Controla o quanto a escolha do próximo token é aleatória. A cada passo, o modelo calcula uma pontuação (*logit*) para cada token do vocabulário, e a função **softmax** transforma essas pontuações em probabilidades. A temperatura *T* divide as pontuações antes do softmax:

$$P(\text{token}_i) = \frac{e^{z_i / T}}{\sum_j e^{z_j / T}}$$

- **T baixa (perto de 0)** -> a distribuição fica concentrada no token mais provável. Respostas previsíveis. Bom para extração de dados, classificação e código.
- **T alta (acima de 1)** -> a distribuição fica achatada e tokens improváveis ganham chance. Mais variedade, mais risco de sair do trilho. Bom para brainstorm.
- ==🟡 **Atenção:** temperatura 0 não garante saídas 100% idênticas em todas as chamadas, por detalhes numéricos e de infraestrutura==
- ==🔵 **Aprofundamento:**== existem outros controles de amostragem, como **top-p** (só sorteia entre os tokens que somam p% da probabilidade) e **top-k**.

### Do Input à Response

- **Usuário faz uma pergunta -> Mensagem é quebrada em *tokens* -> Modelo considera instruções + histórico -> Gera uma sequência de *tokens* a partir de probabilidades -> Formula a resposta**
- Em resumo: TEXTO -> TOKEN -> CONTEXTO -> GERAÇÃO -> RESPOSTA
- ==🔵 **Aprofundamento:** a geração é **autoregressiva**== -> o modelo não gera a resposta inteira de uma vez:
	1. Lê todo o contexto e calcula as probabilidades do próximo token
	2. Escolhe um token (de acordo com a temperatura)
	3. Anexa esse token ao contexto
	4. Repete até gerar um token de fim ou atingir o limite
- É por isso que as respostas aparecem "digitando" na tela (*streaming*), e por isso que um erro no começo da resposta tende a contaminar o resto: o modelo continua a partir do que já escreveu.


## AULA 2: Training x Context

| | Training | Context |
|---|---|---|
| **O que muda** | Os parâmetros do modelo | Nada no modelo; só a entrada daquela chamada |
| **Duração** | Permanente | Some ao fim da chamada |
| **Custo** | Alto, feito poucas vezes | Pago por token, a cada chamada |
| **Quando acontece** | Antes de o modelo ser usado | Durante a inferência |
| **Exemplos** | Pré-treino, fine-tuning | Histórico da conversa, RAG, anexos, buscas na web, resultados de ferramentas |

- ==🔴 **Correção:**== o treino não muda "a base de arquivos" do modelo. Ele muda os **valores dos parâmetros**; não há arquivos ou documentos guardados dentro do modelo.

### Hallucination (Alucinação)
- ==🔴 **Correção importante:**== alucinação **não** é um resultado "improvável e sem nexo". É quase o contrário: é o modelo gerar algo **fluente, convincente e plausível, mas falso** ou sem base nas fontes. Uma citação de artigo que não existe, uma função de biblioteca inventada, uma data errada dita com confiança. O perigo está justamente em **parecer certo**.
- **Por que acontece?** O modelo foi treinado para gerar o texto **mais provável**, não o texto **verdadeiro**. Quando não sabe, ele não tem um mecanismo nativo de "não sei" e completa com o que soa certo.
- **Fatores que aumentam o risco:**
	-> **Falta de contexto** ou pergunta sobre algo que o modelo nunca viu (dados privados, eventos recentes, nichos)
	-> **Perguntas que pressupõem algo falso** (*"por que Einstein ganhou dois Nobel?"*): o modelo tende a seguir a premissa
	-> **Pedidos de detalhes muito específicos**: números, citações, URLs, referências bibliográficas
	-> **Temperatura alta** aumenta a variação e pode contribuir
- ==🔴 **Correção:**== temperatura alta e dados desatualizados contribuem, mas não são as causas principais. Modelos alucinam **mesmo com temperatura 0**. E dado desatualizado é um problema um pouco diferente: o modelo pode dar uma resposta que *era* verdadeira.

### Grounding
-> Consiste em "ancorar" a resposta em **fontes verificáveis**, em vez de depender só da memória do modelo
-> Serve para fazer o modelo devolver respostas corretas e rastreáveis
-> **Técnicas:**
	- **RAG** com documentos da empresa
	- **Ferramentas e APIs**: consultar o banco de dados, uma API de cotação, uma busca na web
	- **Instruções explícitas**: *"responda apenas com base nos documentos; se a resposta não estiver neles, diga que não sabe"*
	- **Citações obrigatórias**: exigir que cada afirmação aponte o trecho de origem, o que facilita verificar
	- **Validação**: checar a saída com código (o JSON é válido? o ID existe no banco?) ou com um segundo modelo avaliador

==🟡 **LLMs não são bancos de dados:** para fatos atuais e informações críticas, conecte os modelos a **Sources of Truth** (fontes da verdade) para garantir contextualização atual e integridade das respostas==

### AULA 2: Resumo
- Tokens são pedaços de texto, as unidades de processamento do modelo
- Context Window é o limite de tokens por chamada, incluindo a resposta
- A geração é autoregressiva: um token por vez, escolhido por probabilidades
- Temperatura muda a variabilidade das respostas, não a "inteligência"
- Hallucination é uma resposta plausível e falsa; exige Grounding e validação para ser evitada


## AULA 3: Como a IA entende o significado das palavras + Embeddings

### Busca por palavra x Busca por significado

- **Keyword Search** (busca por palavra-chave) -> encontra documentos que contêm **as mesmas palavras** da pergunta. Algoritmo clássico: **BM25**, que pontua pela frequência do termo no documento e pela raridade dele na coleção.
	- Força: excelente para termos exatos, como códigos de produto, nomes próprios, números de erro e siglas
	- Fraqueza: não entende sinônimos. *"Como cancelar minha assinatura"* não encontra um documento que diz *"encerramento do plano"*
- **Semantic Search** (busca semântica) -> encontra documentos com **significado parecido**, mesmo sem nenhuma palavra em comum. Funciona comparando embeddings.
	- Força: entende sinônimos, paráfrases e até outros idiomas
	- Fraqueza: pode falhar em termos exatos (os códigos "ERR-4012" e "ERR-4021" parecem quase iguais para ela)
- ==🔵 **Aprofundamento:**== em produção, o padrão é a **busca híbrida**, que combina as duas e une os rankings.

### Embedding
- Um **vetor de números** que representa o significado de um texto (ou imagem, ou áudio). É gerado por um **modelo de embedding**, treinado para que textos com significado parecido virem vetores próximos.
- ==🔵 **Aprofundamento:**== embeddings têm **centenas ou milhares de dimensões** (384, 768, 1536 e 3072 são tamanhos comuns). Cada dimensão isolada não tem um significado legível por humanos; o significado está na posição do vetor como um todo.
- ==🟡 **Atenção:** o **modelo de embedding é diferente do LLM** que gera a resposta. No RAG você usa dois modelos: um pequeno e barato para gerar vetores, outro grande para escrever a resposta==
- ==🟡 **Atenção:** documentos e perguntas precisam ser convertidos pelo **mesmo** modelo de embedding. Trocou o modelo? Precisa gerar todos os vetores de novo==

### Similaridade semântica
- Texto -> Embedding -> Comparação -> Resultado
- Em resumo: TEXTO -> VETOR -> SIMILARIDADE -> BUSCA
- A medida mais usada é a **similaridade de cosseno**, que mede o ângulo entre dois vetores:

$$\cos(\theta) = \frac{\mathbf{a} \cdot \mathbf{b}}{\lVert \mathbf{a} \rVert \, \lVert \mathbf{b} \rVert}$$

- Perto de **1** -> mesma direção, significado muito parecido
- Perto de **0** -> sem relação
- **Negativo** -> direções opostas (raro na prática com embeddings de texto)
- Outras medidas: **produto escalar** (igual ao cosseno quando os vetores estão normalizados, o que é comum) e **distância euclidiana** (distância em linha reta; menor = mais parecido).
- ==🟡 **Atenção:** "próximo" significa "aparece em contextos parecidos", não "significa a mesma coisa". "Quente" e "frio" podem ficar próximos, porque aparecem nas mesmas frases sobre temperatura. Similaridade não é o mesmo que relevância==
- ==🔵 **Aprofundamento:**== comparar a pergunta com milhões de vetores um a um seria lento. Bancos vetoriais usam índices de **busca aproximada** (*ANN*, como o HNSW), que acham os vizinhos mais próximos em milissegundos, trocando um pouco de precisão por muita velocidade.

- ##### ==🟡 Embedding não responde -> **Ajuda a encontrar a resposta**==

### Visual: proximidade entre vetores e o que entra no contexto

A pergunta vira um vetor, o sistema mede a distância até cada trecho da base e **só os k mais próximos** são colocados no prompt. O LLM nunca vê os outros.

![[rag-proximidade-vetores.png]]

*Exemplo ilustrativo em 2 dimensões: 8 trechos de uma base de atendimento, 1 pergunta, k = 3. O #4 ("Trocas de produto com defeito") é bem relacionado ao tema, mas ficou abaixo do corte e não chega ao modelo.*

- **Proximidade não aumenta a "probabilidade": ela decide quem entra**
	- ==🔴 **Correção:**== a recuperação não sorteia nada. Ela calcula a similaridade, **ordena** e aplica um **corte**: os *k* primeiros (ou todos acima de um limiar de similaridade) entram com certeza, o resto fica fora com certeza. O #3 e o #4 podem ter notas parecidas, e mesmo assim um entra e o outro não.
	- **Por isso o ajuste de k importa:** k pequeno pode deixar de fora a informação necessária; k grande traz ruído, custa mais tokens e pode confundir o modelo. Um padrão comum é buscar uns 20 a 50 candidatos e usar um **reranker** para reduzir aos 3 a 10 melhores.
	- **Mais próximo não é o mesmo que correto:** um trecho pode ser o vizinho mais próximo e ainda assim não responder à pergunta, ou estar desatualizado.
- **Onde a probabilidade aparece de verdade**
	1. **Busca aproximada (ANN)** -> em bases grandes, o índice pode, raramente, deixar escapar um vizinho que deveria estar no top-k
	2. **Na geração** -> depois que os trechos estão no contexto, o LLM gera a resposta token a token, por probabilidades. Ele tende a se apoiar mais nos trechos que respondem melhor à pergunta, por meio do mecanismo de **atenção**. Mas isso é decisão do LLM sobre o texto, não da distância entre embeddings
	3. **Posição no prompt** -> trechos no início e no fim de um contexto longo costumam ser mais aproveitados que os do meio

==🟡 **Em uma frase:** a proximidade decide **SE** o trecho chega ao modelo; o modelo decide **QUANTO** ele pesa na resposta==

### AULA 3: Resumo
- Embedding representa significado numericamente
- Vetores próximos tendem a ter significado mais próximo
- Semantic Search encontra relações além das palavras exatas; em produção, combine com Keyword Search (busca híbrida)
- A recuperação é um **ranking com corte** (top-k), não uma escolha por probabilidade
- Embeddings são uma peça central de muitos RAGs


## Correções feitas

| Onde | Nas notas originais | Correto |
|---|---|---|
| Subcampos | DL ⊃ IA Generativa (estrito) | A IA generativa *atual* é majoritariamente DL; existem modelos generativos sem DL |
| Deep Learning | Todo modelo responde por probabilidades | Classificadores e LLMs sim; modelos de regressão devolvem números diretos |
| Treinamento | O modelo não guarda os dados | Correto em geral, mas trechos muito repetidos podem ser memorizados |
| RAG | Soma o conhecimento do modelo com dados externos | O objetivo é o modelo **priorizar** os dados recuperados |
| RAG | Evita alucinação | **Reduz**, não elimina |
| Fine-tuning / LoRA | Mesma quantidade de parâmetros (e, ao mesmo tempo, camada extra) | LoRA adiciona um adapter pequeno, que pode ser mesclado depois |
| Token | Pedaços de contexto | Pedaços de **texto** |
| Context Window | Informação recebida | Limite em **tokens**, incluindo a saída |
| Training x Context | Muda a base de arquivos | Muda os **valores dos parâmetros** |
| Alucinação | Resultado improvável e sem nexo | Resultado **plausível e convincente, mas falso** |
| Alucinação | Causada por temperatura alta e dados desatualizados | Causa principal: o modelo otimiza o texto provável, não o verdadeiro; ocorre até com temperatura 0 |
| Aula 3 | Proximidade aumenta a probabilidade de o trecho ser usado | A recuperação é um **ranking**: os *k* mais próximos entram, o resto fica de fora |
