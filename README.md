# Azure Cognitive Search: Utilizando AI Search para indexação e consulta de Dados

Criar um recurso de Pesquisa de IA do Azure
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

Criar um recurso de serviços de IA do Azure
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

