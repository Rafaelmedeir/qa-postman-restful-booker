# Testes de API na Prática - Restful-Booker com Postman

## Sobre o Projeto
Este é um projeto prático desenvolvido para consolidar meus estudos em **Quality Assurance (QA)** e automação de testes de API. Utilizei a API pública Restful-Booker para simular o dia a dia de testes em um ambiente real.

O objetivo principal foi construir um fluxo de testes **End-to-End (E2E)**, validando todas as etapas do ciclo de vida de uma reserva de hotel (Criar, Ler, Atualizar e Deletar - CRUD), garantindo que os dados conversam corretamente entre si sem precisar de intervenção manual.

## Tecnologias Utilizadas
* **Postman:** Ferramenta principal para criação das requisições e execução automatizada da suíte de testes usando o Collection Runner.
* **JavaScript:** Utilizado nas abas de Pre-request Scripts e Tests para criar validações automáticas e manipular variáveis.
* **Restful-Booker:** API de laboratório usada como ambiente de testes.

## O Fluxo de Testes (Passo a Passo)
Configurei a Collection para rodar de forma 100% encadeada. Isso significa que o Postman captura as informações de uma resposta e já guarda para usar na requisição seguinte. O fluxo segue esta ordem:

1. **Autenticação (POST):** Geração de um token de acesso que é salvo automaticamente nas variáveis da Collection.
2. **Criação da Reserva (POST):** Envio dos dados da reserva e captura do bookingid gerado pelo servidor.
3. **Atualização Completa (PUT):** Uso do token de autorização para reescrever os dados da reserva.
4. **Atualização Parcial (PATCH):** Alteração de apenas alguns campos (nome e sobrenome). Aqui utilizei scripts pré-requisição para gerar dados dinâmicos e validar se a API realmente salvou o que foi enviado.
5. **Exclusão (DELETE):** Apagamento da reserva utilizando as variáveis salvas nos passos anteriores.
6. **Verificação de Limpeza (GET):** Uma última chamada buscando o ID apagado, esperando intencionalmente receber um erro 404 Not Found, provando que a exclusão funcionou de verdade.

## Bug Encontrado e Documentado
Como a API Restful-Booker é um ambiente de treinamento, ela possui algumas falhas intencionais para testar a atenção do QA. Durante a automação, peguei a seguinte situação:

* **Erro de Status Code no DELETE:** Quando excluímos uma reserva com sucesso, a API retorna o Status 201 Created (Criado). Na arquitetura REST, isso está incorreto, pois nada foi criado. O ideal seria retornar 200 OK ou 204 No Content. Configurei meu script de teste para falhar de propósito e evidenciar esse desvio no relatório do Postman.

## Como rodar este projeto
1. Faça o clone ou baixe este repositório.
2. Importe o arquivo .json da Collection para o seu Postman.
3. Clique nos três pontinhos da Collection e selecione Run (Executar).
4. Veja todas as validações passando automaticamente!

## Autor
**Rafael Medeiros**
*Analista de QA Júnior*

[LinkedIn](https://www.linkedin.com/in/rafaelmedeir/) | [GitHub](https://github.com/Rafaelmedeir) | [E-mail](mailto:rafael.medeir.rm@gmail.com)
