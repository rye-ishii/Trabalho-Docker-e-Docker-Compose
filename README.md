# Docker e Docker Compose

## O que é Docker?
O Docker é um sistema de virtualização capaz de executar sua aplicação independente de onde o programador esteja desenvolvendo. A aplicação fica contida dentro de um container, com todas as funcionalidades necessárias para rodar sem depender de instalações e requisitos adicionais.

Diferente de uma máquina virtual, o Docker consegue funcionar sem precisar instalar um sistema operacional próprio, pois utiliza o do hospedeiro. Cada container possui uma parte dos recursos da máquina (memória, CPU etc), realiza a separação de redes e mantém as variáveis do sistema. Sendo assim, o Docker acaba se tornando uma solução mais leve, tendo em vista que não é necessário baixar dependências e vários sistemas operacionais. Também não tem mais a desculpa de que "na minha máquina funciona", já que o Docker roda com o ambiente configurado e pronto, sem necessidade de outras pré-definições.

A distinção entre Docker e container é que o Docker é o sistema de virtualização em si, enquanto containers são uma espécie de pacote que contém a aplicação com uma parcela dos recursos da máquina, da rede e compartilha o sistema operacional do hospedeiro.

## Imagem vs Container
A imagem contém todas as informações do ambiente, é como uma foto estática que inclui todas as dependências, bibliotecas, códigos e arquivos necessários para executar o container. É imutável, utilizada somente para leitura, e caso haja alterações, é necessário criar uma nova imagem. É utilizada para armazenar os detalhes de configuração da aplicação.

O container é uma instância de uma imagem em execução. É mutável e suas alterações são isoladas àquele container específico, sem afetar a imagem associada. Nele ficam situadas as aplicações com todas as funcionalidades necessárias, sem precisar configurar ou alterar o sistema operacional, pois o container é vinculado à máquina do hospedeiro.

Quando se inicia um novo container, é iniciado um processo na máquina hospedeira, que pode ser uma máquina física ou uma VM. Assim, é possível ter várias instâncias da mesma imagem rodando simultaneamente, como por exemplo cinco containers distintos na mesma máquina hospedeira.

## O que é um Dockerfile?
O Dockerfile é um arquivo presente dentro da aplicação, funciona como um projeto de arquitetura que define como ela deve funcionar. Nele estão contidas todas as informações necessárias para gerar uma imagem. Em outras palavras, o Dockerfile orienta como a imagem deve ser executada e como o container deve se comportar, servindo como um manual de instruções.

## O que é Docker Compose?
O Docker Compose é uma ferramenta que simplifica o processo de orquestração de containers. Com ele, é possível definir, iniciar e gerenciar vários containers utilizando apenas um arquivo de configuração, permitindo que o desenvolvedor execute múltiplos serviços de forma organizada.

De maneira simplificada, imagine que você possua uma aplicação frontend com Angular, backend em Node.js e um banco de dados no MySQL. Para cada um deles existe um container. Subir e orquestrar os três manualmente se tornaria uma atividade exaustiva, mas com o Docker Compose esse processo é muito mais rápido e prático.

Utilizamos um arquivo YAML(define uma sequência de ações e configurações de maneira fácil de compreenssão) para configurar os serviços desses containers. Com um único comando, criamos e inicializamos todos os serviços conforme a configuração definida. Ao utilizar o Docker Compose, basicamente seguimos três etapas:

- definir o ambiente da aplicação com o Dockerfile para que possa ser reproduzido em qualquer máquina;
- definir os serviços que compõem a aplicação em um arquivo YAML do Docker Compose para que possam ser executados em um ambiente isolado;
- executar o comando `docker compose up`, responsável por inicializar e executar toda a aplicação.

## Exemplo Prático

O `docker compose up` constrói, recria e anexa containers de um serviço, além de iniciar qualquer serviço vinculado. O comando exibe no terminal tudo que cada container está fazendo em tempo real. Para interromper, basta fechar o terminal ou apertar `Ctrl + C`. Caso queira rodar em segundo plano sem travar o terminal, utilize `docker compose up --detach`.

Se o desenvolvedor realizou alguma alteração no projeto após a última execução, o Docker automaticamente para e recria os containers com as mudanças. Caso prefira recriar os containers do zero, utilize a flag `--force-recreate`. Se na saída ocorrer algum erro, o código retornado é `1`, enquanto containers encerrados normalmente retornam `0`.


## Referências
- APRENDA DOCKER DO ZERO | TUTORIAL COMPLETO COM DEPLOY - Fernanda Kipper: https://youtu.be/DdoncfOdru8?si=UMb5BWBqP1LRiepQ
- AMAZON WEB SERVICES (AWS): https://aws.amazon.com/pt/compare/the-difference-between-docker-images-and-containers/
- O que é Dockerfile? (A receita para criação de containers) - AlgaWorks https://youtu.be/5QGexrfqu60?si=HQowHJ4oeOa9So7F
- Medium - Hugo Habbema: https://medium.com/@habbema/docker-compose-8c16d02585b4
- Dockerdocs: https://docs.docker.com/reference/cli/docker/compose/up/