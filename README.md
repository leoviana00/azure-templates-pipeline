# azure-templates-pipeline

- Repositório utilizado para armazenar templates pipeline ci-cd azure devops

## Pipeline CI

- Etapas do pipeline `ci-steps-template.yml`

        - Crie e envie a imagem do docker
        - Instala o cliente Helm
        - Autenticar no ACR
        - Cria e envia o gráfico do Helm para o ACR.
        - Cria variables.jsonque contém a versão do gráfico do Helm recém-criada. Que usaremos para obter a versão correta do gráfico durante o CD.
        - Copie alguns arquivos adicionais para o artefato. Que podemos usar para substituir os valores do gráfico do Helm.

## Pipeline CD

- Etapas do pipeline `cd-steps-template.yml`

        - Autentique-se no Azure usando as credenciais principais de serviço
        - Defina o cluster AKS especificado como o contexto.
        - Instala o cliente Helm
        - Autentique o ACR com as credenciais do ACR 
        - Extraia a versão do gráfico do Helm que precisa ser instalada
        - Puxa o gráfico do Helm e o instala (ou atualiza). Aqui, estamos substituindo o repositório de imagens do gráfico para nosso repositório ACR.

## Estrutura

![](./img/estrutura-cicd.jpg)

