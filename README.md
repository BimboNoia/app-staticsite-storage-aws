# Armazenamento AWS S3 (Site estático)

O objetivo desta atividade é explorar na prática os conceitos de armazenamento utilizando o serviço AWS Simple Storage Service (S3). 

O Amazon S3 pode ser utilizado para hospedar sites estáticos.

Hospedar um site estático no Amazon S3 proporciona um site altamente escalável e de alto desempenho por uma fração do custo de um servidor Web tradicional.

Para hospedar um site estático no Amazon S3, configure um bucket do Amazon S3 para hospedagem e faça upload do conteúdo do seu site.

> Referência: [https://docs.aws.amazon.com/pt_br/AmazonS3/latest/userguide/WebsiteHosting.html](https://docs.aws.amazon.com/pt_br/AmazonS3/latest/userguide/WebsiteHosting.html)<br><br>

## Target architecture

![Notifier](/images/target_architecture.png)<br><br>

## Passo a passo

1. Faça login no AWS Console.

2. Em **Serviços** selecione **S3**.

3. Selecione o botão **Criar bucket**.

4. Na tela de criação de bucket preencha com as informações abaixo e no final da tela clique em  **Criar bucket**.

   > **ATENÇÃO !!!** Substitua o texto **Bucket-Name** por um nome de Bucket qualquer. Mantenha as demais opções padrões. 

   - **nome**: `Bucket-Name`
   - **região**: Norte da Virgínia (us-east-1)
   - **ACLs desabilitadas (recomendado)**: selecionado
   - **Bloquear todo o acesso público**: desabilitado
   - **Desativar o bloqueio de todo o acesso público ...:** selecionado
   - **Versionamento de Bucket**: habilitado<br><br>

5. Clique sobre o nome do Bucket criado.

6. No menu **Permissões** navegue até **Política do bucket**, clique em **Editar**, preencha com as informações abaixo e clique em **Salvar alterações**.

   > **ATENÇÃO !!!** Substitua o texto **Bucket-Name** pelo nome do bucket utilizado no passo anterior. Mantenha as demais opções padrões. 

    ```
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Principal": "*",
                "Action": "s3:GetObject",
                "Resource": "arn:aws:s3:::Bucket-Name/*"
            }
        ]
    }
    ```   

7. Faça download dos arquivos HTML de exemplo **index.html** e **error.html** do repositório GitHub abaixo.
 
   > GitHub repository: [https://github.com/kledsonhugo/app-static-site-s3/tree/main/app](https://github.com/kledsonhugo/app-static-site-s3/tree/main/app)

8. No menu **Objetos** clique em **Carregar**.

   - Selecione **Adicionar arquivos**
   - Busque pelos arquivos baixados e clique em **Carregar**
   - Clique em **Fechar**<br><br>

9. No menu **Propriedades** navegue até **Hospedagem de Site estático**, clique em **Editar**, preencha com as informações abaixo e clique em **Salvar alterações**.

   - Hospedagem de site estático: `Ativar`
   - Documento de índice: `index.html`
   - Documento de erro opcional: `error.html`<br><br>

10. No menu **Propriedades** navegue até **Hospedagem de Site estático** e clique na url **Endpoint de site de bucket**.

    > **SUCESSO !!!** O sucesso dessa atividade será a abertura de uma página web mostrando o conteúdo do arquivo **index.html**.
