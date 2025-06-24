# Analisador de Cartas da Steam

Parece meio doido, mas eu faço uma bela grana na steam com farm de cartas/pacotes e skins, então fiz isso.
Fiz este app apenas para mim, mas fique a vontade para usar se quiser. **Por enquanto eu não pretendo dar suporte ou traduzir o app**.
A intenção é agilizar a busca de jogos com cartas e me ajudar durante os meus farms de cartas.
O app identifica quais jogos possuem cartas colecionáveis (mesmo quando o jogo não avisa isso na página da loja) e gerencia os que ainda têm drops pendentes na sua conta.
Jogos pegos de "graça" não dropam cartas, então o app também consegue achar quais desses jogos você possui.
Além disso, ele possui uma ferramenta para analisar lojas de pontos de canais da Twitch (via StreamElements) e encontrar jogos com cartas para você poder comprar com pontos, assim eu não preciso ficar caçando quais jogos tem drops ou não e quais eu ainda não tenho.

## Pré-Requisitos

Antes de começar, você precisará de três coisas:

1.  **Steam API Key**: Uma chave de acesso para que o programa possa consultar a API da Steam em seu nome. (Pode ser a APIKEY de qualquer conta steam, ela servirá apenas para ter acesso a algumas variáveis da steam, como: lista de jogos dos usuários.)
    *   Você pode obter uma aqui: [https://steamcommunity.com/dev/apikey](https://steamcommunity.com/dev/apikey)
2.  **Seu Steam ID**: O identificador único da sua conta Steam. Pode ser sua URL personalizada (ex: `meu_nick_legal`) ou seu SteamID64 (um número de 17 dígitos). (O APP irá verificar o ID e ver a lista de jogos deste ID)
    *   Você pode encontrar o seu aqui: [https://steamdb.info/calculator/](https://steamdb.info/calculator/)
3.  **Arquivo CSV de Jogos com Cartas**: Um arquivo no formato `.csv` contendo a lista de todos os jogos na Steam que possuem cartas colecionáveis e os appids de cada jogo.
    *   Use o arquivo .csv que eu coloquei aqui. Sempre irei atualizar o arquivo .csv com os novos jogos adicionados na steam que possuem cartas com a data atual.

## Passo a Passo Inicial

1.  Abra o aplicativo.
2.  Preencha os campos na seção **Configuração**.
3.  Clique no botão **Analisar Biblioteca**.
4.  Aguarde a análise ser concluída. Os resultados aparecerão nas abas correspondentes.

## Visão Geral das Funcionalidades

### Tela Principal e Configuração

A tela inicial é onde você insere suas informações e inicia a análise.

| Componente | Descrição |
| :--- | :--- |
| **Sua Steam API Key** | Cole a sua chave da API da Steam aqui. Ela será exibida como asteriscos (`*`) por segurança. |
| **Seu Steam ID** | Insira sua URL personalizada da Steam ou seu SteamID64. |
| **Arquivo CSV** | Clique em "Procurar..." para selecionar o arquivo CSV com a lista de jogos que dropam cartas. |
| **Botão: Analisar Biblioteca** | O botão principal. Ao clicar, o app irá: buscar seus jogos, compará-los com a lista do CSV e popular as abas de resultados. |
| **Botão: Gerenciar Drops Concluídos** | Abre uma nova janela para você gerenciar a lista de jogos cujos drops de cartas você já considera "concluídos". |

### Abas de Resultados

Após a análise, os resultados são divididos em várias abas para facilitar a visualização.

| Aba | O que ela mostra? |
| :--- | :--- |
| **Informações** | Um console de log que exibe o progresso da análise, mensagens de erro e outras informações úteis. |
| **Loja de Pontos** | Uma ferramenta para analisar lojas do StreamElements. Cole a URL completa da loja, clique em "Analisar Loja" e o app listará apenas os **jogos com cartas que você não possui**, ordenados por custo em pontos. |
| **Jogos que Possuo** | Uma lista de todos os jogos da sua biblioteca que têm cartas colecionáveis. |
| **Jogos que Não Possuo** | Uma lista de jogos com cartas que **não** estão na sua biblioteca. Os preços são buscados automaticamente. Você pode ocultar jogos grátis, atualizar os preços manualmente e buscar por jogos expecificos. |
| **Drops Pendentes de Cartas** | Mostra os jogos que você possui e que têm cartas, mas que **não** foram marcados como "concluídos" no gerenciador. É a sua lista de jogos para "farmar" ou comprar. Você também pode buscar por jogos expecificos. |

**Observação:** Nas abas "Jogos que Não Possuo" e "Drops Pendentes", você pode clicar no cabeçalho das colunas para ordenar a lista.
**Observação:** Durante a busca, caso existir nomes iguais, uma lista com todos os nomes iguais será mostrada, pedindo para você escolher um.

### Gerenciador de Jogos Concluídos

Esta janela, acessada pelo botão "Gerenciar Drops Concluídos", permite que você mantenha uma lista personalizada de jogos cujos drops de cartas já foram esgotados. Isso evita que eles apareçam na aba "Drops Pendentes".
Na sua Steam vá na página **Insignias** e clique no botão **Informações Sobre Pacotes Bônus** , selecione todos os jogos da lista e adicione eles em massa aos drops pendentes do app.
Alguns jogos possuem nomes diferentes de acordo com a sua região, mas o app irá tentar buscar por esses nomes junto com o appid de cada jogo.
Caso ele não detectar alguns jogos, uma lista desses jogos será informada para você adicionar eles manualmente.

| Funcionalidade | Descrição |
| :--- | :--- |
| **Lista de Jogos** | Exibe todos os jogos que você marcou como concluídos. |
| **Adicionar Manualmente** | Permite adicionar um jogo à lista informando seu nome e App ID. |
| **Adicionar em Massa** | Permite colar uma lista de nomes de jogos ou App IDs (um por linha) para adicioná-los de uma só vez. Na sua Steam vá na página **Insignias** e clique no botão **Informações Sobre Pacotes Bônus** , selecione todos os jogos da lista e adicione eles em massa aos drops pendentes do app. Caso ele não detectar alguns jogos, uma lista desses jogos será informada para você adicionar eles manualmente. |
| **Remover Selecionados** | Remove os jogos que você selecionou na lista. Para remover em massa use CTRL+A para selecionar tudo de uma só vez ou CTRL+clique para selecionar múltiplos jogos de forma expecifica. |
| **Busca** | Busca por jogos expecificos na lista. |
| **Salvar e Fechar** | Salva suas alterações no arquivo `jogos_concluidos.json` e fecha a janela, atualizando a aba "Drops Pendentes". |

## Arquivos Gerados

O aplicativo cria um arquivo no mesmo diretório onde ele é executado:

*   `jogos_concluidos.json`: Este arquivo armazena a lista de jogos que você marcou como concluídos. Você pode fazer backup deste arquivo para não perder sua lista.
