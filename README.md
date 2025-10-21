💸 Desafio Técnico - Backend PicPay

Este projeto foi desenvolvido como parte de um desafio técnico do PicPay, com o objetivo de demonstrar habilidades em desenvolvimento Backend com Java.
O sistema simula funcionalidades básicas de uma plataforma de pagamentos digital, permitindo o cadastro de usuários, transferências entre contas e envio de notificações após as transações, seguindo regras de negócio definidas pelo desafio.


---

🚀 Tecnologias Utilizadas

Java 17

Spring Boot

Spring Data JPA / Hibernate

H2 Database (banco em memória)

Maven

Lombok

RestTemplate (para consumo de APIs externas)

JUnit / Mockito (para testes)



---

🧠 Sobre o Desafio

O PicPay Simplificado é uma plataforma de pagamentos simplificada onde é possível depositar e realizar transferências de dinheiro entre usuários.
Existem dois tipos de usuários no sistema:

👤 Usuário Comum – Pode enviar e receber dinheiro

🏪 Lojista – Pode apenas receber transferências



---

⚙️ Funcionalidades Implementadas

✅ Cadastro de usuários (com validação de CPF e e-mail únicos)
✅ Realização de transferências entre contas
✅ Verificação de saldo antes da transferência
✅ Integração com serviço externo de autorização:

> GET https://util.devi.tools/api/v2/authorize
✅ Envio de notificações simuladas após transferências:
POST https://util.devi.tools/api/v1/notify
✅ Persistência em banco de dados H2
✅ Estrutura RESTful e boas práticas de arquitetura




---

🔄 Regras de Negócio

Lojistas não podem enviar dinheiro, apenas receber.

Antes de efetuar a transferência, o sistema verifica se o usuário tem saldo suficiente.

A transferência só é concluída se o serviço externo de autorização retornar aprovação.

Caso ocorra alguma falha, a operação é revertida (transação atômica).

Após uma transferência bem-sucedida, o sistema envia uma notificação (mock da API externa).



---

📡 Endpoints Principais

🔸 Criar Usuário

POST /users

{
  "fullName": "Jonas Elias",
  "cpf": "12345678901",
  "email": "jonas@email.com",
  "password": "123456",
  "balance": 1000.00,
  "type": "COMMON"
}

🔸 Realizar Transferência

POST /transfer

{
  "value": 100.0,
  "payer": 1,
  "payee": 2
}

🔸 Listar Usuários

GET /users


---

🧩 Estrutura do Projeto

src
├── main
│   ├── java
│   │   └── com.picpay.desafio
│   │       ├── controller      # Endpoints REST
│   │       ├── service         # Regras de negócio
│   │       ├── model           # Entidades (User, Transaction)
│   │       ├── repository      # Acesso ao banco de dados
│   │       └── dto             # Objetos de transferência de dados
│   └── resources
│       ├── application.properties
│       └── data.sql (opcional para carga inicial)
└── test
    └── ... (testes unitários)


---

🧪 Testes

Os testes foram desenvolvidos com JUnit 5 e Mockito, cobrindo:

Criação de usuários

Fluxo de transferência

Validação de saldo

Integração com os serviços externos simulados


Para executar os testes:

mvn test


---

💾 Banco de Dados H2

A aplicação utiliza um banco em memória H2 para simplificar a execução.
Após iniciar a aplicação, você pode acessar o console em:

🔗 http://localhost:8080/h2-console

JDBC URL: jdbc:h2:mem:picpay

Usuário: sa

Senha: (em branco)



---

🐳 Docker (opcional)

Se desejar rodar via Docker:

docker build -t picpay-desafio .
docker run -p 8080:8080 picpay-desafio


---

🧾 Considerações Finais

Este projeto tem como objetivo demonstrar boas práticas de desenvolvimento Backend, aplicando conceitos de arquitetura limpa, SOLID, e integração com serviços externos.
A proposta foi desenvolvida com foco em clareza, escalabilidade e manutenibilidade do código, conforme os critérios do desafio técnico do PicPay.


---

👨‍💻 Autor

Vitor Melo
📧 vitordutra1125@gmail.com
