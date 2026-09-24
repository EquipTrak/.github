<div align="center">

# 📦 EquipTrack

### Sistema de Empréstimo e Rastreabilidade de Equipamentos

**Fábrica de Software • Engenharia de Software • UNIVILLE**
Projeto **P01** • 2º bimestre • Prazo final: **05/12/2026**

![Java](https://img.shields.io/badge/Java-21-orange?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?logo=springboot&logoColor=white)
![Status](https://img.shields.io/badge/status-em_desenvolvimento-yellow)
![Arquitetura](https://img.shields.io/badge/arquitetura-monólito_modular-blue)

</div>

---

## 📖 Sobre o projeto

Laboratórios, setores acadêmicos e pequenas organizações costumam compartilhar notebooks, projetores, câmeras, kits e adaptadores. Quando o controle é feito por planilhas, mensagens ou anotações, fica difícil saber **quem está com cada item**, **quando ele deve voltar**, **em que condição foi devolvido** e **qual é o seu histórico de uso**.

O **EquipTrack** é um sistema web que centraliza o cadastro de equipamentos e permite rastrear todo o ciclo de **solicitação → aprovação → retirada → devolução → mudança de condição**.

## 🎯 Objetivo

Entregar um sistema web funcional, integrado de ponta a ponta, com:

- Autenticação e controle de acesso por perfil
- Regras de negócio implementadas no backend
- Persistência relacional
- Frontend utilizável
- Testes automatizados
- Documentação suficiente para que outra equipe consiga entender, executar e evoluir a solução

## 👥 Atores

| Perfil | O que faz |
|---|---|
| **Operador / Responsável pelo patrimônio** | Cadastra equipamentos, aprova/rejeita solicitações, registra retiradas e devoluções, consulta histórico |
| **Solicitante** | Consulta itens disponíveis, solicita empréstimo e acompanha suas solicitações |
| **Administrador** | Gerencia usuários, categorias e parâmetros básicos |

## ✅ Escopo do MVP

- [ ] Autenticação e controle de acesso por perfil
- [ ] Cadastro e consulta de equipamentos (identificação patrimonial única, categoria, descrição, condição e situação)
- [ ] Cadastro e consulta de solicitantes
- [ ] Solicitação de empréstimo com período pretendido
- [ ] Aprovação ou rejeição da solicitação pelo operador
- [ ] Registro de retirada do equipamento
- [ ] Registro de devolução (condição na devolução + observação)
- [ ] Histórico completo por equipamento e por solicitante
- [ ] Consulta de empréstimos ativos e atrasados
- [ ] Dashboard com totais de disponíveis, emprestados, atrasados e indisponíveis

### 🚫 Fora de escopo neste bimestre

- Aplicativo mobile nativo
- Leitura obrigatória de QR Code / código de barras
- Integração com patrimônio institucional real
- Assinatura digital avançada
- Notificações por WhatsApp/e-mail como requisito obrigatório
- Gestão completa de manutenção preventiva

> Funcionalidades fora de escopo só podem ser iniciadas quando todo o MVP estiver funcional, testado e aprovado pelo Product Owner.

## 📜 Regras de negócio

1. Cada equipamento possui um identificador patrimonial **único**.
2. Somente equipamento com situação **DISPONÍVEL** pode ser liberado para empréstimo.
3. Solicitação aprovada **não** é retirada — a retirada é registrada separadamente.
4. Um equipamento não pode ter **dois empréstimos ativos** simultaneamente.
5. A devolução deve registrar a **condição** do equipamento.
6. Equipamento devolvido com avaria pode ficar automaticamente **INDISPONÍVEL** até avaliação.
7. Empréstimo não devolvido até a data prevista aparece como **ATRASADO**.
8. O histórico de movimentações **não pode ser apagado** por usuário comum.
9. Solicitante com empréstimo atrasado não recebe novo equipamento até regularização, salvo exceção registrada por administrador.

## 🏗️ Arquitetura e tecnologias

**Monólito modular em camadas**:

```
Frontend → API REST → Controllers → Services → Repositories → Banco relacional
```

| Item | Tecnologia |
|---|---|
| Backend | Java 21 + Spring Boot 4.x |
| Persistência | Spring Data JPA / Hibernate |
| Banco de dados | PostgreSQL ou MySQL *(a definir e justificar no ADR)* |
| API | REST / JSON |
| Frontend | HTML5, CSS3 e JavaScript *(framework a definir e documentar)* |
| Segurança | Spring Security |
| Validação | Jakarta Bean Validation (backend) + validações de UX (frontend) |
| Documentação da API | OpenAPI / Swagger |
| Testes | JUnit 5 + Mockito |
| Versionamento | Git + GitHub (issues, branches curtas e Pull Requests) |

**Princípios:** DTOs para não expor entidades diretamente • regras de negócio na camada de serviço/domínio (nunca em controllers ou no JavaScript de tela) • senhas nunca em texto puro • rotas protegidas por perfil.

## 🧑‍💻 Equipe

| Integrante | Responsabilidade primária |
|---|---|
| **Caio Januario** | Análise de requisitos e domínio + Backend |
| **Guilherme Elias** | Dados + Backend |
| **Iago Longen** | Frontend |
| **Thiago Bueno** | Frontend/UX + Integração |
| **Vinicius Hoffmann** | Backend/Security + Integração |
| **Yuri Hassel** | QA/Documentação + Gestão do fluxo |

> O papel acima é a responsabilidade **principal**, não uma divisão rígida. Todos participam de análise, revisão de PRs, testes e apresentação.

**Professor:** Prof. Sestito — Cliente, Product Owner e Tech Lead acadêmico.

## 🗓️ Cronograma

| Período | Etapa | Resultado esperado |
|---|---|---|
| 21/09 – 27/09 | Descoberta e planejamento | Requisitos iniciais, atores, escopo, regras e backlog |
| 28/09 – 04/10 | Modelagem e prototipação | Wireframes, DER, arquitetura e contrato inicial da API |
| 05/10 – 18/10 | **Sprint 1** | Estrutura, autenticação, banco, cadastros e primeiro fluxo vertical |
| 19/10 – 01/11 | **Sprint 2** | Fluxo principal, regras críticas e integração front/back |
| 02/11 – 15/11 | **Sprint 3** | Conclusão do MVP, histórico, dashboard e correções |
| **16/11** | 🔒 Congelamento de escopo | Nada novo entra sem aprovação do PO |
| 16/11 – 29/11 | Estabilização | Testes, segurança, UX, documentação e ambiente de demo |
| 30/11 – 05/12 | Entrega final | Validação de aceite, demonstração e retrospectiva |

## 🚀 Como executar

> ⚠️ Preencher conforme a versão efetivamente entregue.

### Pré-requisitos

- Java 21
- Maven ou Gradle
- PostgreSQL ou MySQL *(conforme decisão do grupo)*
- Node.js *(se o frontend usar framework)*

### Backend

```bash
git clone https://github.com/<organizacao>/<repositorio-backend>.git
cd <repositorio-backend>

# configurar variáveis de ambiente / application.properties
./mvnw spring-boot:run
```

### Frontend

```bash
git clone https://github.com/<organizacao>/<repositorio-frontend>.git
cd <repositorio-frontend>

npm install
npm run dev
```

### Credenciais de demonstração

| Perfil | Usuário | Senha |
|---|---|---|
| Administrador | *a definir* | *a definir* |
| Operador | *a definir* | *a definir* |
| Solicitante | *a definir* | *a definir* |

### Documentação da API

Após subir o backend: `http://localhost:8080/swagger-ui.html` *(ajustar conforme configuração)*

## 📂 Repositórios da organização

| Repositório | Descrição |
|---|---|
| `equiptrack-backend` | API REST em Java 21 + Spring Boot |
| `equiptrack-frontend` | Interface web do sistema |
| `equiptrack-docs` | Requisitos, DER, arquitetura, ADRs, wireframes e plano de testes |

*(ajustar conforme os repositórios reais)*

## 📚 Entregáveis

- [ ] README com contexto, instruções de execução, tecnologias e credenciais de demo
- [ ] Documento de requisitos (problema, atores, RFs, RNFs, regras e critérios de aceite)
- [ ] Protótipo / wireframes das telas principais
- [ ] Diagrama de contexto e diagrama de arquitetura
- [ ] DER e dicionário de dados
- [ ] Backlog priorizado com responsáveis
- [ ] Registro de decisões técnicas (ADRs)
- [ ] Código versionado com histórico de contribuição por integrante
- [ ] Evidências de testes e relatório dos principais cenários
- [ ] Aplicação executável com massa de dados para demonstração
- [ ] Apresentação final com demo ponta a ponta e retrospectiva

## 🤝 Fluxo de trabalho

- Toda tarefa tem **responsável principal** no backlog antes de começar
- Branches curtas e **Pull Requests obrigatórios**
- Nenhum PR é aprovado apenas pelo próprio autor
- Cada integrante demonstra **ao menos uma contribuição verificável por semana**
- Bloqueios são registrados e levados ao PO/Tech Lead o quanto antes
- Decisões importantes são registradas no repositório

### ✔️ Definition of Done

Uma funcionalidade só está concluída quando:

- O critério de aceite foi atendido
- O backend valida dados e trata erros previsíveis
- As permissões de acesso foram verificadas
- O fluxo funciona com o banco de dados real
- A tela tem estados de carregamento, sucesso, vazio e erro (quando aplicável)
- O código foi revisado por pelo menos outro integrante via PR
- Os testes das regras críticas passaram
- A documentação impactada foi atualizada

## 🎬 Fluxo de aceite mínimo

1. Cadastrar um equipamento e vê-lo como disponível
2. Solicitante cria uma solicitação para período válido
3. Operador aprova, registra a retirada e o item deixa de constar como disponível
4. Registrar a devolução e atualizar a situação do equipamento
5. Tentar emprestar um item já emprestado e o sistema impedir
6. Consultar o histórico completo do equipamento após o ciclo

---

<div align="center">

Projeto acadêmico • **UNIVILLE** • Engenharia de Software • Fábrica de Software 2026

</div>
