# 🇧🇷 **BrasilAPI – Unificando dados públicos do Brasil**

---

## 🧭 1. Introdução

A **BrasilAPI** é uma iniciativa **open source** voltada à unificação e simplificação do acesso a **dados públicos brasileiros**.  
Diversas fontes de informação governamentais disponibilizam APIs, mas com **formatos inconsistentes**, **baixa disponibilidade** e **falta de documentação**.  
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
- Garantir performance e disponibilidade via **Vercel CDN**.  

---

## 🧱 3. Arquitetura do Sistema

A **BrasilAPI** adota uma arquitetura modular e escalável, baseada em **Next.js** e **Node.js**, hospedada na **Vercel** com suporte a **CI/CD** automatizado.

### 🧩 Visão Geral

```bash
Cliente (HTTP Request)
↓
Next.js / API Gateway
↓
Serviços Modulares (CEP, CNPJ, DDD, IBGE, etc.)
↓
Fontes Externas (Correios, Receita Federal, etc.)
↓
Cache e Resposta Unificada
````

### 🔍 Principais Componentes

| Camada                    | Função                                                                  |
| ------------------------- | ----------------------------------------------------------------------- |
| **Frontend (Next.js)**    | Exibição da documentação e interface interativa.                        |
| **Backend (Node.js)**     | Processamento das requisições e integração com fontes externas.         |
| **Serviços Modulares**    | Cada módulo implementa uma integração específica (CEP, CNPJ, IBGE etc). |
| **Vercel Infrastructure** | Hospedagem, CDN, logs e pipelines automáticos.                          |
| **Cache/CDN**             | Otimiza a latência e reduz chamadas redundantes.                        |

---

## ⚙️ 4. Tecnologias Utilizadas

| Categoria          | Tecnologias              | Descrição                                            |
| ------------------ | ------------------------ | ---------------------------------------------------- |
| **Frontend**       | Next.js, React           | Framework e biblioteca para UI da documentação.      |
| **Backend**        | Node.js, Express         | Camada de serviços e integração com APIs externas.   |
| **Infraestrutura** | Vercel, Docker           | Deploy automatizado e ambiente isolado de execução.  |
| **Documentação**   | OpenAPI, Swagger UI      | Especificação e visualização das rotas e parâmetros. |
| **Testes**         | Jest, Supertest          | Validação de endpoints e responses.                  |
| **Monitoramento**  | Vercel Analytics, Sentry | Observabilidade e métricas de uso.                   |

---

## 🧠 5. Estrutura do Projeto

```bash
📦 BrasilAPI
 ┣ 📁 src
 ┃ ┣ 📁 services          # Integrações com APIs externas (Correios, IBGE, etc)
 ┃ ┣ 📁 routes            # Definição das rotas (ex: /cep, /cnpj)
 ┃ ┣ 📁 utils             # Funções auxiliares e middlewares
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

💡 Todas as respostas seguem formato JSON e são documentadas via **OpenAPI (Swagger)**.

---

## 🔁 8. Fluxo de Requisições

```bash
1. O cliente realiza a chamada para o endpoint desejado.
2. O sistema identifica o módulo correspondente (CEP, CNPJ, etc).
3. São realizadas requisições simultâneas a múltiplas fontes externas.
4. As respostas são tratadas, padronizadas e retornadas em formato JSON.
5. O resultado é cacheado e servido pela Vercel CDN.
```

---

## 🧪 9. Testes e Qualidade

A qualidade do código é garantida por testes automatizados e ferramentas de integração contínua.

### 🧰 Stack de Testes

```bash
- Jest: testes unitários e mocks.
- Supertest: simulação de chamadas HTTP reais.
- Coverage: mínimo de 90% nos módulos críticos.
```

### ✅ Critérios de Qualidade

```bash
- Padrão de código verificado com ESLint + Prettier.
- PRs revisados por múltiplos colaboradores.
- Testes automatizados no GitHub Actions.
```

---

## 🚀 10. Deploy e Infraestrutura

O processo de deploy é automatizado e baseado em **CI/CD via Vercel**.

### 🔄 Pipeline de Deploy

```bash
1. Commit na branch main → Trigger de pipeline.
2. Build automatizado via Next.js.
3. Deploy incremental com cache inteligente.
4. Disponibilização via CDN global da Vercel.
```

### 🧱 Ambientes

| Ambiente     | URL                                                                          |
| ------------ | ---------------------------------------------------------------------------- |
| **Produção** | [https://brasilapi.com.br](https://brasilapi.com.br)                         |
| **Staging**  | [https://staging.brasilapi.vercel.app](https://staging.brasilapi.vercel.app) |
| **Local**    | `npm run dev`                                                                |

---

## 🤝 11. Como Contribuir

A **BrasilAPI** é mantida pela comunidade, e toda contribuição é bem-vinda!

### 🔧 Passos para contribuir

```bash
# Clone o projeto
git clone https://github.com/BrasilAPI/BrasilAPI.git

# Entre na pasta
cd BrasilAPI

# Instale as dependências
npm install

# Rode localmente
npm run dev
```

### 📤 Envio de PR

```bash
1. Crie uma branch: git checkout -b feature/nova-feature
2. Faça suas alterações e commits.
3. Envie um pull request explicando o contexto da mudança.
```

---

## 👥 12. Equipe e Comunidade

O projeto é mantido por voluntários e desenvolvedores da comunidade brasileira.
Atualmente, conta com dezenas de contribuidores ativos e apoio de diversas empresas de tecnologia.

| Papel                        | Responsável                                                                                                   |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Fundador**                 | [@filipedeschamps](https://github.com/filipedeschamps)                                                        |
| **Colaboradores Principais** | [@diego3g](https://github.com/diego3g), [@rocketseat](https://github.com/Rocketseat) e comunidade open source |
| **Comunidade**               | Discord, GitHub Issues, PRs e fóruns                                                                          |

---

## 🧾 13. Licença

Este projeto está licenciado sob a **MIT License** – veja o arquivo `LICENSE` para mais detalhes.

---

## 📚 14. Referências

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

A **BrasilAPI** é um exemplo de como a **colaboração aberta** pode transformar o acesso à informação pública, oferecendo uma infraestrutura moderna, escalável e de fácil integração para desenvolvedores e sistemas em todo o Brasil. 🇧🇷
