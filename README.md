# SpringBoot com Mensageria

Esse BackEnd usa mensageria para fazer o envio de emails.

## Requisitos

- **Java 17**
- **IDE STS (Spring Tool Suite)**
- **Conta no CloudAMQP (usar RabbitMQ)**
- **Servidor SMTP Gmail**
- **MySQL**

## Primeiros Passos

### 1. Clonar o Repositório

Clone o repositório ou baixe o arquivo ZIP do projeto e descompacte-o no seu workspace da IDE STS:

```bash
git clone https://github.com/Eduardogarccia/emailSender-mensageria-springBoot.git
```

## 2. Iniciar a Aplicação

Crie o database email2 no MySQL

Abra a IDE STS, importe o projeto e inicie a aplicação com a opção **Run As Spring Boot App**.

## 3. Testar

Configure uma chave de acesso para o email que será usado para envio nesse link: https://support.google.com/accounts/a...

Atualize o application.properties:
```
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=EMAIL CONFIGURADO
spring.mail.password=CHAVE DE ACESSO GERADA
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
```
Crie uma conta no CloudAMQP, crie uma nova instância e use a URL gerada.

Atualize o application.properties:
```
spring.rabbitmq.addresses=URL GERADA
spring.rabbitmq.queue=ms.email
```
### NO RABBITMQ MANAGEMENT:

Vá em publish message e passe o corpo da requisição no payload.
Exemplo:
```
{
    "ownerRef": "Eduardo",
    "emailFrom": "dududutragarcia@gmail.com",
    "emailTo": "joseeduardo.garccia@gmail.com",
    "subject": "teste 2 mensageria",
    "text": "Olá isso eh somente um teste de menssageria" 
}
```

O email foi enviado usando mensageria e agora você ja pode ver os dados na tabela email2.



