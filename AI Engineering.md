
## INTRODUÇÃO

### O que é Inteligência Artificial?

* **Inteligência Artificial (IA)** é o campo da computação que constrói sistemas capazes de realizar tarefas que, em humanos, exigiriam inteligência: reconhecer imagens, entender e produzir linguagem, tomar decisões, planejar, resolver problemas.
* A diferença para um programa comum está em **como** o sistema chega à resposta:
   * **Programa tradicional** -> o programador escreve todas as regras (*"se o valor for maior que 1000, peça aprovação"*). O computador só executa.
   * **Sistema de IA** -> lida com situações que são difíceis ou impossíveis de descrever com regras fixas (*"esta foto tem um cachorro?"*, *"este e-mail é golpe?"*).
* Tudo começou com a dúvida: **Computadores podem pensar como seres humanos?** Eles poderiam responder como uma pessoa?

#### Teste de Turing
* Proposto por **Alan Turing em 1950**, também chamado de *"Jogo da Imitação"*.
* **Como funciona:** um avaliador conversa por texto, ao mesmo tempo, com um ser humano e com um computador, sem saber quem é quem. Se não conseguir distinguir qual dos dois é a máquina, o computador **"passa"** no teste.
* ==🟡 O teste mede se o **comportamento** é indistinguível do humano, não se a máquina "pensa" ou "entende". Turing trocou uma pergunta filosófica ("máquinas pensam?") por uma pergunta que dá para testar==
* **Hoje:** LLMs conseguem enganar pessoas em conversas curtas e, mesmo assim, cometem erros que nenhum humano cometeria (como errar a contagem de letras de uma palavra). Por isso o teste é visto como um **marco histórico**, não como uma medida útil. Na prática, modelos são avaliados com **benchmarks** (provas padronizadas de matemática, código, raciocínio) e **evals** (testes criados para a tarefa específica de cada empresa).

### Subcampos da Inteligência Artificial

* **Hierarquia** -> os campos ficam um dentro do outro: **IA ⊃ Machine Learning ⊃ Deep Learning**. A IA Generativa atual é construída quase toda sobre Deep Learning.

| Campo | Ideia central | Exemplo |
|---|---|---|
| **IA** | Qualquer técnica que faz a máquina agir de forma "inteligente" | GPS calculando a melhor rota |
| **Machine Learning** | Aprender padrões a partir de exemplos | Filtro de spam |
| **Deep Learning** | ML com redes neurais de muitas camadas | Reconhecimento facial |
| **IA Generativa** | Modelos que criam conteúdo novo | ChatGPT, Claude, geradores de imagem |

* **Existe IA sem Machine Learning:** sistemas especialistas com regras escritas à mão, algoritmos de busca (como o do GPS) e motores de xadrez clássicos são IA, mas não aprendem com dados.
* Também existiam **modelos generativos antes do Deep Learning** (como as cadeias de Markov, que geravam texto simples prevendo a próxima palavra com base na anterior). Os modelos generativos atuais são muito mais poderosos porque usam Deep Learning.

#### Machine Learning
* **Ideia central:** em vez de programar as regras, você mostra **exemplos** e o algoritmo **descobre os padrões sozinho**.
* **Exemplo:** o modelo analisa 1000 fotos **rotuladas** (*"isto é cachorro" / "isto não é cachorro"*) e aprende os padrões que diferenciam uma da outra. Depois, recebe uma foto nova e usa esses padrões para decidir se há um cachorro nela.
* **Conceitos básicos:**
   * **Dataset** -> o conjunto de exemplos usado para treinar
   * **Features** (características) -> as informações de entrada. Para prever o preço de um imóvel: área, bairro, número de quartos
   * **Rótulo** (*label*) -> a resposta certa de cada exemplo. No caso do imóvel: o preço real de venda
   * **Modelo** -> o resultado do treino: uma "função" que recebe features e devolve uma previsão
* **Tipos de aprendizado:**

| Tipo | Como aprende | Exemplos de uso |
|---|---|---|
| **Supervisionado** | Com exemplos rotulados (entrada -> resposta certa) | Classificar e-mails como spam; prever preço de imóvel; detectar fraude |
| **Não supervisionado** | Sem rótulos; encontra estruturas e grupos sozinho | Agrupar clientes por comportamento de compra; detectar anomalias |
| **Por reforço** | Por tentativa e erro, recebendo recompensas e punições | Robô aprendendo a andar; IA que joga xadrez ou videogame |

* O supervisionado ainda se divide em dois tipos de problema:
   * **Classificação** -> a resposta é uma **categoria** (spam / não spam; cachorro / gato / pássaro)
   * **Regressão** -> a resposta é um **número** (preço do imóvel; temperatura de amanhã)
* LLMs usam os três tipos: o pré-treino é **autossupervisionado** (o próprio texto fornece o rótulo: a próxima palavra), o ajuste de instruções é **supervisionado** e o alinhamento usa **reforço** (RLHF).

* **Treino, validação e teste**
   * Os dados são divididos em três partes: **treino** (o modelo aprende com eles), **validação** (usados para ajustar configurações durante o desenvolvimento) e **teste** (usados só no final, para medir o desempenho real).
   * ==🟡 O modelo nunca pode ser avaliado com os mesmos dados que usou para treinar. Seria como fazer uma prova com as mesmas questões da lista de exercícios: a nota sai alta, mas não prova que ele aprendeu==

* **Overfitting x Underfitting**
   * **Overfitting** (sobreajuste) -> o modelo **decora** os exemplos de treino em vez de aprender o padrão geral. Vai muito bem no treino e mal em dados novos. Como um aluno que decorou as respostas da lista, mas não sabe resolver uma questão diferente.
   * **Underfitting** (subajuste) -> o modelo é simples demais e não consegue aprender nem os exemplos de treino. Como um aluno que não estudou.
   * O objetivo é a **generalização**: ir bem em dados que o modelo nunca viu.

* **Quando usar Machine Learning?**
   * ✅ Quando o padrão é difícil de descrever em regras, mas existem muitos exemplos (reconhecer fraude, classificar imagens)
   * ✅ Quando as regras mudam com o tempo e o sistema precisa se adaptar (novos tipos de spam)
   * ❌ Quando uma regra simples resolve (*"bloquear pagamentos acima de R$ 10.000 sem aprovação"*). Regra é mais barata, previsível e fácil de explicar
   * ❌ Quando não há dados suficientes ou de boa qualidade

#### Deep Learning
* Subcampo do Machine Learning que usa **redes neurais profundas**: redes com muitas camadas de "neurônios" artificiais.
* **Como funciona um neurônio artificial:** recebe números de entrada, multiplica cada um por um **peso**, soma tudo com um **viés** e aplica uma função de ativação. Sozinho é simples; milhões deles conectados em camadas aprendem padrões muito complexos.
* **Por que "profundo":** cada camada transforma a entrada em representações cada vez mais abstratas. Numa imagem, as primeiras camadas detectam **bordas**, as do meio detectam **formas** (olhos, orelhas) e as últimas, **objetos inteiros** (um rosto, um cachorro).
* **Parâmetros** -> os **pesos** e **vieses** da rede (no dia a dia, chamados só de "pesos"). São números organizados em matrizes e ajustados durante o treino. É neles que fica todo o "conhecimento" do modelo. LLMs têm de **bilhões a trilhões** de parâmetros.
* **A saída depende da tarefa:**
   * Classificadores e LLMs produzem **probabilidades** (*"92% de chance de ser cachorro"*; *"qual o próximo token mais provável"*)
   * Modelos de **regressão** devolvem um número direto (*"amanhã fará 28 °C"*)
* **Quando usar Deep Learning x ML clássico:**

| Situação | Melhor escolha | Por quê |
|---|---|---|
| Dados em tabela (planilhas, bancos SQL) | **ML clássico** (árvores de decisão, XGBoost) | Mais rápido, barato e geralmente tão bom ou melhor |
| Imagem, áudio, vídeo, texto livre | **Deep Learning** | Só redes profundas aprendem bem padrões desses dados |
| Poucos dados | **ML clássico** ou modelo pré-treinado | Redes profundas precisam de muitos dados para treinar do zero |
| Linguagem natural (chat, resumo, extração) | **LLM pronto** via API | Treinar do zero é inviável; usar um modelo existente resolve |

#### IA Generativa
* Modelos capazes de **gerar conteúdo novo** a partir de uma instrução: textos, imagens, áudios, vídeos, código.
* **Principais tipos:**
   * **LLMs** (*Large Language Models*) -> geram texto e código. Ex.: ChatGPT, Claude, Gemini, Llama
   * **Modelos de difusão** -> geram imagens e vídeos partindo de "ruído" e refinando aos poucos até formar a imagem
   * **Modelos multimodais** -> entendem e/ou geram vários tipos de dado ao mesmo tempo (texto + imagem + áudio)
* **Exemplos de uso:** chatbots de atendimento, resumo de documentos, geração e revisão de código, extração de dados de contratos, tradução, criação de imagens para marketing.
* ==🟡 IA Generativa não "busca" respostas prontas: ela **gera** a resposta na hora, peça por peça. Isso explica tanto a flexibilidade quanto o risco de inventar coisas (alucinação, Aula 2)==

### Processo de aprendizado

* **FLUXO:** **Data** (dados) -> **Training** (treino) -> **Model** (modelo) -> **Inference** (inferência)
* O modelo **aprende uma vez** (treino: caro e demorado) e depois é **usado milhões de vezes** (inferência: barata por chamada).

#### Training (treinamento)
* O modelo processa uma **quantidade massiva de dados** e ajusta seus **parâmetros** para capturar os padrões desses dados.
* No caso de texto, ele é dividido em **tokens** (pedaços de texto). Cada token vira um número (um ID) e depois um vetor que a rede consegue processar.
* **Como o ajuste acontece** -> um ciclo que se repete bilhões de vezes:
   1. O modelo faz uma **previsão** (ex.: qual a próxima palavra de *"O céu é ___"*)
   2. Uma **função de perda** (*loss*) mede o tamanho do erro (ele disse "verde", o certo era "azul")
   3. O **backpropagation** calcula quanto cada parâmetro contribuiu para esse erro (o **gradiente**)
   4. O **gradiente descendente** ajusta cada parâmetro um pouquinho na direção que reduz o erro
* **Analogia:** imagine descer uma montanha com neblina, sem ver o vale. A cada passo você sente a inclinação do chão sob os pés (o gradiente) e dá um passo pequeno para baixo. Depois de milhões de passos, chega perto do ponto mais baixo (o menor erro).
* ==🟡 É aqui que entra a matemática: **derivadas** (o gradiente), **matrizes** (as camadas) e **probabilidade** (as previsões)==

#### As etapas de treino de um LLM
1. **Pré-treino** (*pre-training*) -> o modelo lê trilhões de tokens da internet, livros e código, aprendendo a prever o próximo token. Sai daqui um "autocompletar" muito poderoso, que sabe muito sobre linguagem e o mundo, mas ainda **não sabe conversar** (se você perguntar algo, ele pode continuar com outra pergunta, em vez de responder).
2. **Ajuste de instruções** (*SFT, Supervised Fine-Tuning*) -> treino com milhares de exemplos de pergunta e resposta ideal. O modelo aprende o **formato de assistente**.
3. **Alinhamento** (*RLHF, DPO e similares*) -> humanos ou outros modelos comparam respostas e indicam a melhor. O modelo aprende a preferir respostas mais **úteis, honestas e seguras**.

* ==🟡 O modelo **NÃO** guarda os dados em um banco de dados. Ele guarda apenas o que aprendeu deles, na forma de parâmetros==
   * **Analogia:** é como uma pessoa que leu milhares de livros. Ela não tem os livros na cabeça, mas aprendeu vocabulário, fatos e jeitos de escrever.
   * **Exceção:** textos que aparecem muitas vezes no treino (licenças de software, trechos muito famosos) podem ser **memorizados** quase palavra por palavra. Por isso existe preocupação com dados privados no treino.

#### Inference (inferência)
* É o **uso** do modelo já treinado: você manda uma entrada e recebe uma saída. Cada mensagem enviada ao ChatGPT ou ao Claude é uma inferência.
* Na inferência, os parâmetros ficam **congelados**: o modelo **não aprende** com a sua conversa.
* ==🟡 Quando um chatbot "lembra" de algo que você disse antes, não é aprendizado. O aplicativo reenvia o histórico da conversa a cada mensagem, dentro do contexto (Aula 2)==
* **Em resumo:** dados são usados para treinar modelos, que, depois de treinados, respondem perguntas (inferência) com base no que aprenderam.

### RAG (Retrieval-Augmented Generation)

* **O problema que o RAG resolve:** um modelo só sabe o que viu no treino. Ele não conhece os documentos da sua empresa, nem fatos posteriores à data de corte do treino.
* **A solução:** antes de o modelo responder, o sistema **busca** (*retrieval*) a informação relevante em uma fonte externa e a **coloca no prompt** (*augmented*). O modelo então **gera** (*generation*) a resposta com base nesse material, priorizando-o em vez da própria memória.
* ==🟡 Você pergunta: "qual a política de reembolso da loja?". O modelo nunca viu esse documento. O sistema busca os trechos da política e os entrega junto com a pergunta. É como fazer uma **prova com consulta**: o aluno (modelo) não muda, só recebe o material de apoio==
* A fonte pode ser qualquer coisa: documentos em um banco vetorial, um banco SQL, uma API, uma busca na web (busca na web também é uma forma de RAG).

* **Passo a passo resumido** (detalhado na Aula 4):
   * **Fase offline** (preparação, feita antes das perguntas):
      1. **Ingestão** -> extrair o texto dos documentos
      2. **Chunking** -> dividir em trechos menores
      3. **Embedding** -> converter cada trecho em um vetor que representa seu significado (Aula 3)
      4. **Indexação** -> guardar vetores, textos e metadados em um **banco vetorial**
   * **Fase online** (a cada pergunta):
      1. **Embedding da pergunta**, com o mesmo modelo usado nos documentos
      2. **Recuperação** -> buscar os *k* trechos mais próximos da pergunta (o **top-k**)
      3. **Reranking** (opcional) -> reordenar os candidatos com um modelo mais preciso
      4. **Geração** -> o LLM responde com base nos trechos e cita as fontes

* **Por que utilizar RAG?**
   * **Informações atualizadas ou privadas**, que não estavam no treino
   * **Menos alucinação**, porque a resposta se ancora em fontes reais (reduz bastante, mas não elimina)
   * **Rastreabilidade** -> dá para mostrar de onde veio cada informação
   * **Custo baixo** -> atualizar a base é muito mais barato que retreinar o modelo
   * **Controle de acesso** -> dá para filtrar os documentos de acordo com quem perguntou

* **Quando usar RAG?**
   * ✅ Chatbot que responde sobre documentos internos (manuais, políticas, contratos)
   * ✅ Suporte ao cliente com base de conhecimento que muda com frequência
   * ✅ Busca inteligente em grandes acervos (jurídico, médico, técnico)
   * ❌ Quando o problema é **comportamento ou formato** da resposta, não falta de informação (aí o caminho é prompt ou fine-tuning)
   * ❌ Quando a base é pequena o bastante para caber inteira no prompt (aí basta colocar tudo no contexto)

* **Limitações**
   * A resposta **depende da recuperação**: se o sistema trouxer trechos errados ou incompletos, a resposta sai ruim. Na prática, a maioria dos problemas de RAG está na busca, não no LLM.
   * O modelo ainda pode interpretar mal um trecho ou misturar com o que "lembra" do treino.
   * Perguntas que exigem **juntar informação espalhada** (*"quantos contratos venceram em 2025?"*) costumam falhar com RAG simples, porque o top-k traz só alguns trechos. Esses casos pedem consultas SQL, agentes ou outras técnicas.

### Fine-Tuning (Ajuste Fino)

* **O que é?** É **continuar o treinamento** de um modelo já pronto com um **conjunto pequeno e específico** de exemplos (geralmente pares de *entrada -> resposta ideal*). O resultado é uma **nova versão do modelo**, com a mesma arquitetura e os valores dos parâmetros ajustados.
* ==🟡 Fine-tuning muda o **VALOR** dos parâmetros. É como afinar um violão: as cordas continuam sendo seis, o que muda é a tensão de cada uma==
* **Exemplo:** uma empresa quer que o modelo classifique tickets de suporte em 12 categorias internas, sempre devolvendo um JSON no mesmo formato. Ela junta 2.000 tickets já classificados e faz fine-tuning. O modelo passa a fazer isso com mais precisão e consistência do que só com instruções no prompt.

* **Para que serve?**
   * Ajustar **comportamento**: tom de voz, formato de resposta, estilo de escrita
   * **Especializar** em uma tarefa: classificar tickets, extrair campos de notas fiscais, escrever em linguagem jurídica
   * **Eficiência** -> um modelo pequeno ajustado pode igualar um modelo grande numa tarefa específica, sendo mais barato e mais rápido

* **Tipos**
   * **Fine-tuning completo** -> atualiza todos os parâmetros. A quantidade de parâmetros continua a mesma. Caro e exige muita memória de GPU.
   * **LoRA** (*Low-Rank Adaptation*) -> congela o modelo original e treina pequenas matrizes acopladas às camadas existentes (o **adapter**), normalmente menos de 1% do tamanho do modelo. Depois do treino, o adapter pode ficar separado ou ser **mesclado** aos pesos originais. É o mais usado hoje.
   * **QLoRA** -> o mesmo que o LoRA, mas com o modelo base comprimido (**quantizado**), cabendo em GPUs menores.
   * ==🟡 Com LoRA dá para ter **um** modelo base e vários adapters pequenos (um por cliente ou por tarefa), trocando em tempo de execução==

* **Quando usar fine-tuning?**
   * ✅ O modelo precisa seguir um **formato ou estilo** muito específico e o prompt não está sendo suficiente
   * ✅ Tarefa repetitiva em **alto volume**, em que um modelo menor ajustado reduz custo e latência
   * ✅ Você tem **centenas a milhares de exemplos** de boa qualidade
   * ❌ Para ensinar **fatos novos** ou dados que mudam (use RAG)
   * ❌ Antes de tentar um bom prompt (muitas vezes o prompt resolve)

* **Limitações**
   * Precisa de **dados de boa qualidade**. Dado ruim gera modelo ruim.
   * **Overfitting** -> o modelo decora os exemplos em vez de generalizar
   * **Esquecimento catastrófico** -> ajustar demais numa tarefa pode piorar o modelo em outras que ele fazia bem
   * É **ruim para ensinar conhecimento novo**: o modelo pode memorizar mal, misturar informações ou inventar detalhes

### Retreinamento (Pré-treino)

* Treinar o modelo com um **volume massivo de dados**, do zero (**pré-treino**) ou continuando um pré-treino existente (**pré-treino continuado**), para que ele ganhe conhecimento e capacidades gerais novas. É o que as empresas de IA fazem para lançar uma **nova geração** de modelo.
* **Extremamente custoso** (milhões de dólares em GPUs) e **demorado** (semanas ou meses).
* ==🟡 Fine-tuning e pré-treino usam o **MESMO mecanismo** (ajustar parâmetros com gradiente descendente). O que muda é a **escala**, os **dados** e o **objetivo**==
   * **Pré-treino** -> texto bruto, para prever o próximo token
   * **Fine-tuning** -> exemplos curados de entrada e saída
   * **Alinhamento** -> preferências entre respostas
* Em artigos e vagas, os termos usados são *pre-training*, *continued pre-training* e *post-training* (fine-tuning + alinhamento).
* **Quando usar?** Quase nunca, fora das grandes empresas de IA. O caso mais comum é o **pré-treino continuado** em domínios muito específicos com enorme volume de dados próprios (ex.: um modelo para um idioma pouco representado ou para textos médicos).

### Comparação

| | Dados | Muda o modelo? | Custo | Objetivo | Exemplo |
|---|---|---|---|---|---|
| **Prompt engineering** | Instruções e exemplos no prompt | Não | Muito baixo | Guiar a resposta | *"Responda em tópicos, em tom formal"* |
| **RAG** | Base externa, consultada na hora | Não | Baixo | Dar informação | Chatbot sobre o manual da empresa |
| **Fine-tuning** | Centenas a milhares de exemplos | Sim | Médio/baixo | Ajustar comportamento | Classificador de tickets em JSON |
| **Pré-treino** | Trilhões de tokens | Sim (cria o modelo) | Altíssimo | Conhecimento e capacidades gerais | Lançamento de um novo LLM |

* ==🟡 **Regra prática:** RAG ensina ao modelo **O QUE** saber. Fine-tuning ensina **COMO** se comportar. Muitas aplicações usam os dois juntos==
* **Ordem que um engenheiro segue:**
   1. **Prompt engineering** -> sempre o primeiro passo. É rápido, barato e resolve muito.
   2. **Falta informação?** -> **RAG**
   3. **O problema é formato, estilo ou custo em escala?** -> **Fine-tuning**
   4. Pular direto para fine-tuning é um erro comum e caro.

### INTRODUÇÃO: Resumo
-> IA é um campo amplo; **IA ⊃ ML ⊃ Deep Learning**, e a IA Generativa atual é construída sobre Deep Learning
-> Machine Learning aprende padrões a partir de exemplos (supervisionado, não supervisionado, por reforço); o objetivo é **generalizar** sem cair em overfitting
-> Para dados em tabela, ML clássico costuma bastar; para texto, imagem e áudio, Deep Learning
-> LLM (*Large Language Model*) é um modelo de linguagem com bilhões de parâmetros, treinado para prever o próximo token
-> **Training** ajusta os parâmetros (caro, uma vez); **Inference** é o uso do modelo congelado (barato, sempre)
-> **RAG** busca dados externos e os coloca no contexto; **Fine-tuning** ajusta o comportamento; **Pré-treino** cria o conhecimento geral
-> Ordem de tentativa: **prompt -> RAG -> fine-tuning**



## AULA 2: Tokens, Contexto e Geração

### O que é um Token?

* **Token** é a unidade de texto que o modelo processa. Pode ser uma palavra inteira, um pedaço de palavra, um sinal de pontuação ou um espaço.
* O modelo **não lê letras nem palavras**: ele lê tokens. Quando recebe um texto, um componente chamado **tokenizador** quebra esse texto em tokens.
* **Exemplo ilustrativo** (a divisão exata varia de um modelo para outro):
   * *"Inteligência artificial é incrível"* -> `Intel` `igência` ` artificial` ` é` ` incr` `ível`
   * Palavras comuns costumam virar um token só; palavras raras ou longas são quebradas em pedaços.
* **O caminho completo:** **texto -> tokens -> IDs numéricos -> vetores (embeddings internos)**
   * Cada token tem um **ID** (um número) no **vocabulário** do modelo, que tem dezenas a centenas de milhares de tokens possíveis.
   * Cada ID é convertido em um vetor, que é o que a rede neural realmente processa.
* **Por que isso importa na prática:**
   * **Custo** -> APIs de LLM cobram **por token** (de entrada e de saída)
   * **Limite** -> o tamanho máximo de uma conversa é medido em tokens
   * **Idioma** -> em inglês, um token tem em média uns 4 caracteres. **Português costuma gastar mais tokens** para o mesmo conteúdo, porque os tokenizadores foram treinados com mais inglês
* ==🟡 Por enxergar tokens e não letras, LLMs tropeçam em tarefas como contar letras de uma palavra ("quantos R tem em 'carro'?") ou inverter uma string==

### Context Window (Janela de Contexto)

* É a **quantidade máxima de tokens** que o modelo consegue considerar **em uma única chamada**. Inclui tudo:
   * Instruções do sistema (*system prompt*)
   * Histórico da conversa
   * Documentos anexados ou recuperados (RAG)
   * A pergunta atual
   * **A resposta que está sendo gerada**
* **Analogia:** é a **mesa de trabalho** do modelo. Tudo o que ele vai usar para responder precisa estar em cima da mesa. Se não couber, algo precisa sair.
* Os modelos atuais têm janelas que vão de **dezenas de milhares** a **mais de um milhão** de tokens, dependendo do modelo.
* **Sem estado** (*stateless*): cada chamada à API é independente. O modelo não lembra da chamada anterior. Quem guarda a conversa é a **aplicação**, que reenvia o histórico inteiro a cada mensagem.
   * **Consequência:** conversas longas ficam cada vez **mais caras** (o histórico é cobrado de novo a cada mensagem) e, no limite, precisam ser **resumidas ou cortadas**.
* ==🟡 Caber no contexto não garante que o modelo use bem. Informação no meio de contextos muito longos tende a ser menos aproveitada (efeito *lost in the middle*). Mais contexto nem sempre é melhor: o ideal é colocar **o que é relevante**==

### Prompt

* São as **instruções, o contexto, os exemplos e a pergunta** fornecidos ao modelo.
* Em APIs, o prompt é organizado em **papéis** (*roles*):
   * **System** -> regras gerais e o papel do assistente. Vale para a conversa toda
   * **User** -> as mensagens do usuário
   * **Assistant** -> as respostas anteriores do modelo
* **Exemplo:**

```text
System: Você é um assistente de suporte da Loja X. Responda em português,
        de forma curta e educada. Se não souber, diga que vai encaminhar
        para um atendente.
User:   Meu pedido não chegou, o que eu faço?
```

* **Boas práticas de prompt:**
   * Ser **claro e específico** sobre a tarefa e o formato da resposta
   * Dar **contexto** (quem é o usuário, para que serve a resposta)
   * Mostrar **exemplos** do resultado esperado (*few-shot*)
   * Dizer o que fazer quando **não souber** a resposta

### Temperature (Temperatura)

* Controla o quanto a escolha do próximo token é **previsível** ou **variada**.
* **Como funciona:**
   1. A cada passo, o modelo calcula uma pontuação (**logit**) para cada token do vocabulário
   2. A função **softmax** transforma essas pontuações em probabilidades que somam 100%
   3. A temperatura *T* **divide** as pontuações antes do softmax

$$P(\text{token}_i) = \frac{e^{z_i / T}}{\sum_j e^{z_j / T}}$$

* **Exemplo numérico** -> lacuna: *"Meu animal favorito é o ___"*, com logits: cachorro = 2, gato = 1, cavalo = 0

| Temperatura | cachorro | gato | cavalo | Efeito |
|---|---|---|---|---|
| **T = 0,5** | 86,7% | 11,7% | 1,6% | Concentra no favorito |
| **T = 1,0** | 66,5% | 24,5% | 9,0% | Distribuição original |
| **T = 2,0** | 50,6% | 30,7% | 18,6% | Achata: todos ganham chance |

* **Quando usar cada temperatura:**

| Temperatura | Comportamento | Use para |
|---|---|---|
| **Baixa (0 a 0,3)** | Previsível, repete as escolhas mais prováveis | Extração de dados, classificação, código, respostas factuais, RAG |
| **Média (0,5 a 0,8)** | Equilíbrio entre consistência e naturalidade | Chatbots, resumos, e-mails |
| **Alta (acima de 1)** | Criativa, variada, com mais risco de sair do trilho | Brainstorm, nomes de produto, escrita criativa |

* Mesmo com temperatura 0, as saídas podem variar um pouco entre chamadas, por detalhes numéricos e de infraestrutura.
* ==🟡 Temperatura muda a **variabilidade**, não a **inteligência**. Temperatura baixa não deixa o modelo mais esperto, só mais previsível==
* **Outros controles de geração:**
   * **Top-p** (*nucleus sampling*) -> só sorteia entre os tokens que, somados, chegam a p% da probabilidade (ex.: top-p = 0,9 ignora a "cauda" de tokens improváveis)
   * **Top-k** -> só sorteia entre os k tokens mais prováveis
   * **Max tokens** -> limite de tamanho da resposta
   * **Stop sequences** -> textos que fazem a geração parar quando aparecem

### Do Input à Response

* **Usuário faz uma pergunta -> Mensagem é quebrada em *tokens* -> Modelo considera instruções + histórico -> Gera uma sequência de *tokens* a partir de probabilidades -> Formula a resposta**
* Em resumo: **TEXTO -> TOKEN -> CONTEXTO -> GERAÇÃO -> RESPOSTA**

#### Geração autoregressiva
* O modelo **não gera a resposta inteira de uma vez**. Ele gera **um token por vez**:
   1. Lê todo o contexto e calcula as probabilidades do próximo token
   2. Escolhe um token (de acordo com a temperatura)
   3. **Anexa esse token ao contexto**
   4. Repete até gerar um **token de fim** ou atingir o limite de tamanho
* **Exemplo:** pergunta *"Qual é a capital do Brasil?"*

| Passo | Contexto que o modelo lê | Token gerado |
|---|---|---|
| 1 | Qual é a capital do Brasil? | A |
| 2 | Qual é a capital do Brasil? A | capital |
| 3 | Qual é a capital do Brasil? A capital | é |
| 4 | Qual é a capital do Brasil? A capital é | Brasília |
| 5 | Qual é a capital do Brasil? A capital é Brasília | . |
| 6 | Qual é a capital do Brasil? A capital é Brasília. | [fim] |

* A cada passo, o modelo relê **tudo**: a pergunta e o que ele próprio já escreveu. No passo 4, para chegar em "Brasília", ele conecta "capital" (que acabou de escrever) com "Brasil" (lá na pergunta). Essa conexão entre tokens é feita pelo mecanismo de **atenção** dos Transformers.
* ==🟡 É por isso que as respostas aparecem "digitando" na tela (*streaming*), e por isso que um erro no começo da resposta tende a contaminar o resto: o modelo continua a partir do que já escreveu==
* **Consequência prática:** pedir para o modelo **raciocinar antes de responder** (*"pense passo a passo"*) costuma melhorar respostas complexas, porque o raciocínio escrito vira contexto para os tokens seguintes.


## AULA 2: Training x Context

* Existem **duas formas** de um modelo "saber" algo: o que ele aprendeu no **treino** (está nos parâmetros) e o que está no **contexto** daquela chamada (está no prompt).

| | Training | Context |
|---|---|---|
| **O que muda** | Os valores dos parâmetros do modelo | Nada no modelo; só a entrada daquela chamada |
| **Duração** | Permanente | Some ao fim da chamada |
| **Custo** | Alto e demorado, feito poucas vezes | Pago por token, a cada chamada |
| **Quando acontece** | Antes de o modelo ser usado | Durante a inferência |
| **O que entra** | Conhecimento geral e comportamento (*behavior*) | Histórico da conversa, anexos, documentos, buscas na web, resultados de ferramentas |
| **Exemplos** | Pré-treino, fine-tuning | Conversa no chat, RAG, anexar um PDF |
| **Analogia** | O que a pessoa estudou ao longo da vida | O papel que ela tem na mão agora |

* **RAG trabalha no contexto**: soma informações por meio de documentos e buscas, sem mexer no modelo.
* ==🟡 Quando o modelo precisa saber algo **específico, recente ou privado**, a solução quase sempre é colocar isso no **contexto**, não treinar o modelo==

### Hallucination (Alucinação)

* **Alucinação** é quando o modelo gera algo **fluente, convincente e plausível, mas falso** ou sem base nas fontes.
* **Exemplos:**
   * Citar um artigo científico com autor, ano e título que **não existem**
   * Sugerir uma função de biblioteca que **nunca existiu**
   * Afirmar com confiança uma data, um número ou uma lei **errados**
* ==🟡 O perigo da alucinação está justamente em **parecer certa**. Não é uma resposta sem nexo; é uma resposta que soa correta==
* **Por que acontece?** O modelo foi treinado para gerar o texto **mais provável**, não o texto **verdadeiro**. Quando não sabe algo, ele não tem um mecanismo nativo de "não sei" e completa com o que soa certo. Por isso modelos alucinam **até com temperatura 0**.
* **Fatores que aumentam o risco:**
   * -> **Falta de contexto** ou pergunta sobre algo que o modelo nunca viu (dados privados, eventos recentes, assuntos de nicho)
   * -> **Conhecimento desatualizado** (o modelo pode dar uma resposta que *era* verdadeira)
   * -> **Perguntas com premissa falsa** (*"por que Einstein ganhou dois Nobel?"*): o modelo tende a seguir a premissa em vez de corrigi-la
   * -> **Pedidos de detalhes muito específicos**: números, citações, URLs, referências bibliográficas
   * -> **Temperatura alta**, que aumenta a variação e a chance de sair do trilho

### Grounding (Ancoragem)

* **Grounding** é **ancorar** a resposta em **fontes verificáveis**, em vez de depender só da memória do modelo.
* Serve para fazer o modelo devolver respostas **corretas, atuais e rastreáveis**.
* **Técnicas:**
   * **RAG** -> buscar documentos relevantes e colocá-los no contexto
   * **Ferramentas e APIs** (*tool use*) -> deixar o modelo consultar um banco de dados, uma API de cotação, uma busca na web
   * **Instruções explícitas** -> *"responda apenas com base nos documentos; se a resposta não estiver neles, diga que não sabe"*
   * **Citações obrigatórias** -> exigir que cada afirmação aponte o trecho de origem, o que facilita verificar
   * **Validação** -> checar a saída com código (o JSON é válido? o ID existe no banco?) ou com um segundo modelo avaliador
* **Exemplo:** um assistente de vendas precisa informar o estoque de um produto. Sem grounding, ele "chuta" um número plausível. Com grounding, ele chama a API de estoque e responde com o valor real.

==🟡 **LLMs não são bancos de dados:** para fatos atuais e informações críticas, conecte os modelos a **Sources of Truth** (fontes da verdade) para garantir contextualização atual e integridade das respostas==

### AULA 2: Resumo
- **Tokens** são pedaços de texto, as unidades que o modelo processa; definem custo e limite
- **Context Window** é o limite de tokens por chamada, incluindo a resposta; o modelo não tem memória entre chamadas
- **Prompt** organiza instruções (system), mensagens do usuário e respostas anteriores
- **Temperatura** muda a variabilidade das respostas, não a inteligência; baixa para tarefas factuais, alta para criativas
- A geração é **autoregressiva**: um token por vez, cada um virando contexto para o próximo
- **Training** muda o modelo; **Context** só muda a entrada daquela chamada
- **Hallucination** é uma resposta plausível e falsa; combate-se com **Grounding** e validação



## AULA 3: Como a IA entende o significado das palavras + Embeddings

### Linguagem e Busca semântica

* Para um computador, texto é só uma sequência de caracteres. Ele sabe que "carro" e "carro" são iguais, mas não sabe que "carro" e "automóvel" significam a mesma coisa.
* Para buscar por **significado**, é preciso transformar o texto em algo que permita **medir o quanto duas coisas são parecidas**. Essa é a função dos **embeddings**: transformar significado em números.

### Busca por palavra x Busca por significado

#### Keyword Search (busca por palavra-chave)
* Encontra documentos que contêm **as mesmas palavras** da pergunta.
* Algoritmo clássico: **BM25**, que dá mais pontos quando:
   * O termo aparece **várias vezes** no documento
   * O termo é **raro** na coleção (aparecer "reembolso" vale mais que aparecer "de")
* **Força:** excelente para termos exatos, como códigos de produto, nomes próprios, números de erro, siglas e números de lei.
* **Fraqueza:** não entende sinônimos nem paráfrases. *"Como cancelar minha assinatura"* não encontra um documento que diz *"encerramento do plano"*.

#### Semantic Search (busca semântica)
* Encontra documentos com **significado parecido**, mesmo sem nenhuma palavra em comum. Funciona comparando **embeddings**.
* **Força:** entende sinônimos, paráfrases, erros de digitação e até outros idiomas (*"refund policy"* encontra *"política de reembolso"*).
* **Fraqueza:** pode falhar em termos exatos. Para ela, os códigos "ERR-4012" e "ERR-4021" parecem quase iguais.

#### Busca híbrida
* **Combina as duas**: roda a busca por palavra-chave e a semântica, depois une os dois rankings (uma técnica comum é a **RRF**, *Reciprocal Rank Fusion*).
* É o **padrão em produção**, porque fica com o melhor dos dois mundos.

#### Quando usar cada uma

| Tipo de busca | Use quando | Exemplo de pergunta |
|---|---|---|
| **Keyword** | Termos exatos importam | *"erro ERR-4012"*, *"artigo 157 do Código Penal"*, *"SKU 88213"* |
| **Semântica** | As pessoas descrevem o problema com as próprias palavras | *"meu pedido chegou quebrado, o que faço?"* |
| **Híbrida** | Sistemas reais, que recebem os dois tipos de pergunta | Chatbot de suporte, busca em documentação técnica |

### Embedding

* **Embedding** é um **vetor de números** que representa o significado de um texto (ou de uma imagem, ou de um áudio).
* É gerado por um **modelo de embedding**, treinado para que textos com significado parecido virem vetores **próximos** no espaço.
* **Analogia:** imagine um mapa em que cada frase é um ponto. Frases sobre "reembolso" ficam num bairro, frases sobre "entrega" em outro, frases sobre "vagas de emprego" bem longe dos dois. As coordenadas de cada ponto são o embedding.
* **Exemplo simplificado** (com 3 dimensões, só para ilustrar):
   * *"Gato dormindo no sofá"* -> `[0.80, 0.10, 0.30]`
   * *"Felino descansando no móvel"* -> `[0.79, 0.12, 0.31]` (muito perto)
   * *"Taxa de juros subiu"* -> `[0.05, 0.90, 0.20]` (longe)
* Na prática, embeddings têm **centenas ou milhares de dimensões** (384, 768, 1536 e 3072 são tamanhos comuns). Cada dimensão isolada não tem um significado legível por humanos; o significado está na **posição do vetor como um todo**.
* ==🟡 O **modelo de embedding é diferente do LLM** que gera a resposta. No RAG são dois modelos: um pequeno e barato para gerar vetores, outro grande para escrever a resposta==
* ==🟡 Documentos e perguntas precisam ser convertidos pelo **mesmo** modelo de embedding. Vetores de modelos diferentes vivem em "espaços" diferentes e não podem ser comparados. Trocou o modelo? Precisa gerar todos os vetores de novo==

#### Para que mais servem embeddings (além de RAG)
* **Busca semântica** -> encontrar documentos, produtos ou perguntas parecidas
* **Recomendação** -> *"quem leu este artigo também pode gostar de…"* (artigos com vetores próximos)
* **Classificação** -> treinar um classificador simples em cima dos vetores (ex.: separar tickets por assunto)
* **Agrupamento** (*clustering*) -> descobrir temas em milhares de avaliações de clientes
* **Deduplicação** -> encontrar perguntas repetidas escritas de formas diferentes
* **Detecção de anomalias** -> encontrar textos que não se parecem com nada do resto

#### Como escolher um modelo de embedding
* **Idioma** -> para textos em português, use um modelo **multilíngue** ou treinado com português
* **Qualidade x custo** -> modelos maiores geram vetores melhores, mas custam mais e ocupam mais espaço
* **Dimensões** -> mais dimensões = mais detalhe, mas mais armazenamento e busca mais lenta
* **Onde roda** -> via API (simples, paga por uso) ou modelo aberto rodando no seu servidor (mais controle, dados não saem da empresa)
* Rankings públicos como o **MTEB** comparam modelos de embedding em várias tarefas e idiomas

### Similaridade semântica

* **Fluxo:** Texto -> Embedding -> Comparação -> Resultado
* Em resumo: **TEXTO -> VETOR -> SIMILARIDADE -> BUSCA**
* A medida mais usada é a **similaridade de cosseno**, que mede o **ângulo** entre dois vetores (se apontam para a mesma direção):

$$\cos(\theta) = \frac{\mathbf{a} \cdot \mathbf{b}}{\lVert \mathbf{a} \rVert \, \lVert \mathbf{b} \rVert}$$

- **a · b** (produto escalar) -> multiplica posição por posição e soma tudo
- **‖a‖** (norma) -> o tamanho do vetor: raiz quadrada da soma dos quadrados
- **Resultado:**
	- Perto de **1** -> mesma direção, significado muito parecido
	- Perto de **0** -> sem relação
	- **Negativo** -> direções opostas (raro na prática com embeddings de texto)

* **Exemplo calculado:**
   * a = `[1, 2, 3]`, b = `[2, 4, 6]` -> a · b = 2 + 8 + 18 = 28; ‖a‖ = √14 ≈ 3,74; ‖b‖ = √56 ≈ 7,48 -> cos = 28 / 28 = **1** (mesma direção; b é só a "esticado")
   * a = `[1, 2, 3]`, c = `[3, -1, 0]` -> a · c = 3 − 2 + 0 = 1; ‖c‖ = √10 ≈ 3,16 -> cos = 1 / (3,74 × 3,16) ≈ **0,08** (quase sem relação)
* **Outras medidas:**
   * **Produto escalar** -> igual ao cosseno quando os vetores estão **normalizados** (tamanho 1), o que é comum. Mais rápido de calcular
   * **Distância euclidiana** -> distância em linha reta entre os pontos; **menor = mais parecido**
* ==🟡 "Próximo" significa "aparece em contextos parecidos", não "significa a mesma coisa". "Quente" e "frio" podem ficar próximos, porque aparecem nas mesmas frases sobre temperatura. **Similaridade não é o mesmo que relevância**==
* **Busca em escala:** comparar a pergunta com milhões de vetores um a um seria lento. Bancos vetoriais usam índices de **busca aproximada** (*ANN, Approximate Nearest Neighbors*, como o **HNSW**), que acham os vizinhos mais próximos em milissegundos, trocando um pouco de precisão por muita velocidade.

- ##### ==🟡 Embedding não responde -> **Ajuda a encontrar a resposta**==

### Proximidade entre vetores e o que entra no contexto

A pergunta vira um vetor, o sistema mede a distância até cada trecho da base e **só os k mais próximos** são colocados no prompt. O LLM nunca vê os outros.

![[rag-proximidade-vetores.png]]

*Exemplo ilustrativo em 2 dimensões: 8 trechos de uma base de atendimento, 1 pergunta, k = 3. O #4 ("Trocas de produto com defeito") é relacionado ao tema, mas ficou abaixo do corte e não chega ao modelo.*

- **A proximidade decide quem entra**
	- A recuperação não é um sorteio: ela calcula a similaridade, **ordena** os trechos e aplica um **corte**. Os *k* primeiros (ou todos acima de um limiar de similaridade) entram no prompt; o resto fica de fora. O #3 e o #4 podem ter notas parecidas, e mesmo assim um entra e o outro não.
	- **Escolha do k:** k pequeno pode deixar de fora a informação necessária; k grande traz ruído, custa mais tokens e pode confundir o modelo. Um padrão comum é buscar uns 20 a 50 candidatos e usar um **reranker** para reduzir aos 3 a 10 melhores.
	- **Mais próximo não é o mesmo que correto:** um trecho pode ser o vizinho mais próximo e ainda assim não responder à pergunta, ou estar desatualizado.
- **Onde a probabilidade entra**
	1. **Busca aproximada (ANN)** -> em bases grandes, o índice pode, raramente, deixar escapar um vizinho que deveria estar no top-k
	2. **Na geração** -> depois que os trechos estão no contexto, o LLM gera a resposta token a token, por probabilidades. Ele tende a se apoiar mais nos trechos que respondem melhor à pergunta, por meio do mecanismo de **atenção**
	3. **Posição no prompt** -> trechos no início e no fim de um contexto longo costumam ser mais aproveitados que os do meio

==🟡 A proximidade decide **SE** o trecho chega ao modelo; o modelo decide **QUANTO** ele pesa na resposta==

### Embedding x Previsão da próxima palavra

* São dois mecanismos diferentes, que costumam ser confundidos:

| | Embedding (similaridade) | Próxima palavra (geração) |
|---|---|---|
| **Pergunta que responde** | "Que textos têm significado parecido com este?" | "Dado tudo que já foi escrito, o que vem agora?" |
| **Como decide** | Distância ou ângulo entre dois vetores | O LLM processa o contexto inteiro e calcula uma probabilidade para cada token do vocabulário |
| **Onde é usado** | Busca semântica, RAG | Geração de texto |

* **Exemplo:** em *"O gato subiu no ___"*, as palavras mais próximas de "gato" no espaço vetorial são "felino", "cachorro" e "gatinho". Mas a próxima palavra provável é "telhado" ou "muro". Palavras próximas **podem substituir** umas às outras; não necessariamente **vêm uma depois da outra**.
* **O que acontece dentro do LLM:** no último passo, o modelo produz um vetor que representa **"o que cabe na lacuna"**, calculado a partir do **contexto inteiro**. Esse vetor é comparado com o vetor de cada token do vocabulário, e os mais alinhados ganham mais probabilidade. Ou seja, existe uma comparação de proximidade, mas entre o **vetor da lacuna** e cada token possível, não entre a palavra anterior e a próxima.
* ==🟡 Embedding mede **semelhança de significado**; quem prevê a próxima palavra é o **modelo inteiro lendo o contexto**==

### AULA 3: Resumo
- **Embedding** representa significado como um vetor de números; vetores próximos tendem a ter significado próximo
- **Keyword Search** acha termos exatos; **Semantic Search** acha significados parecidos; em produção, use **busca híbrida**
- **Similaridade de cosseno** mede o ângulo entre vetores: perto de 1 = parecido, perto de 0 = sem relação
- O **modelo de embedding** é diferente do LLM, e o mesmo modelo deve ser usado para documentos e perguntas
- A recuperação é um **ranking com corte** (top-k): os mais próximos entram no contexto, o resto fica de fora
- Embeddings servem também para recomendação, classificação, agrupamento e deduplicação
- Embedding **ajuda a encontrar** a resposta; quem **gera** a resposta é o LLM



## AULA 4: RAG do zero -> Vector Database, Chunking, Retrieval, Top K e Reranking

### Visão geral

Um sistema RAG tem **duas fases** que acontecem em momentos diferentes:

| Fase | Quando acontece | O que faz | Analogia |
|---|---|---|---|
| **Indexing** (indexação) | Antes das perguntas; repete quando os documentos mudam | Prepara os documentos para serem buscados | Organizar e etiquetar os livros de uma biblioteca |
| **Retrieval + Generation** (recuperação + geração) | A cada pergunta do usuário | Busca os trechos certos e gera a resposta | Ir à estante certa, pegar as páginas certas e responder |

==🟡 A qualidade da fase de **indexing** limita tudo o que vem depois. Se a informação foi mal extraída ou mal dividida, nenhum LLM consegue compensar==

#### Quando vale a pena montar um RAG?
* ✅ A base de conhecimento é **grande demais** para caber no prompt (centenas de documentos, milhares de páginas)
* ✅ Os documentos **mudam com frequência** e a resposta precisa estar sempre atualizada
* ✅ É preciso **citar a fonte** ou **controlar quem vê o quê**
* ❌ A base é **pequena** (alguns documentos curtos): é mais simples colocar tudo direto no contexto, sem banco vetorial
* ❌ A pergunta exige **cálculos ou agregações** sobre dados estruturados (*"qual o faturamento total de março?"*): o caminho é consultar o banco SQL, não buscar trechos de texto

### Indexing: preparando os dados

- **Fluxo:** Source -> Text -> Chunks -> Embeddings -> Index
- Em português: **Fonte -> Extração -> Divisão -> Vetorização -> Armazenamento**

#### 1. Fonte (*Source*)
De onde vêm os dados que vão alimentar o contexto da IA: PDFs, sites, CMS, bancos de dados, documentos internos, tickets de suporte, wikis (Notion, Confluence).
- A escolha da fonte já define a qualidade das respostas: documento **desatualizado, duplicado ou contraditório** na fonte vira resposta errada no final.
- Cada fonte precisa de uma rotina de **atualização** (quando um documento muda, os trechos dele precisam ser reindexados).

#### 2. Extract (extração)
Transformar o arquivo em **texto utilizável**, descartando o que não é conteúdo: menus, cabeçalhos e rodapés repetidos, números de página, propagandas.
- É uma etapa mais difícil do que parece:
	- **Tabelas** viram texto bagunçado se extraídas de qualquer jeito
	- **PDFs escaneados** são imagens e precisam de **OCR** (reconhecimento de texto em imagem)
	- **Layouts em colunas** podem embaralhar a ordem das frases
- Junto com o texto, extraem-se os **metadados**: nome do arquivo, página, seção, data, autor, idioma.

#### 3. Chunk (divisão em trechos)
Dividir o texto em **partes coerentes**, cada uma tratando de uma ideia.
- **Por que dividir?**
	- Um único vetor para um documento inteiro mistura muitos assuntos e fica genérico. Um vetor por trecho representa **uma ideia clara** e é encontrado com mais precisão.
	- Na hora de responder, só os trechos relevantes vão para o prompt, economizando contexto e tokens.
- **O equilíbrio do tamanho:**
	- Chunk **grande demais** -> mistura assuntos, o significado fica diluído e a busca perde precisão
	- Chunk **pequeno demais** -> perde contexto (*"o prazo é de 7 dias"*, mas prazo de quê?)
- **Estratégias comuns:**
	- **Tamanho fixo** -> cortar a cada N tokens (ex.: 300 a 800). Simples, mas pode cortar uma ideia no meio
	- **Sobreposição (*overlap*)** -> cada chunk repete um pedaço do anterior (ex.: 10% a 20%), para que nenhuma informação fique "partida" entre dois trechos
	- **Por estrutura** -> respeitar títulos, seções, parágrafos e listas do documento. Geralmente dá os melhores resultados
	- **Semântico** -> cortar onde o assunto muda, medindo a similaridade entre frases vizinhas
- **Exemplo** -> trecho de uma política de reembolso:
	- ❌ **Corte ruim:** Chunk A termina em *"…o prazo para solicitar o reembolso é de"* e o Chunk B começa com *"7 dias corridos após o recebimento."* Nenhum dos dois, sozinho, responde *"qual o prazo de reembolso?"*
	- ✅ **Com overlap ou divisão por seção:** um único chunk contém *"Prazo de reembolso: o prazo para solicitar o reembolso é de 7 dias corridos após o recebimento."* A busca encontra, e o LLM responde.
	- ✅ **Dica:** incluir o **título da seção** no começo de cada chunk (*"Política de Reembolso > Prazos: …"*) ajuda tanto a busca quanto o LLM a entender do que o trecho fala.
- ==🟡 Não existe tamanho ideal universal. O certo é testar com perguntas reais e medir qual configuração recupera melhor==

#### 4. Embed (vetorização)
Passar cada chunk pelo **modelo de embedding**, que devolve um vetor representando o significado do trecho. É aqui que o texto vira um ponto no espaço vetorial (Aula 3).
- ==🟡 O **mesmo** modelo de embedding deve ser usado nos documentos e nas perguntas. Trocou o modelo? Todos os vetores precisam ser gerados de novo==

#### 5. Store (armazenamento)
Salvar cada chunk em um **Vector Database** (banco vetorial). Cada registro guarda três coisas:

| Campo | Exemplo | Para que serve |
|---|---|---|
| **Vetor** | `[0.021, -0.338, 0.174, …]` | Encontrar o trecho por similaridade |
| **Texto** | "Reembolsos podem ser solicitados em até 7 dias…" | É o que vai de fato para o prompt |
| **Metadata** | `{fonte: "politica.pdf", pagina: 2, loja: "BR", versao: "2026"}` | Filtrar a busca e citar a origem |

#### Vector Database
- Banco de dados especializado em guardar vetores e encontrar rapidamente os **mais próximos** de um vetor de consulta.
- Comparar a pergunta com milhões de vetores um por um seria lento. Por isso esses bancos criam **índices de busca aproximada** (*ANN*, como o **HNSW**), que respondem em milissegundos trocando um mínimo de precisão por muita velocidade.
- Também permitem **filtrar por metadata** durante a busca (ex.: só trechos da loja BR, em português, versão 2026).
- Exemplos: **pgvector** (extensão do PostgreSQL, ótima para quem já usa Postgres), **Qdrant**, **Weaviate**, **Chroma**, **Pinecone**, **Milvus**.

#### Indexing em código (pseudocódigo Python)

```python
for arquivo in fontes:                                        # Fonte
    texto, meta = extrair(arquivo)                            # Extract
    chunks = dividir(texto, tamanho=500, sobreposicao=50)     # Chunk
    for chunk in chunks:
        vetor = modelo_embedding.encode(chunk)                # Embed
        banco.inserir(vetor=vetor, texto=chunk, meta=meta)    # Store
```

### Retrieval + Generation: respondendo uma pergunta

- **Fluxo:** Query -> Vector -> Retrieval -> Grounding -> Answer
- Em português: **Pergunta -> Vetor -> Busca -> Contexto ancorado -> Resposta**

1. **Input / Ask** -> o usuário faz uma pergunta: *"Em quanto tempo posso pedir reembolso?"*
2. **Embed** -> a pergunta vira um vetor, com o mesmo modelo de embedding da indexação
3. **Search** -> o banco vetorial retorna os **Top K** chunks mais próximos da pergunta (aplicando filtros de metadata, se houver)
4. **Rerank** (opcional, muito recomendado) -> um modelo mais preciso reordena os candidatos e mantém só os melhores
5. **Context** -> os chunks escolhidos entram no prompt, junto com a pergunta e as instruções. É aqui que acontece o **grounding**: a resposta passa a ter uma âncora em fontes reais
6. **LLM** -> gera a resposta com **citações** (*citations*), indicando de qual trecho veio cada informação

#### Exemplo de prompt montado

```text
Responda à pergunta usando APENAS os trechos abaixo.
Se a resposta não estiver nos trechos, diga que não encontrou.
Cite a fonte de cada informação.

[1] (politica.pdf, p.2) Reembolsos podem ser solicitados em até 7 dias após o recebimento...
[2] (politica.pdf, p.3) O estorno no cartão de crédito ocorre em até 2 faturas...

Pergunta: Em quanto tempo posso pedir reembolso?
```

> Resposta esperada: *"Você pode pedir reembolso em até 7 dias após receber o produto [1]."*

### Top K

- **K** é a quantidade de chunks que a busca devolve. Com K = 3, os 3 trechos mais próximos entram no contexto e o resto fica de fora.
- É um **ajuste fino de equilíbrio**:
	- **K pequeno** -> menos ruído e menos custo, mas risco de deixar de fora a informação necessária
	- **K grande** -> mais chance de trazer a informação certa, mas mais tokens, mais custo e mais trechos irrelevantes para "distrair" o modelo
- Alternativa ou complemento: um **limiar de similaridade** (*threshold*), em que só entram trechos acima de uma nota mínima. Isso evita colocar no prompt trechos fracos quando nada relevante foi encontrado.
- ==🟡 O Top K controla **quantos** resultados entram no contexto. O reranking controla **quais** são os melhores entre eles==

### Reranking

- **O problema:** a busca vetorial é rápida, mas aproximada. Ela compara vetores calculados **separadamente** para a pergunta e para cada trecho, então às vezes coloca um trecho só "parecido" acima de um que realmente responde.
- **A solução:** uma segunda etapa com um modelo **reranker** (geralmente um *cross-encoder*), que lê a pergunta e o trecho **juntos** e dá uma nota de relevância muito mais precisa.
- **Por que não usar só o reranker?** Ele é lento: ler cada par pergunta + trecho é caro demais para milhões de documentos.
- **O padrão em duas etapas:**
	1. Busca vetorial (rápida) -> traz uns **20 a 50 candidatos**
	2. Reranker (preciso) -> reordena e mantém os **3 a 10 melhores** para o prompt

| | Busca vetorial (*bi-encoder*) | Reranker (*cross-encoder*) |
|---|---|---|
| Como compara | Vetores calculados separadamente | Lê pergunta e trecho juntos |
| Velocidade | Muito rápida (milhões de itens) | Lenta (dezenas de itens) |
| Precisão | Boa | Alta |
| Papel | Filtrar o universo | Escolher os melhores |

### Metadata e sistemas multi-tenant

- **Metadata** são as informações sobre cada chunk: fonte, data, página, idioma, país, loja, cliente, versão, nível de permissão.
- Servem para **filtrar** a busca antes ou durante a recuperação. Exemplos:
	- Só documentos em português
	- Só a versão mais recente da política
	- Só os documentos que **este usuário** tem permissão de ver
- **Multi-tenant** -> um único sistema atende vários clientes (*tenants*), como um SaaS que serve várias empresas. Os documentos de todos ficam na mesma infraestrutura, mas cada cliente só pode acessar os seus.
- ==🟡 Em sistemas multi-tenant, o filtro por metadata (ex.: `tenant_id`) é **obrigatório**. Sem ele, um cliente pode receber trechos de documentos de outro cliente: um vazamento de dados grave==

### Como saber se o problema foi no retrieval ou no generation?

Quando o RAG dá uma resposta errada, a falha pode estar em dois lugares:
- **Retrieval (recuperação)** -> a informação certa **não chegou** ao prompt
- **Generation (geração)** -> a informação certa **chegou** ao prompt, mas o modelo **respondeu mal**

A correção é completamente diferente em cada caso, então diagnosticar vem antes de qualquer ajuste.

#### 1. Olhar os trechos que entraram no prompt
Para cada resposta errada, abra o **log** e faça a pergunta-chave:

> **A informação necessária para a resposta certa estava nos chunks que o LLM recebeu?**

- **Não estava** -> o problema é no **retrieval**
- **Estava** -> o problema é na **generation**

==🟡 Para isso funcionar, o sistema precisa **registrar** (logar) cada etapa: a pergunta, a pergunta reescrita (se houver), os chunks recuperados com suas notas de similaridade, o prompt final enviado ao LLM e a resposta. Sem esse registro, o diagnóstico vira adivinhação. Ferramentas de **observabilidade** (*tracing*) para LLMs fazem isso automaticamente==

#### 2. Teste do "contexto ideal"
Um teste simples e muito eficaz:
1. Pegue a pergunta que deu errado
2. Encontre **manualmente** o trecho que contém a resposta certa
3. Coloque esse trecho direto no prompt, **pulando a busca**, e rode o LLM de novo

- **Acertou com o trecho certo na mão?** -> o LLM sabe responder quando recebe a informação. O problema está no **retrieval**.
- **Errou mesmo com o trecho certo na mão?** -> o problema está na **generation** (prompt, modelo ou o próprio trecho é confuso).

#### 3. Se o problema foi no retrieval: onde exatamente?
Siga o caminho do dado, do começo ao fim:

| Pergunta de diagnóstico | Se a resposta for "não" | Correção |
|---|---|---|
| A informação **existe** na fonte? | O documento nunca foi indexado | Incluir a fonte; revisar a rotina de atualização |
| O texto foi **extraído** corretamente? | Tabela quebrada, PDF escaneado sem OCR, texto embaralhado | Melhorar a extração |
| A informação está **inteira em um chunk**? | Foi cortada entre dois chunks | Ajustar tamanho, overlap ou dividir por seção |
| O chunk certo aparece **entre os K**? | Ficou em 8º lugar com K = 5 | Aumentar K, usar reranking ou busca híbrida |
| O **filtro de metadata** está certo? | O filtro excluiu o documento (versão, idioma, permissão errados) | Corrigir os metadados ou o filtro |
| A pergunta **combina** com o texto do documento? | Usuário fala *"cancelar"* e o documento fala *"rescisão contratual"* | Reescrita da pergunta (*query rewriting*), busca híbrida |

#### 4. Se o problema foi na generation: o que observar?
- **O modelo ignorou o trecho** e respondeu com o que "lembrava" do treino -> reforçar no prompt: *"use apenas os trechos fornecidos"*
- **Interpretou mal** um trecho ambíguo ou muito técnico -> melhorar o texto do chunk (incluir título da seção, contexto) ou usar um modelo mais capaz
- **Misturou trechos contraditórios** (política de 2024 e de 2026 juntas) -> filtrar por versão ou data na metadata
- **Contexto poluído**: muitos trechos irrelevantes "distraíram" o modelo -> reduzir K ou usar reranking
- **Trecho certo perdido no meio** de um contexto muito longo (*lost in the middle*) -> reduzir o contexto ou colocar os melhores trechos no início
- **Instrução fraca**: o prompt não diz o que fazer quando a resposta não está nos trechos -> instruir a dizer *"não encontrei essa informação"*

#### 5. Usar as métricas para ver o padrão
Olhar um caso de cada vez resolve bugs pontuais. Para ver o comportamento geral, use as métricas da seção de avaliação:

| Recall@K (retrieval) | Fidelidade (generation) | Diagnóstico |
|---|---|---|
| Baixo | Qualquer | O problema principal é o **retrieval** |
| Alto | Baixa | O problema principal é a **generation** |
| Alto | Alta, mas respostas ainda erradas | Revisar a **fonte**: os documentos podem estar desatualizados ou errados |

#### Exemplo completo
- **Pergunta:** *"Posso devolver um produto comprado na promoção?"*
- **Resposta do RAG:** *"Sim, todos os produtos podem ser devolvidos em até 7 dias."* (errada: produtos de promoção não têm devolução)
- **Diagnóstico:**
	1. Nos logs, os 5 chunks recuperados falam da regra geral de 7 dias. Nenhum menciona promoção.
	2. Teste do contexto ideal: com o parágrafo sobre promoções colocado à mão, o LLM responde certo.
	3. Conclusão: **retrieval**. Investigando, o parágrafo sobre promoções estava numa **tabela** do PDF que a extração transformou em texto embaralhado, então o vetor dele não ficou próximo da pergunta.
	4. Correção: melhorar a extração de tabelas e reindexar o documento.

==🟡 Regra de ouro: **primeiro descubra se a informação chegou ao modelo**. Trocar o LLM por um mais caro não resolve um problema de retrieval, e mexer no chunking não resolve um problema de geração==

### Como melhorar um RAG ruim?

O primeiro passo é sempre o **diagnóstico** da seção anterior. Depois, aplique a técnica que ataca a causa encontrada.

**Técnicas de melhoria:**
- **Otimizar o chunking** -> chunks grandes demais misturam assuntos; pequenos demais perdem contexto. Testar tamanhos, overlap e divisão por estrutura.
- **Metadata** -> filtrar por país, loja, idioma, permissão, versão etc. para reduzir o universo de busca e evitar trechos errados.
- **Hybrid Search** -> combinar busca por palavra-chave (BM25) com busca semântica. Essencial quando termos exatos importam: códigos de produto, nomes, siglas, números de erro.
- **Reranking** -> reordenar os candidatos com um modelo mais preciso.
- **Reescrita da pergunta** (*query rewriting*) -> usar um LLM para reformular perguntas vagas ou incompletas antes da busca (*"e o prazo?"* -> *"qual o prazo para pedir reembolso?"*).
- **Melhorar a extração** -> corrigir tabelas quebradas, aplicar OCR, remover lixo do texto.
- **Ajustar o prompt** -> instruir o modelo a usar só os trechos, citar fontes e dizer "não sei" quando a informação não estiver presente.

### Avaliação: por que medir é essencial

- Sem avaliação, qualquer mudança (tamanho do chunk, valor do K, modelo de embedding) é um chute. Avaliar transforma ajustes em **decisões baseadas em dados**.
- O RAG deve ser avaliado em **duas partes separadas**:

| O que avaliar | Pergunta-chave | Exemplos de métrica |
|---|---|---|
| **Retrieval** | Os trechos certos foram encontrados? | **Recall@K** (o trecho certo está entre os K?), **Precision@K** (quantos dos K são relevantes?), **MRR** (o trecho certo veio em que posição?) |
| **Generation** | A resposta usou bem os trechos? | **Fidelidade** (*faithfulness*: a resposta se apoia só nos trechos?), **Relevância** (responde o que foi perguntado?), **Correção** (está certa?) |

- **Como avaliar na prática:**
	1. Montar um **conjunto de teste** (*golden dataset*): perguntas reais com as respostas e os trechos corretos esperados. Exemplo de uma linha:
		- **Pergunta:** *"Qual o prazo para pedir reembolso?"*
		- **Resposta esperada:** *"7 dias corridos após o recebimento"*
		- **Trecho esperado:** `politica.pdf, p.2, seção Prazos`
	2. Rodar o sistema sobre essas perguntas a cada mudança
	3. Medir as métricas, de forma automática ou com um **LLM avaliador** (*LLM-as-a-judge*), e comparar versões
- Em produção, também vale **monitorar** perguntas sem resposta, avaliações negativas dos usuários e trechos que nunca são recuperados.
- ==🟡 RAG **reduz** alucinação, mas não garante a verdade. Só a avaliação contínua mostra se o sistema está realmente acertando==

### AULA 4: Resumo
- **Indexing** -> prepara os dados: Fonte -> Extract -> Chunk -> Embed -> Store
- **Vector Database** -> guarda vetor + texto + metadata e encontra os vizinhos mais próximos rapidamente
- **Retrieval + Generation** -> pergunta vira vetor, busca os Top K, monta o contexto e o LLM responde com citações
- **Top K** -> controla quantos resultados entram no contexto
- **Reranking** -> segunda etapa, mais precisa, que escolhe os melhores entre os candidatos
- **Metadata** -> filtra a busca; essencial em sistemas multi-tenant para isolar os dados de cada cliente
- **Diagnóstico** -> a informação certa chegou ao prompt? Se não, é **retrieval**; se sim, é **generation**. O teste do "contexto ideal" confirma
- **Melhorar um RAG** -> atacar a causa encontrada: extração, chunking, metadata, busca híbrida, reranking, reescrita da pergunta ou prompt
- **Avaliação** -> medir retrieval e generation separadamente, com um conjunto de teste
- **RAG** -> reduz a **hallucination**, mas não garante a verdade



## GLOSSÁRIO

| Termo | Significado |
|---|---|
| **Adapter** | Pequeno conjunto de parâmetros treinado no LoRA, acoplado a um modelo congelado |
| **Alinhamento** | Etapa de treino que ensina o modelo a preferir respostas úteis, honestas e seguras (RLHF, DPO) |
| **ANN** | *Approximate Nearest Neighbors*: busca aproximada pelos vetores mais próximos, rápida em grandes volumes |
| **Atenção** | Mecanismo dos Transformers que conecta cada token aos outros tokens relevantes do contexto |
| **Autoregressivo** | Que gera um token por vez, usando os tokens anteriores como contexto |
| **Backpropagation** | Algoritmo que calcula quanto cada parâmetro contribuiu para o erro |
| **Benchmark** | Prova padronizada para comparar modelos |
| **BM25** | Algoritmo clássico de busca por palavra-chave |
| **Chunk** | Trecho de um documento, unidade de busca no RAG |
| **Citation** | Indicação da fonte de onde veio uma informação da resposta |
| **Context window** | Limite de tokens que o modelo considera em uma chamada, incluindo a resposta |
| **Cross-encoder** | Modelo que lê pergunta e trecho juntos para dar uma nota de relevância; usado no reranking |
| **Embedding** | Vetor de números que representa o significado de um texto, imagem ou áudio |
| **Eval** | Teste criado para medir a qualidade de um sistema de IA numa tarefa específica |
| **Few-shot** | Técnica de prompt que inclui exemplos do resultado esperado |
| **Fine-tuning** | Continuar o treino de um modelo pronto com exemplos específicos |
| **Golden dataset** | Conjunto de perguntas com respostas e fontes corretas, usado para avaliar o sistema |
| **Gradiente descendente** | Método que ajusta os parâmetros na direção que reduz o erro |
| **Grounding** | Ancorar a resposta em fontes verificáveis |
| **Hallucination** | Resposta plausível e convincente, mas falsa ou sem base nas fontes |
| **HNSW** | Tipo de índice muito usado em bancos vetoriais para busca aproximada |
| **Hybrid search** | Combinação de busca por palavra-chave com busca semântica |
| **Inference** | Uso do modelo já treinado para gerar uma saída |
| **LLM** | *Large Language Model*: modelo de linguagem com bilhões de parâmetros |
| **LLM-as-a-judge** | Uso de um LLM para avaliar respostas de outro sistema |
| **Logit** | Pontuação bruta que o modelo dá a cada token antes do softmax |
| **LoRA / QLoRA** | Fine-tuning eficiente que treina só um pequeno adapter (QLoRA: com o modelo base quantizado) |
| **Loss** | Função que mede o tamanho do erro do modelo durante o treino |
| **Metadata** | Informações sobre cada chunk (fonte, data, idioma, permissão) usadas para filtrar e citar |
| **Multi-tenant** | Sistema que atende vários clientes isolando os dados de cada um |
| **Overfitting** | Quando o modelo decora os exemplos de treino e vai mal em dados novos |
| **Parâmetros** | Pesos e vieses da rede neural, onde fica o conhecimento do modelo |
| **Pré-treino** | Treino em larga escala que cria o conhecimento geral do modelo |
| **Prompt** | Instruções, contexto, exemplos e pergunta enviados ao modelo |
| **Query rewriting** | Reformular a pergunta do usuário antes da busca para melhorar a recuperação |
| **RAG** | *Retrieval-Augmented Generation*: buscar informação externa e colocá-la no contexto antes de gerar |
| **Recall@K** | Métrica que indica se o trecho certo está entre os K recuperados |
| **Reranking** | Reordenar os candidatos da busca com um modelo mais preciso |
| **Similaridade de cosseno** | Medida do ângulo entre dois vetores; perto de 1 = significado parecido |
| **Softmax** | Função que transforma logits em probabilidades que somam 100% |
| **Temperature** | Controle da variabilidade na escolha do próximo token |
| **Token** | Unidade de texto que o modelo processa |
| **Tokenizador** | Componente que quebra o texto em tokens |
| **Top-K** | Quantidade de trechos que a busca devolve para o contexto (ou de tokens considerados no sorteio) |
| **Top-p** | Sorteio restrito aos tokens que somam p% da probabilidade |
| **Vector database** | Banco de dados especializado em guardar vetores e buscar os mais próximos |
