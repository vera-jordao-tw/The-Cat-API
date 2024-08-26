# The-Cat-API
Documentação de APIs


**The Cat API** é uma API pública de gestão de **informações** e **imagens** de gatos, os reis da internet 🐱.  

Com nossas APIs, você pode:

1.  **Criar** novos registros;
2.  **Buscar** registros por ID;
3.  **Excluir** registros.

> ℹ️ O objeto **_images_** armazena os arquivos de gatos enviados. Imagens sem gatos ou   impróprias serão rejeitadas.

# Pré-requisitos

-   **Autenticação**: é **obrigatório** obter a **API Key**. 
Registre-se em https://thecatapi.com/signup para receber a API key por email.
Ela deve ser informada no **header** das chamadas através da variável `x-api-key.`

-   **Path de chamadas**: utilizar o path [https://api.thecatapi.com/v1](https://api.thecatapi.com/v1)
