1) Instalação o SonarQube, subindo o seu container. Você pode se guiar pelo script que o instrutor seguiu durante a aula:
~~~bash
# Subindo o container com o Sonarcube
  Na máquina devops (Vagrant): docker run -d --name sonarqube -p 9000:9000 sonarqube:lts
  # Acessar: http://192.168.33.10:9000
    Usuário: admin
    Senha: admin
    Name: jenkins-todolist
        Provide a token: enkins-todolist e anotar o seu token
        Run analysis on your project > Other (JS, Python, PHP, ...) > Linux > django-todo-list
        # Copie o shell script fornecido

sonar-scanner \
  -Dsonar.projectKey=enkins-todolist \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://192.168.33.10:9000 \
  -Dsonar.login=<seu token>
~~~
2) Crie um job para o escaneamento do seu código. Você pode se guiar pelo script que o instrutor seguiu durante a aula:
~~~bash
# Criar um job para Coverage com o nome: todo-list-sonarqube
    # Gerenciamento de código fonte > Git
        git: git@github.com:alura-cursos/jenkins-todo-list.git (Selecione as mesmas credenciais)
        branch: master
        Pool SCM: * * * * *
        Delete workspace before build starts
        Execute Script:

    # Build > Adicionar passo no build > Executar Shell

        #!/bin/bash
        # Baixando o Sonarqube
        wget https://s3.amazonaws.com/caelum-online-public/1110-jenkins/05/sonar-scanner-cli-3.3.0.1492-linux.zip

        # Descompactando o scanner
        unzip sonar-scanner-cli-3.3.0.1492-linux.zip

        # Rodando o Scanner
        ./sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner   -X \
          -Dsonar.projectKey=jenkins-todolist \
          -Dsonar.sources=. \
          -Dsonar.host.url=http://192.168.33.10:9000 \
          -Dsonar.login=<seu token>
~~~
