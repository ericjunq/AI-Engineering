
## O que é Engenharia de Contexto?
- Construção de sistemas dinâmicos pra fornecer as informações e ferramentas certas no formato correto para que o LLM (Large Language Model) possa realizar a tarefa de maneira plausível
- Muitas das vezes em que um agente não tem um desempenho confiável, a causa é que o contexto, instruções e ferramentas apropriadas não foram comunicadas ao modelo
- **Engenharia de contexto é uma das habilidades mais importantes que um Engenheiro de IA pode ter** 

#### Context Window e sua importância na precisão das respostas
- Janela de contexto (Context Window) é o toda a grande de informações que o modelo tem acesso - **Isso inclui os prompts/inputs, as respostas, o histórico de conversa, RAGs e instruções pré-definidas**
- Context Windows tem tamanhos limitados
- Quanto mais contexto, mais informação. Ao longo do crescimento da Context Window, a precisão das respostas do LLM vai degradando devido ao excesso de informações
- Informações desnecessárias e/ou irrelevantes fazem a LLM ficar "distraída" em meio a tanta informação, afetando negativamente a precisão do modelo

#### O que uma LLM precisa ter pra funcionar corretamente?
- Bons prompts (Instruções claras)
- Qualidade dos dados 

	A IA é uma ferramenta probabilística, e nossa função é influenciar positivamente os resultados para reproduzir os melhores resultados na maioria das vezes

#### LLMs são STATELESS, ou seja: Não guardam estado, ou seja, ela não guarda memória. Os históricos de mensagem + identificadores são de extrema importância para ceder a LLM todo o contexto necessário para que ela prossiga atuando o mais precisamente possível