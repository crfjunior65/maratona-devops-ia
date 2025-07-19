# 🚀 Maratona DevOps IA

[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![DigitalOcean](https://img.shields.io/badge/DigitalOcean-0080FF?style=for-the-badge&logo=digitalocean&logoColor=white)](https://www.digitalocean.com/?refcode=12736b5d24eb&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)

## 📋 Sobre o Projeto

Este projeto é parte de uma maratona de aprendizado em DevOps, focada em tecnologias como Docker, Kubernetes e Node.js. O projeto é dividido em três partes principais:

[![DigitalOcean Referral Badge](https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%203.svg)](https://www.digitalocean.com/?refcode=6dbd40fd44c2&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)

A **Maratona DevOps IA** é um projeto educacional focado no aprendizado prático de tecnologias DevOps modernas, incluindo containerização com Docker, orquestração com Kubernetes e deploy em cloud. O projeto demonstra a evolução de aplicações desde o desenvolvimento local até a produção em ambiente Kubernetes.

## 🎯 Objetivos da Maratona

- **Containerização**: Criação e otimização de containers Docker
- **Orquestração**: Deploy e gerenciamento com Kubernetes
- **Cloud Native**: Implementação de práticas cloud-native
- **Monitoramento**: Observabilidade e health checks
- **IaC**: Infrastructure as Code com manifests Kubernetes
- **CI/CD**: Automação de deploy e entrega contínua

## 🏗️ Estrutura do Projeto

```
maratona-devops-ia/
├── 00-exemplo-deploy/          # Exemplos básicos de deploy Kubernetes
│   ├── deployment.yaml         # Manifest de deployment
│   ├── README.md              # Documentação do deploy
│   └── image.png              # Diagrama da arquitetura
├── 01-conversao-temperatura/   # Aplicação Node.js de conversão
│   ├── src/                   # Código-fonte da aplicação
│   │   ├── Dockerfile         # Container da aplicação
│   │   ├── server.js          # Servidor Express
│   │   └── convert.js         # Lógica de conversão
│   └── README.md              # Documentação do projeto
├── 02-kube-news/              # Portal de notícias completo
│   ├── src/                   # Aplicação Node.js + PostgreSQL
│   │   ├── Dockerfile         # Container da aplicação
│   │   ├── server.js          # Servidor principal
│   │   ├── models/            # Modelos de dados
│   │   └── views/             # Templates EJS
│   ├── k8s/                   # Manifests Kubernetes
│   │   ├── deployment.yaml    # Deploy da aplicação
│   │   └── README.md          # Guia de deploy K8s
│   ├── compose.yaml           # Docker Compose local
│   └── popula-dados.http      # Dados de exemplo
├── CMD-KubeCTL-15072025       # Histórico de comandos kubectl
└── .gitignore                 # Arquivos ignorados pelo Git
```

## 🛠️ Tecnologias Utilizadas

### Backend & Runtime
- **Node.js** - Runtime JavaScript
- **Express.js** - Framework web
- **PostgreSQL** - Banco de dados relacional
- **Sequelize** - ORM para Node.js

### DevOps & Infrastructure
- **Docker** - Containerização
- **Kubernetes** - Orquestração de containers
- **DigitalOcean** - Cloud provider
- **Docker Hub** - Registry de imagens

### Monitoramento & Observabilidade
- **Prometheus** - Coleta de métricas
- **Health Checks** - Monitoramento de saúde
- **Chaos Engineering** - Testes de resiliência

## 🚀 Projetos Incluídos

### 1. Conversão de Temperatura
**Localização**: `01-conversao-temperatura/`

Aplicação simples em Node.js para conversão entre escalas de temperatura (Celsius, Fahrenheit, Kelvin).

**Características**:
- API REST simples
- Container Docker otimizado
- Porta padrão: 8080
- Ideal para primeiros passos com containers

### 2. Kube News
**Localização**: `02-kube-news/`

Portal completo de notícias com funcionalidades avançadas de monitoramento e chaos engineering.

**Características**:
- Frontend com templates EJS
- Backend Node.js + PostgreSQL
- Endpoints de health check
- Métricas para Prometheus
- Simulação de falhas para testes
- Deploy completo no Kubernetes

### 3. Exemplos de Deploy
**Localização**: `00-exemplo-deploy/`

Exemplos práticos de deployment no Kubernetes com manifests básicos.

## 📦 Como Executar

### Pré-requisitos

```bash
# Ferramentas necessárias
- Docker
- Kubernetes (kubectl)
- Node.js (para desenvolvimento local)
- Git
```

### Execução Local com Docker

```bash
# Clone o repositório
git clone <repository-url>
cd maratona-devops-ia

# Conversão de Temperatura
cd 01-conversao-temperatura/src
docker build -t conversao-temp .
docker run -p 8080:8080 conversao-temp

# Kube News (com Docker Compose)
cd ../../02-kube-news
docker-compose up -d
```

### Deploy no Kubernetes

```bash
# Aplicar manifests do Kube News
cd 02-kube-news/k8s
kubectl apply -f deployment.yaml

# Verificar status
kubectl get pods
kubectl get services
```

## 🔧 Configuração de Ambiente

### Variáveis de Ambiente - Kube News

| Variável | Descrição | Valor Padrão |
|----------|-----------|--------------|
| `DB_DATABASE` | Nome do banco | kubedevnews |
| `DB_USERNAME` | Usuário do banco | kubedevnews |
| `DB_PASSWORD` | Senha do banco | Pg#123 |
| `DB_HOST` | Host do banco | localhost |
| `DB_PORT` | Porta do banco | 5432 |

### Comandos Kubectl Úteis

```bash
# Verificar cluster
kubectl cluster-info
kubectl get nodes

# Gerenciar aplicações
kubectl get pods
kubectl get services
kubectl get deployments

# Logs e debug
kubectl logs <pod-name>
kubectl describe pod <pod-name>
```

## 📊 Monitoramento e Health Checks

### Endpoints Disponíveis

- `/health` - Status da aplicação
- `/ready` - Readiness probe
- `/metrics` - Métricas Prometheus
- `/unhealth` - Simular falha (PUT)
- `/unreadyfor/:seconds` - Simular indisponibilidade (PUT)

### Chaos Engineering

O projeto inclui funcionalidades para testar resiliência:

```bash
# Simular aplicação não saudável
curl -X PUT http://localhost:8080/unhealth

# Simular indisponibilidade por 30 segundos
curl -X PUT http://localhost:8080/unreadyfor/30
```

## 🎓 Cronograma da Maratona

### Dia 1: Containerização
- ✅ Criação de Dockerfiles
- ✅ Build e push de imagens
- ✅ Testes locais com Docker

### Dia 2: Kubernetes
- ✅ Deploy no DigitalOcean Kubernetes
- ✅ Manifests de deployment
- ✅ Configuração de services

### Dia 3: Observabilidade
- 🔄 Implementação de métricas
- 🔄 Health checks avançados
- 🔄 Monitoramento em produção

## 🤝 Contribuição

Este é um projeto educacional. Contribuições são bem-vindas através de:

1. Fork do projeto
2. Criação de branch para feature
3. Commit das mudanças
4. Push para a branch
5. Abertura de Pull Request

## 📚 Recursos Adicionais

- [Documentação Docker](https://docs.docker.com/)
- [Documentação Kubernetes](https://kubernetes.io/docs/)
- [DigitalOcean Kubernetes](https://www.digitalocean.com/products/kubernetes/)
- [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)

## 📄 Licença

Este projeto é desenvolvido para fins educacionais como parte da Maratona DevOps IA.

---

**Desenvolvido com ❤️ durante a Maratona DevOps IA**

[![DigitalOcean Referral Badge](https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%201.svg)](https://www.digitalocean.com/?refcode=12736b5d24eb&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)