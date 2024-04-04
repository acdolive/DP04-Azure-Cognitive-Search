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

Habilite o acesso anônimo de blob
![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/4bc9881c-00c2-4cfe-9055-538cbbe3ab06)


## Carregar documentos no Armazenamento do Azure
No painel de menu esquerdo, selecione Contêineres.

![image](https://github.com/acdolive/DP04-Azure-Cognitive-Search/assets/162451624/2f95dc9a-7763-4da0-a616-f1b87be9b68e)

Selecione + Contêiner. Um painel do lado direito é aberto.


Insira as seguintes configurações e clique em Criar:
Nome: café-comentários
Nível de acesso público: Contêiner (acesso de leitura anônimo para contêineres e blobs)
Avançado: sem alterações.
Em uma nova guia do navegador, baixe as revisões de café compactadas do e extraia os arquivos para a pasta de comentários.https://aka.ms/mslearn-coffee-reviews

No portal do Azure, selecione seu contêiner de avaliações de café. No contêiner, selecione Carregar.

