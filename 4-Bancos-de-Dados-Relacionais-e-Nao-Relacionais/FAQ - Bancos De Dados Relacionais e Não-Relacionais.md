# **Materiais:**

**Q: Qual o link para os materiais do professor Herwin?**

R: O material de apoio para atividades sobre Bancos de Dados de chave-valor consta no ícone de folha a4 ao lado do título da disciplina, os arquivos das práticas do professor Herwin estão em uma página do Dropbox, é possível fazer o download e executar. Os arquivos solicitados:

1.Exemplo de Chaves de Acesso: NoSQL\_BD\_ChaveValor\_AccessKeys.xlsx

2.Comandos do AWS CLI: NoSQL\_BD\_ChaveValor\_AWS\_CLI.pdf

3.Dados do Exercício: NoSQL\_BD\_ChaveValor\_Dados.txt

4.Manual do PartiQL: NoSQL\_BD\_ChaveValor\_PartiQL.pdf

5.Script em Linguagem R para o Exercício: NoSQL\_BD\_ChaveValor\_Scripts.R

6.Slides das Aulas Teóricas: NoSQL\_BD\_ChaveValor\_Slides.pdf

7.Vídeo da Aula Prática: NoSQL\_BD\_ChaveValor\_Pratica.mp4

Encontram-se na folha a4 - Aula 1 - Material Complementar (BDChave-Valor).

Os arquivos das práticas sobre Bancos de Dados orientado a Grafos do professor Herwin estão em uma página do Dropbox, você poderá fazer o download e executar. Os arquivos solicitados encontram-se na folha a4 - Aula 2 - BDGrafo.

O material sobre banco de dados orientado a Documentos, ainda não foi disponibilizado pelo professor Herwin por uma falta de atenção. Estamos em contato com ele para poder disponibilizar o mais rápido possível.

# **Ferramentas:**
**Estou encontrando um erro ao rodar o código do "shortest path". Neo4j retorna o erro "There is no procedure with the name `gds.alpha.kShortestPaths.stream` registered for this database instance."**

Este erro se dá pois ao fazer a instalação do Neo4j a Local DBMS padrão, ele cria sempre a versão mais nova baixada. É necessário então setar a versão utilizada pelo professor Herwin (4.2.1).

# **Conceitos e Exercícios:**

**Q: Supondo que, ao passarmos do modelo conceitual para o modelo lógico, optamos por gerar uma tabela própria para um relacionamento; esta nova tabela automaticamente terá pelo menos duas colunas chave estrangeira se referindo a chave primária da tabela &quot;referidora&quot; e a chave primária da tabela referida.**

**Estas duas colunas chaves estrangeiras da nova tabela são**  **necessariamente**  **chave primária desta nova tabela?**

R: Assumindo que o relacionamento seja muitos-para-muitos (também chamado de N-N), a técnica usual de mapeamento é a geração de uma tabela para esse relacionamento contendo duas chaves estrangeiras, uma para cada entidade envolvida no relacionamento.

Suponha que tenhamos o exemplo da relação &quot;atuação&quot; (N-N) entre uma entidade &quot;engenheiro&quot; e uma entidade &quot;projeto&quot;. Agora vamos supor que temos {e1, e2, e3} como engenheiros e {p1, p2} como projetos. Os seguintes pares podem representar a relação &quot;atuação&quot;: (e1, p1), (e1, p2), (e2, p1). Observe que precisamos que cada par seja único (por exemplo, o engenheiro e1 não pode aparecer duas vezes atuando no projeto p1), logo a chave primária será uma chave composta pelas colunas de ambas as chaves estrangeiras que referenciam o engenheiro e o projeto.

Se assumirmos que seja um relacionamento um-para-muitos (1-N), a opção de usar uma tabela própria deve ser analisada caso a caso e verificar o comportamento das chaves. Suponha que tenhamos o exemplo da relação &quot;financia&quot; entre uma entidade &quot;financeira&quot; e várias entidades &quot;venda&quot;. Agora vamos supor que tenhamos {f1, f2} como financeiras e {v1, v2, v3, v4} como vendas. Os seguintes pares podem representar a relação &quot;financia&quot;: (f1, v1), (f1, v2), (f2, v3).

Observe que também neste caso cada venda somente apareceria no máximo uma única vez no relacionamento e, portanto, poderia ser utilizado somente a chave estrangeira para a entidade &quot;venda&quot; como uma chave primária conforme sua sugestão.

**Q: Referente à tabela de pré-requisitos, (slide 62 da apresentação de apoio).**

**As colunas cod\_depto e num\_disc, que são chaves estrangeiras e referenciam colunas homônimas na tabela disciplina, formam juntas a chave primária da própria tabela prereq.**

**Entretanto, como pode-se esperar que uma disciplina tenha mais de um pré-requisito, de fato observamos ocorrências duplas, por ex., de INF01 e 109 (bem como INF01, 108).**

**Isto não é uma quebra de integridade de chave? Uma vez que há mais de uma linha com os mesmos valores nas colunas chave-primária da tabela prereq.**

R: A imagem do slide 62 deveria estar pintada de vermelho todas as quatro colunas da tabela &quot;prereq&quot; de modo a indicar que a chave primária seria composta das quatro colunas. Logo, esta observação de que apenas as colunas &quot;cod\_depto&quot; e &quot;num\_disc&quot; são insuficientes como chave primária está corretíssima.

**Q: Ao marcar com o X os dados que foram excluídos, eles deixam de ser acessados, ou eu poderia utilizá-los como dados históricos?**

**Por exemplo em uma mudança de endereço, é marcado com o X o antigo endereço, mas se quisermos saber todos os endereços de um cliente é possível extrair essa informação baseado no histórico de alterações neste campo?**

R: No Cassandra não tem como consultar um dado deletado. Ele cria o _tombstone_ que indica que o dado foi deletado, depois de um tempo ele faz compactação e deleta fisicamente para manter a base mais enxuta. Nesse meio tempo em que não ocorre a deleção fisicamente, ele mantém todos os logs de comandos, mas na busca ele retorna sempre a versão mais recente.

Teria que verificar se tem como desabilitar a compactação, mas acabaria perdendo performance até ficar uma base muito inchada. Para utilizar como histórico, seria melhor a criação de um campo de _deleted_ (_boolean_).

**Q: Qual a relação possível em um grafo do tipo multigrafo?**

R: O professor Herwin é claro em sua explicação durante a parte 01 da aula 02, ao minuto 21 quando explica os tipos de grafos. Quando dizemos multigrafo nos referimos aos casos em que o vértice pode ter mais de 1 saída ou entrada. Quando nos referimos a grafo, aí sim entram os autos relacionamentos. A mesma questão também se encontra elucidada no livro da disciplina, na página 16, parte 1 da aula 2

**Q: Fiquei com uma dúvida referente a chave artificial que o professor explicou na última parte da aula 04. Quando crio uma chave artificial eu deixo de utilizar a composição de chaves que haviam dispostos no modelo anterior com um conjunto de colunas que mantinha a integridade tanto dos dados quanto das associações entre astabelasNão perco esta referência? Ou seja, não corro o risco de ter conteúdo duplicado nas outras colunas?**

R: Como o professor Júlio indicou, não há nenhum demérito em ter as chaves primárias compostas por várias partes (colunas) mas, para simplificar a leitura das chaves e relacionamentos podemos utilizar\criar uma coluna "extra" para ser apenas a chave primária que geralmente é um identificador único. Mas note que ele indica que muitas vezes sabe que as demais colunas também permanecem candidatas e que de acordo com o negócio, ele sabe que a composição permanece única. Essa chave primária artificial é utilizada para colocar de forma genérica a chave primária de uma entidade, pois uma chave natural pode se tornar muito complexa, impactando em termos de performance no banco de dados. Mas usando um atributo artificial na chave primaria podemos vir a repetir varias vezes as mesmas colunas, mas não seria possível ter o registro (linha) todo repetido, pois essa chave primária será auto-incremental.

**Q: Gostaria de saber mais sobre como se enquadra o "CockroachDB", já que ele é tanto um noSQL como também um SQL transacional.**

R: O CockroachDB é um banco de dados SQL que pode escalar horizontalmente. Se você precisa para suportar maiores volumes, você pode simplesmente adicionar mais máquinas. Com CockroachDB, os servidores replicam automaticamente e reequilibrar-se, que mantém o seu sistema disponível à medida que cresce e evolui. Ele  busca oferecer o mesmo desempenho escalável dos bancos NoSQL, para cargas de trabalho OLTP read-write, mantendo as garantias das propriedades ACID em suas transações.

_\*FAQ gerado com base em comentários até o dia 02/03/2022._