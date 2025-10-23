# 🇧🇷 **BrasilAPI – Unificando dados públicos do Brasil**

---

## 🧭 1. Introdução

A **BrasilAPI** é uma iniciativa **open source** voltada à unificação e simplificação do acesso a **dados públicos brasileiros**.  
Diversas fontes governamentais disponibilizam APIs, mas com **formatos inconsistentes**, **baixa disponibilidade** e **falta de documentação**.  
O objetivo do projeto é oferecer uma **interface única e padronizada**, de fácil integração e alto desempenho, para consumo desses dados em aplicações modernas.

O projeto surgiu da necessidade da comunidade de desenvolvedores de ter um **ponto central de dados públicos**, com confiabilidade e suporte colaborativo.  

---

## 🎯 2. Objetivos

### 🎯 Objetivo Geral
Construir uma API moderna e aberta que unifique o acesso a dados públicos do Brasil, fornecendo uma camada de abstração sobre fontes governamentais heterogêneas.

### 🎯 Objetivos Específicos
- Criar endpoints padronizados para consumo de dados nacionais.  
- Facilitar o desenvolvimento de aplicações que dependem de dados públicos.  
- Promover a colaboração entre desenvolvedores e órgãos públicos.  
- Fornecer documentação interativa via **OpenAPI**.  
- Garantir performance, segurança e disponibilidade via **Vercel CDN** e **cache interno**.  

---

## 🧱 3. Arquitetura do Sistema

A **BrasilAPI** adota uma arquitetura **modular e escalável**, baseada em **Next.js** e **Node.js**, hospedada na **Vercel** com suporte a **CI/CD** automatizado.

### 🧩 Visão Geral

```bash
Cliente (HTTP Request / gRPC / Webhook)
↓
Next.js / API Gateway / BFF
↓
Serviços Modulares (CEP, CNPJ, DDD, IBGE, etc.)
↓
Fontes Externas (Correios, Receita Federal, etc.)
↓
Cache interno (Redis) e Resposta Unificada
````

### 🔍 Principais Componentes

| Camada                    | Função                                                                    |
| ------------------------- | ------------------------------------------------------------------------- |
| **Frontend (Next.js)**    | Exibição da documentação e interface interativa.                          |
| **Backend (Node.js)**     | Processamento das requisições e integração com fontes externas.           |
| **Serviços Modulares**    | Cada módulo implementa uma integração específica (CEP, CNPJ, IBGE etc).   |
| **Vercel Infrastructure** | Hospedagem, CDN, logs e pipelines automáticos.                            |
| **Cache/CDN**             | Redis + Vercel CDN para otimizar latência e reduzir chamadas redundantes. |

---

## ⚙️ 4. Tecnologias Utilizadas

| Categoria              | Tecnologias                    | Descrição                                                          |
| ---------------------- | ------------------------------ | ------------------------------------------------------------------ |
| **Frontend**           | Next.js, React                 | Framework e biblioteca para UI da documentação.                    |
| **Backend**            | Node.js, Express               | Camada de serviços e integração com APIs externas.                 |
| **Comunicação**        | REST, Webhooks, gRPC           | Diversos padrões para integração com clientes e parceiros.         |
| **Infraestrutura**     | Vercel, Docker                 | Deploy automatizado e ambiente isolado de execução.                |
| **Cache/Persistência** | Redis                          | Armazenamento temporário de respostas e otimização de performance. |
| **Documentação**       | OpenAPI, Swagger UI            | Especificação e visualização das rotas e parâmetros.               |
| **Testes**             | Jest, Supertest                | Validação de endpoints e responses.                                |
| **Monitoramento**      | Vercel Analytics, Sentry       | Observabilidade e métricas de uso.                                 |
| **Segurança**          | Helmet, OAuth2/JWT, Rate Limit | Proteção contra ataques comuns e controle de acesso.               |

---

## 🧠 5. Estrutura do Projeto

```bash
📦 BrasilAPI
 ┣ 📁 src
 ┃ ┣ 📁 services          # Integrações com APIs externas (Correios, IBGE, etc)
 ┃ ┣ 📁 routes            # Definição das rotas (ex: /cep, /cnpj)
 ┃ ┣ 📁 utils             # Funções auxiliares, middlewares e segurança
 ┣ 📁 tests               # Testes unitários e de integração
 ┣ 📁 docs                # Documentação e especificações OpenAPI
 ┣ 📁 public              # Ícones e assets estáticos
 ┣ 📄 vercel.json         # Configuração de deploy
 ┣ 📄 package.json        # Dependências e scripts
 ┣ 📄 README.md           # Este arquivo
```

---

## 🧩 6. Design System

Mesmo sendo uma API, o projeto mantém uma identidade visual consistente em sua documentação oficial.

| Elemento             | Padrão                                                        |
| -------------------- | ------------------------------------------------------------- |
| **Componentização**  | Interface construída com React + Tailwind, focada em clareza. |
| **Cores Principais** | Azul 🇧🇷 (tecnologia e confiança), branco e cinza neutro.    |
| **Tipografia**       | Sans-serif (Inter / Roboto).                                  |
| **Ícones**           | Flat design, minimalista.                                     |
| **Layout**           | Baseado em grid responsivo.                                   |

### ✨ Princípios de Design

* **Clareza:** informações visuais diretas e acessíveis.
* **Consistência:** elementos visuais reaproveitáveis.
* **Acessibilidade:** compatível com leitores de tela e navegação por teclado.

---

## 🌐 7. Endpoints Disponíveis

| Serviço                | Rota Base                 | Descrição                                   |
| ---------------------- | ------------------------- | ------------------------------------------- |
| **CEP**                | `/api/cep/v1/:cep`        | Consulta endereços por CEP.                 |
| **CNPJ**               | `/api/cnpj/v1/:cnpj`      | Retorna informações cadastrais de empresas. |
| **DDD**                | `/api/ddd/v1/:ddd`        | Retorna cidades relacionadas a um DDD.      |
| **IBGE**               | `/api/ibge/municipios/v1` | Retorna municípios e códigos IBGE.          |
| **Feriados Nacionais** | `/api/feriados/v1/:ano`   | Lista feriados nacionais.                   |

💡 Todas as respostas seguem **JSON padronizado** e são documentadas via **OpenAPI (Swagger)**.

---

## 🔁 8. Fluxo de Requisições

```bash
1. Cliente realiza chamada (REST/gRPC/Webhook).
2. Sistema identifica o módulo correspondente.
3. Requisições simultâneas a múltiplas fontes externas.
4. Respostas são padronizadas e cacheadas no Redis.
5. Resultado é entregue via CDN Vercel.
```

---

## 🧪 9. Testes, Qualidade e Observabilidade

A qualidade do código é garantida por **testes automatizados**, **CI/CD**, e monitoramento contínuo.

### 🧰 Stack de Testes

```bash
- Jest: testes unitários e mocks.
- Supertest: simulação de chamadas HTTP reais.
- Coverage mínimo: 90% nos módulos críticos.
```

### ✅ Critérios de Qualidade

```bash
- Padrão de código com ESLint + Prettier.
- PRs revisados por múltiplos colaboradores.
- Testes automatizados em GitHub Actions.
```

### 📊 Observabilidade

```bash
- Logs estruturados e métricas via Sentry.
- Vercel Analytics para monitoramento de uso.
- Alertas automáticos para erros críticos.
```

---

## 🔒 10. Segurança

```bash
- Autenticação via OAuth2 / JWT.
- Proteção contra ataques: CSRF, XSS, SQL Injection.
- Limite de requisições (rate limiting) para evitar abuso.
- Cabeçalhos de segurança via Helmet.
```

---

## 🚀 11. Deploy e Infraestrutura

Pipeline totalmente **automático**, baseado em **CI/CD** via Vercel.

### 🔄 Pipeline de Deploy

```bash
1. Commit na branch main → Trigger de pipeline.
2. Build automatizado via Next.js.
3. Deploy incremental com cache inteligente (Redis + CDN).
4. Disponibilização via CDN global da Vercel.
```

### 🧱 Ambientes

| Ambiente     | URL                                                                          |
| ------------ | ---------------------------------------------------------------------------- |
| **Produção** | [https://brasilapi.com.br](https://brasilapi.com.br)                         |
| **Staging**  | [https://staging.brasilapi.vercel.app](https://staging.brasilapi.vercel.app) |
| **Local**    | `npm run dev`                                                                |

---

## 🤝 12. Como Contribuir

A **BrasilAPI** é mantida pela comunidade, e toda contribuição é bem-vinda!

### 🔧 Passos para contribuir

```bash
git clone https://github.com/BrasilAPI/BrasilAPI.git
cd BrasilAPI
npm install
npm run dev
```

### 📤 Envio de PR

```bash
1. Crie uma branch: git checkout -b feature/nova-feature
2. Faça alterações e commits.
3. Envie um pull request explicando o contexto da mudança.
```

---

## 👥 13. Equipe e Comunidade

O projeto é mantido por voluntários e desenvolvedores da comunidade brasileira.

| Papel                        | Responsável                                                                                                   |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Fundador**                 | [@filipedeschamps](https://github.com/filipedeschamps)                                                        |
| **Colaboradores Principais** | [@diego3g](https://github.com/diego3g), [@rocketseat](https://github.com/Rocketseat) e comunidade open source |
| **Comunidade**               | Discord, GitHub Issues, PRs e fóruns                                                                          |

---

## 🧾 14. Licença

Este projeto está licenciado sob a **MIT License** – veja o arquivo `LICENSE` para mais detalhes.

---

## 📚 15. Referências

```bash
- Next.js Documentation
- Vercel Platform
- OpenAPI Specification
- Node.js Docs
- Tailwind CSS
- Jest Framework
- BrasilAPI - Site Oficial
```

---

## 📌 Resumo

A **BrasilAPI** é um exemplo de como a **colaboração aberta** pode transformar o acesso à informação pública, oferecendo uma infraestrutura moderna, escalável, segura e de fácil integração para desenvolvedores e sistemas em todo o Brasil. 🇧🇷
