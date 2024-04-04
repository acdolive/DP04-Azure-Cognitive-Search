# Azure Cognitive Search: Utilizando AI Search para indexação e consulta de Dados

## Criar um recurso de Pesquisa de IA do Azure
Entre no portal do Azure.

Clique no botão + Criar um recurso, procure Pesquisa de IA do Azure e crie um recurso de Pesquisa de IA do Azure com as seguintes configurações:

Assinatura: sua assinatura do Azure.
Grupo de recursos: selecione ou crie um grupo de recursos com um nome exclusivo.
Nome do serviço: um nome exclusivo.
Localização: Escolha qualquer região disponível.
Nível de preços: Básico
Selecione Revisar + criar e, depois de ver a resposta Êxito da validação, selecione Criar.

Após a conclusão da implantação, selecione Ir para o recurso. Na página de visão geral da Pesquisa de IA do Azure, você pode adicionar índices, importar dados e pesquisar índices criados.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/ffc6393a-4c5d-40ec-8321-2efbc06e1c80)

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/2fc91171-1385-4a79-a05c-e960f65266b4)

## Criar um recurso de serviços de IA do Azure

Você precisará provisionar um recurso de serviços de IA do Azure que esteja no mesmo local que seu recurso de Pesquisa de IA do Azure. Sua solução de pesquisa usará esse recurso para enriquecer os dados no armazenamento de dados com insights gerados por IA.

Retorne à home page do portal do Azure. Clique no botão +Criar um recurso e procure serviços de IA do Azure. Selecione criar um plano de serviços de IA do Azure. Você será levado a uma página para criar um recurso de serviços de IA do Azure. Configure-o com as seguintes configurações:
Assinatura: sua assinatura do Azure.
Grupo de recursos: o mesmo grupo de recursos que seu recurso de Pesquisa de IA do Azure.
Região: o mesmo local que seu recurso de Pesquisa de IA do Azure.
Nome: Um nome exclusivo.
Nível de preços: Standard S0
Ao marcar esta caixa reconheço que li e compreendi todos os termos abaixo: Selecionado
Selecione Revisar + criar. Depois de ver a resposta Validação aprovada, selecione Criar.

Aguarde a conclusão da implantação e exiba os detalhes da implantação.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/cba795a5-c1fc-498c-8cac-911341233996)

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/5e3053ed-27b9-4a7d-a480-b3e754d92da5)

## Criar uma conta de armazenamento
Retorne à home page do portal do Azure e selecione o botão + Criar um recurso.

Procure uma conta de armazenamento e crie um recurso de conta de armazenamento com as seguintes configurações:
Assinatura: sua assinatura do Azure.
Grupo de recursos: o mesmo grupo de recursos que os recursos da Pesquisa de IA do Azure e dos serviços de IA do Azure.
Nome da conta de armazenamento: um nome exclusivo.
Localização: Escolha qualquer local disponível.
Desempenho: Standard
Redundância: Armazenamento localmente redundante (LRS)
Clique em Rever e, em seguida, clique em Criar. Aguarde a conclusão da implantação e vá para o recurso implantado.

Na conta de Armazenamento do Azure que você criou, no painel de menu esquerdo, selecione Configuração (em Configurações).
Altere a configuração de Permitir acesso anônimo de Blob para Habilitado e selecione Salvar.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/33627a79-4879-43d1-b257-202d9ec647f0)

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/9c91d5c4-ed01-419c-9cc5-65371cd10245)

## Configuração para realizar o desafio

Vá até a opção de configuração

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/a5565d06-d29f-4be4-be2f-8a1d152616f2)

Habilite o acesso anônimo de blob e clique em salvar. 

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/4bc9881c-00c2-4cfe-9055-538cbbe3ab06)

Sem esta alteração não será habilita a opção para criar um novo contêiner com as configurações anônimas necessárias para o teste.  

## Carregar documentos no Armazenamento do Azure
No painel de menu esquerdo, selecione Contêineres.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/2f95dc9a-7763-4da0-a616-f1b87be9b68e)

Selecione + Contêiner. Um painel do lado direito é aberto.
Insira as seguintes configurações e clique em Criar:
Nome: café-comentários
Nível de acesso público: Contêiner (acesso de leitura anônimo para contêineres e blobs)
Avançado: sem alterações.
Em uma nova guia do navegador, baixe as revisões de café compactadas do e extraia os arquivos para a pasta de comentários.https://aka.ms/mslearn-coffee-reviews

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/68cc3f56-cba1-4413-bc79-8752d05201db)


No portal do Azure, selecione seu contêiner de avaliações de café. No contêiner, selecione Carregar.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/511bf72e-5d29-408d-b06d-f8c77138d25b)

No painel Carregar blob, selecione Selecionar um arquivo.

Na janela do Explorer, selecione todos os arquivos na pasta de comentários, selecione Abrir e selecione Carregar.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/a8158224-436a-4316-9d62-cf9217ec9af0)

Depois que o carregamento for concluído, você poderá fechar o painel Carregar blob. Seus documentos agora estão em seu recipiente de armazenamento de revisões de café.
Indexar os documentos
Depois de ter os documentos em armazenamento, você pode usar a Pesquisa de IA do Azure para extrair insights dos documentos. O portal do Azure fornece um assistente de Importação de dados. Com esse assistente, você pode criar automaticamente um índice e um indexador para fontes de dados com suporte. Você usará o assistente para criar um índice e importar seus documentos de pesquisa do armazenamento para o índice de Pesquisa de IA do Azure.

No portal do Azure, navegue até seu recurso de Pesquisa de IA do Azure. Na página Visão geral, selecione Importar dados.


![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/3cc67ac9-a663-4303-a998-094c7ec1adb8)

Na página Conectar aos seus dados, na lista Fonte de Dados, selecione Armazenamento de Blobs do Azure. Conclua os detalhes do armazenamento de dados com os seguintes valores:
Fonte de dados: Armazenamento de Blobs do Azure
Nome da fonte de dados: coffee-customer-data
Dados a serem extraídos: conteúdo e metadados
Modo de análise: Padrão
Cadeia de conexão: *Selecione Escolher uma conexão existente. Selecione sua conta de armazenamento, selecione o contêiner de revisões de café e clique em Selecionar.
Autenticação de identidade gerenciada: Nenhuma
Nome do contêiner: essa configuração é preenchida automaticamente depois que você escolhe uma conexão existente.
Pasta Blob: deixe isso em branco.
Descrição: Comentários a Fourth Coffee shops.
Selecione Avançar: Adicionar habilidades cognitivas (Opcional).

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/b93dffb6-e437-485a-9eef-1c5d3bce4ba1)

Na seção Anexar Serviços Cognitivos, selecione seu recurso de serviços de IA do Azure.

Na seção Adicionar enriquecimentos:
Altere o nome do Skillset para coffee-skillset.
Marque a caixa de seleção Habilitar OCR e mesclar todo merged_content texto em campo
![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/c197ebfa-0b96-451b-a17a-64ccfb8b2f82)

selecione Avançar: Adicionar habilidades cognitivas (Opcional).

Na seção Anexar Serviços Cognitivos, selecione seu recurso de serviços de IA do Azure.

Na seção Adicionar enriquecimentos:
Altere o nome do Skillset para coffee-skillset.
Marque a caixa de seleção Habilitar OCR e mesclar todo merged_content texto em campo.
Nota É importante selecionar Habilitar OCR para ver todas as opções de campo enriquecidas.


Verifique se o campo Dados de origem está definido como merged_content.
Altere o nível de granularidade de enriquecimento para Páginas (blocos de 5000 caracteres).
Não selecione Habilitar enriquecimento incremental
Selecione os seguintes campos enriquecidos:

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/44720ce9-d1e8-478b-92d7-6050441803aa)


Habilidade Cognitiva	Parâmetro	Nome do campo
Extrair nomes de locais	 	Locais
Extrair frases-chave	 	Frases-chave
Detectar sentimento	 	sentimento
Gerar tags a partir de imagens	 	imageTags
Gerar legendas a partir de imagens	 	imageCaption

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/9f233ae3-27a3-4e7f-b24a-cbeea905cca7)

Em Salvar enriquecimentos em um repositório de conhecimento, selecione:
Projeções de imagens
Documentos
Páginas
Frases-chave
Entidades
Detalhes da imagem
Referências de imagens

Nota : 

Nota Se um aviso solicitando uma Cadeia de Conexão da Conta de Armazenamento for exibido.

Captura de tela que mostra o aviso da tela de conexão da conta de armazenamento com a opção "Escolher uma conexão existente" selecionada.

Selecione Escolher uma conexão existente. Escolha a conta de armazenamento criada anteriormente.
Clique em + Contêiner para criar um novo contêiner chamado knowledge-store com o nível de privacidade definido como Privado e selecione Criar.
Selecione o contêiner de armazenamento de conhecimento e clique em Selecionar na parte inferior da tela.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/57eb93ec-50e3-462a-af42-70524994f974)

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/5b4466c3-4275-4e79-a990-4a22bf2b78f5)

elecione Projeções de blob do Azure: Documento. Uma configuração para Nome do contêiner com as exibições preenchidas automaticamente pelo contêiner do repositório de conhecimento. Não altere o nome do contêiner.

Selecione Avançar: Personalizar índice de destino. Altere o nome do índice para coffee-index.

Verifique se a chave está definida como metadata_storage_path. Deixe o nome do Sugeridor em branco e o modo de Pesquisa preenchido automaticamente.

Revise as configurações padrão dos campos de índice. Selecione filtrável para todos os campos que já estão selecionados por padrão.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/69422c5b-960a-4f25-a838-25d65f136d24)

Selecione Avançar: Criar um indexador.

Altere o nome do indexador para coffee-indexer.

Deixe a Agenda definida como Uma vez.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/4a8ec4a4-3e6f-4932-b321-46fabf71ee62)

Expanda as opções Avançadas. Verifique se a opção Base-64 Encode Keys está selecionada, pois as chaves de codificação podem tornar o índice mais eficiente.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/a791c1d5-1c4f-4e14-a2c7-13d0f46e8a72)

Selecione Enviar para criar a fonte de dados, o conjunto de habilidades, o índice e o indexador. 

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/f448ea64-84ff-47ae-8672-3f9353bbc29b)

O indexador é executado automaticamente e executa o pipeline de indexação, que:
Extrai os campos de metadados do documento e o conteúdo da fonte de dados.
Executa o conjunto de habilidades cognitivas para gerar campos mais enriquecidos.
Mapeia os campos extraídos para o índice.

Retorne à página de recursos da Pesquisa de IA do Azure. No painel esquerdo, em Gerenciamento de Pesquisa, selecione Indexadores. Selecione o indexador de café recém-criado. Aguarde um minuto e selecione &orarr; Atualize até que o Status indique êxito.

Selecione o nome do indexador para ver mais detalhes.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/edb9bbaa-0519-49e4-a038-674d5d04b2bc)

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/56753078-1e7c-4ee9-995b-f10b38b5124d)

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/c116037c-1ade-4298-b5e3-2f61762c52f5)

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/3a199606-08af-462d-a02f-24d2dbb2c6dd)

## Consultar o índice
Use o Gerenciador de pesquisa para escrever e testar consultas. O explorador de pesquisa é uma ferramenta incorporada no portal do Azure que oferece uma maneira fácil de validar a qualidade do seu índice de pesquisa. Você pode usar o Gerenciador de pesquisa para escrever consultas e revisar resultados em JSON.

Na página Visão geral do serviço de Pesquisa, selecione Gerenciador de pesquisa na parte superior da tela.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/7c1ecc99-d914-471b-a2e0-842a175456cf)

Observe como o índice selecionado é o índice de café que você criou. Abaixo do índice selecionado, altere a exibição para JSON view.

No campo Editor de consultas JSON, copie e cole:

Código
{
    "search": "*",
    "count": true
}

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/e08e1fb5-30b2-4e10-9182-cacb82f74702)

Selecione Pesquisar. A consulta de pesquisa retorna todos os documentos no índice de pesquisa, incluindo uma contagem de todos os documentos no campo @odata.count. O índice de pesquisa deve retornar um documento JSON contendo os resultados da pesquisa.

Agora vamos filtrar por localização. No campo Editor de consultas JSON, copie e cole:
Código
{
 "search": "locations:'Chicago'",
 "count": true
}
Selecione Pesquisar. A consulta pesquisa todos os documentos no índice e filtra por revisões com um local de Chicago. Você deve ver no campo.3@odata.count

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/a9fb560f-5929-4466-b309-bc9014ef2130)


Agora vamos filtrar por sentimento. No campo Editor de consultas JSON, copie e cole:
Código
{
 "search": "sentiment:'negative'",
 "count": true
}
Selecione Pesquisar. A consulta pesquisa todos os documentos no índice e filtra por avaliações com um sentimento negativo. Você deve ver no campo.1@odata.count

Nota Veja como os resultados são classificados por . Esta é a pontuação atribuída pelo mecanismo de pesquisa para mostrar o quanto os resultados correspondem à consulta dada.@search.score

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/6893d9e5-34b0-456a-8004-77268cb2c45b)


Um dos problemas que podemos querer resolver é por que pode haver certas revisões. Vamos dar uma olhada nas frases-chave associadas à avaliação negativa. O que você acha que pode ser a causa da revisão?
Revisar o repositório de conhecimento
Vamos ver o poder do armazenamento de conhecimento em ação. Ao executar o assistente Importar dados, você também criou um repositório de conhecimento. Dentro da loja de conhecimento, você encontrará os dados enriquecidos extraídos pelas habilidades de IA persistem na forma de projeções e tabelas.

No portal do Azure, navegue de volta para sua conta de armazenamento do Azure.

No painel de menu esquerdo, selecione Contêineres. Selecione o contêiner de armazenamento de conhecimento.
