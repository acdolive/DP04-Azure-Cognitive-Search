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
