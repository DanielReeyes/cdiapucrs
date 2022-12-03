# **Materiais:**

**Q: Onde encontro os materiais de apoio e os arquivos notebooks para execução dos exercícios?**

R: O material de apoio consta no ícone de folha a4 ao lado do título da disciplina.

# **Ferramentas:**

Não houve comentários sobre ferramentas até a data de geração deste FAQ.

# **Conceitos e Exercícios:**

**Q: O aprendizado auto-supervisionado é o mesmo que aprendizado por reforço? Se não, onde se encaixa o aprendizado por reforço e no que se difere do auto-supervisionado?**

R: Diferenciar o aprendizado auto-supervisionado do aprendizado por reforço é mais simples, mas a linha entre auto-supervisionado e não supervisionado é bastante tênue. Na primeira aula do professor Thomas (Aula 3), ele dá uma explicação sobre essas diferenças.

De forma geral, o **aprendizado auto-supervisionado** não utiliza rótulos, mas tem algum tipo de mecanismo para "prover supervisão". Por exemplo, nos casos de processamento de linguagem natural como BERT, parte das palavras das frases é removida e o algoritmo é treinado para prever as palavras. Nesse caso, não existe um "rótulo", mas ao remover as palavras e tentar prevê-las, podemos entender que é um "método não supervisionado treinado de forma supervisionada".

O **aprendizado por reforço** é bastante diferente onde a principal diferença diferença está no mecanismo de aprendizado - é um paradigma que busca aprender por tentativa e erro, e utiliza um mecanismo de feedback para guiar seu aprendizado. O objetivo é aprender uma "política", que mapeia um "estado" para uma sequência de ações que maximizam tal recompensa ao longo do tempo. Em outras palavras, modelos de aprendizado de máquina são treinados para tomar uma sequência de decisões. O agente aprende a atingir uma meta em um ambiente incerto e potencialmente complexo. 
No aprendizado por reforço, o sistema de inteligência artificial enfrenta uma situação. O computador utiliza tentativa e erro para encontrar uma solução para o problema. Para que a máquina faça o que o programador deseja, a inteligência artificial recebe recompensas ou penalidades pelas ações que executa. Seu objetivo é maximizar a recompensa total.Um ponto interessante é que, embora o Cientista de Dados defina a política de recompensa – isto é, as regras do jogo – ele não dá ao modelo nenhuma dica ou sugestão de como resolver o jogo. Cabe ao modelo descobrir como executar a tarefa para maximizar a recompensa, começando com testes totalmente aleatórios e terminando com táticas sofisticadas. 

Também na Aula 3, o professor Thomas traz alguns exemplos desse tipo de aprendizado. Um exemplo prático de aprendizado por reforço seria aprender a sequência de movimentos que um braço robótico deve realizar para conseguir pegar um objeto, ou a sequência de movimentos que um jogador de um determinado jogo deve realizar para completar uma fase.

**Q: Quanto ao exemplo 1.2.kmedoids_1, gostaria de alertar que a sklearn-extra não está previamente instalada no google colab**

R: É preciso utilizar o comando de instalação antes da execução.'pip install scikit-learn-extra'

**`Q: Sobre o conceito de validação externa, se há rotulos para confrontar o resultado, por que o aprendizado é não supervisionado? Não seria um problema de classificação supervisionado?`**

`R: Na verdade a validação externa seria para saber identificar se o seu modelo criado está tendo capacidade de acertar os rótulos MAS os rótulos não estão INFLUENCIANDO o treinamento do modelo. Por tal motivo ele é um modelo de classificação não supervisionado.`

**`Q: No vídeo da Parte 1, minuto 20:56, o professor comenta que o índice supervisionado pode ser usado para avaliar bases com rótulos. A minha dúvida é: se já existem os rótulos, por que usar um aprendizado não supervisionado (como o agrupamento), sendo que poderia ser utilizado um aprendizado supervisionado (classificação)? Qual seria o objetivo do uso do agrupamento ou qual o benefício de analisar desse modo?`**

`R: É uma ótima pergunta. De fato os índices supervisionados necessitam de rótulos externos. Como visto em aula, existem alguns motivos para usar tais índices:`
`- Quando está se criando algum algoritmo novo de agrupamento de dados e deseja-se comparar com resultados já conhecidos (e.g., tentando replicar um comportamento específico)`
`- Quando se deseja avaliar que o agrupamento corresponde a algum rótulo já conhecido (e.g., no caso de segmentação de clientes, comparar com algum rótulo provido pelo departamento de Marketing).`
`Na prática, acaba-se usando muito mais os índices internos por não termos rótulos. De igual forma, em alguns contextos muito específicos pode ser aplicado (benchmarking de algoritmos com bases conhecidas ou com rótulos que representam algo que o agrupamento vai substituir).`

_\*`FAQ gerado com base em comentários até o dia 30/11/2022.`_
