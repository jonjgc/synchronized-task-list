# Lista de Tarefas Colaborativa

Este projeto é uma aplicação de lista de tarefas colaborativa com sincronização em tempo real, permitindo criar, listar, atualizar, marcar como concluídas e excluir tarefas. O sistema é composto por um **backend** (Node.js) e um **frontend web** (React.js), com um **frontend mobile** (React Native) planejado para ser implementado. A comunicação entre clientes é feita via WebSocket, e os dados são persistidos em um banco MongoDB.

## Funcionalidades
- **Gerenciamento de Tarefas**:
  - Criar novas tarefas.
  - Listar todas as tarefas.
  - Editar títulos de tarefas existentes.
  - Marcar tarefas como concluídas.
  - Excluir tarefas.
- **Sincronização em Tempo Real**: Alterações são refletidas instantaneamente em todos os clientes conectados (web e, futuramente, mobile).
- **Interface Web Profissional**: Design moderno com layout responsivo, sombras, ícones e animações sutis.
- **API RESTful**: Backend fornece endpoints para manipulação de tarefas.
- **Persistência**: Dados armazenados em MongoDB.

## Tecnologias
### Backend
- **Node.js**: Runtime para o servidor.
- **Express**: Framework para a API RESTful.
- **MongoDB**: Banco NoSQL para persistência.
- **Mongoose**: ODM para interação com MongoDB.
- **Socket.IO**: Comunicação em tempo real via WebSocket.
- **dotenv**: Gerenciamento de variáveis de ambiente.

### Frontend Web
- **React.js**: Biblioteca para a interface.
- **Axios**: Requisições HTTP à API.
- **Socket.IO-client**: Sincronização em tempo real.
- **Styled-Components**: Estilização de componentes.
- **React-Icons**: Ícones para a interface.

### Frontend Mobile (Planejado)
- **React Native**: Framework para o app mobile.
- **Expo**: Ferramenta para simplificar o desenvolvimento.
- **React Navigation**: Navegação entre telas.

## Pré-requisitos
- **Node.js** (v16 ou superior)
- **npm** (gerenciador de pacotes do Node.js)
- **MongoDB** (Community Server)
- **Git** (opcional, para controle de versão)

## Instalação
1. **Clone o repositório** (ou copie os arquivos para a pasta `todo-app`):
   ```bash
   git clone <url-do-repositorio>
   cd todo-app