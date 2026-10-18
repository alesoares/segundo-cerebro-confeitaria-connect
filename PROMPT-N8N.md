# Desafio Criativo: Planejando Automações com n8n Através de Prompts Estruturados

Este arquivo documenta a construção do prompt mestre para geração do workflow de monitoramento de dados da **Confeitaria Connect**, integrando a API Java local ao cluster de banco de dados em nuvem.

---

## 📋 Passo 1: Definição do Escopo e Objetivos

* **Processo:** Captura automatizada de novos cadastros de clientes efetuados via Single Page Interface (Next.js) e processados pela API Spring Boot.
* **Usuário Responsável:** Equipe de Logística e Gestão de Delivery (Alessandro).
* **Resultado Desejado:** Validar de forma síncrona o raio de cobertura do pedido com foco restrito no bairro do Tatuapé (Zona Leste), disparando notificações instantâneas no painel gerencial sem onerar a memória RAM do servidor.

---

## 🏢 Passo 2: Contextualização e Definição de Regras Negociais

* **Ambiente Técnico:** Microsserviço Java rodando na porta `8083`, conectado ao cluster PostgreSQL na AWS e Front-end em contêiner Docker na porta `3003`.
* **Regra de Ouro (Filtro Geográfico):** A automação deve realizar uma validação do tipo *Case-Sensitive* no campo string `bairro`. Se o conteúdo for exatamente igual a `"Tatuapé"`, o fluxo prossegue. Caso contrário, o registro é classificado como fora do raio de entrega de doces finos.
* **Restrição de Hardware:** Toda a volumetria de dados de teste (carteira enxuta de 20 clientes fixos) deve trafegar de forma leve, priorizando estruturas nativas para evitar estouro de buffers na hospedagem em nuvem gratuita.

---

## 🧱 Passo 3: O Prompt Mestre Estruturado

### Modelo Adaptado e Preenchido

Atue como um especialista em N8N.

Crie uma automação para monitorar e registrar novos cadastros de clientes efetuados via API Java (Spring Boot) no banco de dados.

Público:
Alessandro (Operador do Painel ADM) e equipe de logística do delivery.

Ferramentas envolvidas:
Next.js (Front-end), API Spring Boot (Backend), PostgreSQL (AWS Neon) e N8N Workflow Engine.

Fluxo:
1. Receber o evento de cadastro via Webhook disparado pela API na porta 8083.
2. Ler a string contendo os dados do cliente (Nome, E-mail, Telefone, Endereço).
3. Filtrar e validar de forma síncrona se a entrega pertence à região de cobertura.

Regras:
* A validação do campo "bairro" deve ser estritamente Case-Sensitive, buscando o valor exato "Tatuapé".
* Registros com campos em branco ou e-mails duplicados devem ser bloqueados e retornar o status "INVALID".
* Consumo máximo de memória RAM do fluxo deve ser mantido no chão, otimizando o tráfego de dados na nuvem gratuita.

Explique quais nós do N8N devem ser utilizados e a lógica de funcionamento do workflow.
