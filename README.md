# Analisador de Cartas da Steam

[Download](https://github.com/o-giu/analisador-de-cartas-da-steam/releases)

**Nota:** $\textcolor{red}{Originalmente,\ fiz\ só\ para\ mim,\ mas\ decidi\ compartilhar\ caso\ seja\ útil\ para\ mais\ alguém.}$ <br>**Sem planos de suporte ou tradução**. Fique à vontade caso quiser utilizar.<br>
Farm de cartas da Steam? Você ficaria surpreso com o tanto de grana que eu faço com isso! :)<br>
Este aplicativo foi criado para otimizar o farm de cartas colecionáveis na Steam e informar quais jogos você precisa comprar ou substituir (Caso tiver pego algum jogo de "graça") para famar. Ele identifica jogos com drops (mesmo os "escondidos"), jogos pagos adicionados de "graça" na sua conta que deveriam te dar cartas, etc. Gerencia o progresso do seu farm e integra-se com lojas de pontos da Twitch para encontrar outros jogos com cartas que você ainda não possui.<br>

![image](https://github.com/user-attachments/assets/3a61bb45-a24b-4893-9728-0a68a7349391)
![image](https://github.com/user-attachments/assets/f38e2715-fc4f-4f06-8492-20f3b81208cf)
![image](https://github.com/user-attachments/assets/d43ddeb1-fad9-431c-b577-37debbebaa6c)
![image](https://github.com/user-attachments/assets/b6b2b0cb-84f3-49ea-be51-8771ba02f650)
![image](https://github.com/user-attachments/assets/08fa298a-21e1-47c0-a911-1a941a23fc75)
![image](https://github.com/user-attachments/assets/beecd948-19fc-4095-959d-33a62d4ac7e0)

## Pré-Requisitos

Antes de começar, você precisará de três coisas:

1.  **Steam API Key**: Uma chave de acesso para que o programa possa consultar a API da Steam em seu nome. (Lembre-se de não divulgar sua APIKEY, ela é apenas sua) (O app aceita a APIKEY de qualquer conta steam, ela servirá apenas para ter acesso a algumas variáveis da steam, como: lista de jogos dos usuários.)
    *   Você pode obter uma aqui: [https://steamcommunity.com/dev/apikey](https://steamcommunity.com/dev/apikey)
2.  **Seu Steam ID**: O identificador único da sua conta Steam. Pode ser sua URL personalizada (ex: `meu_nick_legal`) ou seu SteamID64 (um número de 17 dígitos). (O APP irá verificar o ID e ver a lista de jogos deste ID)
    *   Você pode encontrar o seu aqui: [https://steamdb.info/calculator/](https://steamdb.info/calculator/)
3.  **Arquivo CSV de Jogos com Cartas**: Um arquivo no formato `.csv` contendo a lista de todos os jogos na Steam que possuem cartas colecionáveis e os appids de cada jogo.
    *   O arquivo .csv que eu disponibilizo já vem com todos os nomes dos jogos e os seus appids. Sempre irei atualizar o arquivo .csv com os novos jogos adicionados na steam que possuem cartas com a data atual.

## Passo a Passo Inicial

1.  Abra o aplicativo.
2.  Preencha os campos na seção **Configuração**.
3.  Clique no botão **Analisar Biblioteca**. (Caso a conexão não for estabelecida com a API, espere e tente novamente.)
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
| **Botão: Gerenciar Drops Concluídos** | Abre uma nova janela para você gerenciar a lista de jogos cujos drops de cartas você já considera "concluídos". (Estes jogos podem ser encontrados na página de insignias da Steam e depois clicando no botão **Informações Sobre Pacotes Bônus**, copie todos os nomes e cole no campo dos jogos concluídos.) |

### Abas de Resultados

Após a análise, os resultados são divididos em várias abas para facilitar a visualização.

| Aba | O que ela mostra? |
| :--- | :--- |
| **Informações** | Um console de log que exibe o progresso da análise, mensagens de erro e outras informações úteis. |
| **Loja de Pontos** | Uma ferramenta para analisar lojas do StreamElements. Cole a URL completa da loja, clique em "Analisar Loja" e o app listará apenas os **jogos com cartas que você não possui**, ordenados por custo em pontos. |
| **Jogos que Possuo** | Uma lista de todos os jogos da sua biblioteca que têm cartas colecionáveis. |
| **Jogos que Não Possuo** | Uma lista de jogos com cartas que **não** estão na sua biblioteca. Os preços são buscados automaticamente. Você pode ocultar jogos grátis, atualizar os preços manualmente e buscar por jogos expecificos. |
| **Drops Pendentes de Cartas** | Mostra os jogos que você possui e que têm cartas, mas que **não** foram marcados como "concluídos" no gerenciador. É a sua lista de jogos para "farmar" ou comprar. Você também pode buscar por jogos expecificos. |

**Observação:** Nas abas "Jogos que Não Possuo" e "Drops Pendentes", você pode clicar no cabeçalho das colunas para ordenar a lista.<br>
**Observação:** Durante a busca, caso existir nomes iguais, uma lista com todos os nomes iguais será mostrada, pedindo para você escolher um.<br>
**Problemas:** Alguns jogos banidos pela Steam ou com status de perfil limitado, podem aparecer nas tabelas erradas. Adicione eles de forma manual.

### Gerenciador de Jogos Concluídos

**Adicione seus jogos concluídos na lista para a tabela funcionar corretamente.**
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
