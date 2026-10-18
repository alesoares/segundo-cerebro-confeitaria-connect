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
