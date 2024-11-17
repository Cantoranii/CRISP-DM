# RELATÓRIO - CRISP-DM
Ánalise e Desenvolvimento de Dados
# Compreensão do Projeto
Este relatório faz parte de um trabalho acadêmico envolvendo análise de dados para o curso de Ciências de Dados e IA na Faculdade FEI. O objetivo principal é aplicar o framework CRISP-DM, em um data set extraído da plataforma https://www.kaggle.com. Relacionado ao tema de alguma ODS. No meu caso optei pela escolha da ODS 3 ( Saúde e bem Estar)

# Definição do Problema
A relação entre problemas de saúde mental (como ansiedade, depressão e crise de pânico) e o desempenho acadêmico é uma questão crucial. Entretanto, as influências específicas desses fatores na performance dos estudantes ainda carecem de uma análise detalhada e baseada em dados

# Escopo
 - O objetivo dessa amostra é mostrar uma análise de dados concretos no modelo CRISP-DM de fácil compreensão
 - Após a importação dos dados para o excel realizei todas as etapas necessárias, o entendimento, a preparação, modelagem e a avaliação
 - Ações e métodos executados - One-hot encoding, exclusão de linhas vazias, tradução de colunas do inglês para o português brasileiro, verificação de outliers por meio de quartis, regressão linear, criação de gráficos.

-----------

# Aquisição  e entendimento dos dados
DATA SET CRU

Para vizualização dos dados extraídos antes das formatações acessar: https://www.kaggle.com

Linhas: 102 no total
Colunas: 11 no total - FEATURES: Timestamp, Gender, Age, Curse, Your current year of study, What is your CGPA?, Marital status, Do you have depression?, Do you have anxiety?, Do you have panick attacks?, Did you seek any specialist for a treatment?

----------

# Modelagem
LIMPEZA DE DADOS: Foi feita a remoção de uma linha com valor nulo, Resultando em 101 linhas no total. A tradução do Inglês para o portugues foi feita, NEW FEATURES: DATA, GÊNERO, IDADE, CURSO, ANO, MÉDIA, CASADO?, VOCÊ TEM DEPRESSÃO?, VOCÊ TEM ANSIEDADE?, VOCÊ TEM ATAQUES DE PÂNICO?, VOCÊ BUSCA ALGUM ESPECIALISTA PARA TRATAMENTO?

ONE-HOT ENCODING: Transformação de variáveis categóricas em variáveis binárias para melhor entedimento no machine learning. Respostas como "Sim" e "Não" nas colunas (CASADO?, VOCÊ TEM DEPRESSÃO?, VOCÊ TEM ANSIEDADE?, VOCÊ TEM ATAQUES DE PÂNICO?, VOCÊ BUSCA ALGUM ESPECIALISTA PARA TRATAMENTO?) foram alteradas para 0 e 1, 0 equivale a resposta "Não" e 1 equivale a resposta "Sim". o mesmo processo foi feito para outras colunas, como "Gênero", 0 equivale a "Femenino" e 1 equivale a "Masculino". As média dos alunos foram alteradas para números inteiros para melhor vizualização em gráficos. 

REGRESSÃO: Durante a realização da análise de regressão linear, enfrentei alguns desafios que comprometeram a qualidade dos resultados obtidos. A seguir, descrevo detalhadamente o processo e os problemas encontrados:

Verificação de Outliers:
Antes de realizar a regressão, executei uma verificação para identificar outliers no dataset. Utilizei o método baseado nos quartis (Q1 e Q3), verificando os limites inferiores e superiores através do cálculo do intervalo interquartil (IQR). Após essa análise, constatei que não havia outliers significativos nos dados. Com isso, avancei para a próxima etapa.

Seleção de Colunas para a Regressão:
Um dos maiores desafios foi a ausência de colunas com alta correlação no dataset. A baixa correlação entre as variáveis dificultava a escolha de um par de colunas ideal para a regressão. Para superar essa limitação, utilizei a função =CORREL no Excel para identificar as colunas que apresentavam a maior correlação possível. 

As colunas escolhidas foram:
"Curso" (representando o curso dos alunos)
"Você tem depressão?" (indicando a gravidade da depressão em porcentagem).
Transformação dos Dados:
Como essas colunas continham dados qualitativos realizei uma transformação para adequar os valores ao formato necessário para a regressão. Converti os dados categóricos em percentuais, e logo em seguida em números decimais, possibilitando sua utilização no modelo.

Execução da Regressão Linear:
Após a preparação dos dados, apliquei a regressão linear utilizando as colunas selecionadas. O objetivo era identificar a relação entre o curso dos alunos e a gravidade da depressão.

Problemas Identificados Após a Regressão:
Apesar de ter conseguido realizar a regressão, percebi que os resultados não foram satisfatórios. O principal motivo foi a natureza dos dados: as variáveis escolhidas não apresentavam um padrão de aumento gradual e consistente entre si. Essa característica tornou os gráficos gerados pouco claros e com baixo poder preditivo. Como resultado, conclui que a regressão linear não era a técnica mais adequada para os dados analisados.

GRÁFICOS: Após perceber que a regressão não tinha ficado muito clara, resolvi criar um gráfico mostrando a verdadeira intenção do dataset, escolhendo as colunas "VOÇÊ TEM DEPRESSÃO?" e a coluna "MÉDIA", foi possível ver a média de notas dos alunos que possuem depressão e dos que não possuem, assim mostrando o impacto que a baixa saúde mental pode afetar na vida dos estudantes






