# Desafio 3 - Criando um repositório no GitLab e uma pipeline que execute um "echo Hello World".
## Requisitos:
Ter uma conta no GitLab <br>
Ter o Git instalado em seu computador <br>
- Acesse a sua conta do GitLab, vá em projetos, selecione novo projeto, escolha a opção **criar projeto em branco**
- Na URL do projeto, o Gitlab vai pedir que você atribua  o projeto a um grupo ou usuário
- Dê um nome para o seu projeto
- Em nível de visibilidade, escolha **público**
- Em configurações do projeto, você pode inicializar com um README
- Clique em criar projeto
- No seu computador, crie uma pasta. Clique em cima dessa pasta com o botão direito e escolha abrir com Code
- No VsCode, crie o arquivo **.gitlab-ci.yml

- E coloque o script abaixo:<br>
    ´´´
    stages:
     - hello_world

    hello_world_job:
     stage: hello_world
     script:
     - echo "Hello, World!"
    ´´´
- Temos um estágio chamado hello_world com um trabalho chamado hello_world_job. Quando este pipeline é acionado, ele executará um script que exibirá "Hello, World!".

- Faça um push para seu repositório GitLab com esse novo arquivo **.gitlab-ci.yml**:<br>

    ´´´
    git remote add origin <o_caminho_do_seu_repositorio_no_gitlab>
    ´´´

    ´´´
    git push -u origin main
    ´´´

- Acesse o GitLab: 
- Acesse seu projeto no GitLab.<br>
Obs.: Habilite a configuração **Auto DevOps enable**<br>
- Vá para a seção **CI/CD** e clique em visualizar<br>
- Acompanhe o Progresso: <br>
- Você verá o pipeline sendo concluído e, quando estiver concluído, deverá ver a mensagem **"Hello, World!"** impressa na saída do trabalho.


# Desafio 4 - Criando uma pipeline que faça o deploy do NGINX e que rode automaticamente após cada alteração.

- Repita o passo a passo do desafio 3 acima e no VsCode crie o arquivo **.gitlab-ci.yml** com o seguinte script:

    ´´´
     - deploy

    deploy:
      stage: deploy
      script:
        - apt-get update -qy
        - apt-get install -y nginx
        - service nginx start
        - nginx -v
    ´´´

- Faça um push para seu repositório GitLab:

    ´´´
    git add .
    ´´´
    ´´´
    git commit -m "Adicionar arquivo .gitlab-ci.yml"
    ´´´
    ´´´
    git push origin main
    ´´´

- Acesse o GitLab: 
- Acesse seu projeto no GitLab.<br>
Obs.: Habilite a configuração **Auto DevOps enable**<br>
- Vá para a seção **CI/CD´** e clique em visualizar<br>
- Acompanhe o Progresso: <br>