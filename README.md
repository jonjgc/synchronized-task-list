# Lista de Tarefas Colaborativa

Este projeto é uma aplicação de lista de tarefas colaborativa com sincronização em tempo real, permitindo criar, listar, atualizar, marcar como concluídas e excluir tarefas. O sistema é composto por um **backend** (Node.js), um **frontend web** (React.js) e um **frontend mobile** (React Native). A comunicação entre clientes é feita via WebSocket, e os dados são persistidos em um banco MongoDB.

---

## Configuração

### Configure o Backend:

Navegue até a pasta `backend`:

```bash
cd backend
```

Instale as dependências:

```bash
npm install
```

Crie um arquivo `.env` com:

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/todo-app
```

Certifique-se de que o MongoDB está rodando:

```bash
net start MongoDB
```

Ou inicie manualmente:

```bash
mongod --dbpath C:\data\db
```

---

### Configure o Frontend Web:

Navegue até a pasta `frontend-web`:

```bash
cd ../frontend-web
```

Instale as dependências:

```bash
npm install
```

---

### Configure o Frontend Mobile:

Navegue até a pasta `frontend-mobile`:

```bash
cd ../frontend-mobile
```

Instale as dependências:

```bash
npm install
```

---

## Execução

### Inicie o Backend:

Na pasta `backend`:

```bash
cd ../backend
npm run dev
```

Verifique se aparece `MongoDB connected` e `Server running on port 5000`.

---

### Inicie o Frontend Web:

Na pasta `frontend-web`:

```bash
cd ../frontend-web
npm start
```

A aplicação abrirá em [http://localhost:3000](http://localhost:3000).

---

### Inicie o Frontend Mobile:

Na pasta `frontend-mobile`:

```bash
cd ../frontend-mobile
npx expo start
```

#### Para testar:
- **Emulador Android**: Inicie um emulador no Android Studio e pressione `a`.
- **Expo Go**: Escaneie o QR code com o app Expo Go no celular.
- **Web**: Pressione `w` para abrir no navegador (limitado).

---

## Uso

### Backend:
Teste a API com Postman ou cURL:

- `GET http://localhost:5000/api/tasks`: Lista tarefas.
- `POST http://localhost:5000/api/tasks`: Envie `{ "title": "Nova tarefa" }`.
- `PUT http://localhost:5000/api/tasks/:id`: Envie `{ "title": "Tarefa atualizada", "completed": true }`.
- `DELETE http://localhost:5000/api/tasks/:id`: Exclui uma tarefa.

> O WebSocket emite eventos `taskUpdated` para sincronizar clientes.

---

### Frontend Web:

Acesse [http://localhost:3000](http://localhost:3000).

- **Adicionar tarefa**: Digite um título e clique em "Adicionar".
- **Marcar como concluída**: Clique no checkbox.
- **Editar tarefa**: Clique no ícone de lápis, altere o título e clique em "Salvar".
- **Excluir tarefa**: Clique no ícone de lixeira.
- **Sincronização**: Abra múltiplas abas para ver mudanças em tempo real.

---

### Frontend Mobile:

Abra no emulador ou Expo Go.

- **Adicionar tarefa**: Digite um título e clique em "Adicionar".
- **Marcar como concluída**: Toque no checkbox.
- **Editar tarefa**: Toque no ícone de lápis, altere o título e clique em "Salvar".
- **Excluir tarefa**: Toque no ícone de lixeira.
- **Sincronização**: Teste com o frontend web ou outro dispositivo para confirmar atualizações em tempo real.

---

## Estrutura do Projeto

```
todo-app/
├── backend/
│   ├── src/
│   │   ├── models/
│   │   │   └── Task.js         # Modelo do MongoDB
│   │   ├── routes/
│   │   │   └── tasks.js        # Rotas da API
│   │   ├── index.js            # Entrada do servidor
│   ├── .env                    # Variáveis de ambiente
│   ├── package.json            # Dependências e scripts
├── frontend-web/
│   ├── src/
│   │   ├── components/
│   │   │   └── TaskList.js     # Componente da lista de tarefas
│   │   ├── App.js              # Componente raiz
│   │   ├── index.js            # Entrada da aplicação
│   ├── package.json            # Dependências e scripts
├── frontend-mobile/
│   ├── src/
│   │   ├── screens/
│   │   │   └── TaskScreen.js   # Tela principal de tarefas
│   │   ├── App.js              # Componente raiz
│   ├── index.js                # Entrada da aplicação
│   ├── app.json                # Configurações do Expo
│   ├── package.json            # Dependências e scripts
├── README.md                   # Documentação do projeto
```

---

## Scripts

### Backend

- `npm start`: Inicia o servidor em modo produção.
- `npm run dev`: Inicia com nodemon para desenvolvimento.

### Frontend Web

- `npm start`: Inicia o frontend em modo desenvolvimento.
- `npm build`: Gera uma build para produção.
- `npm test`: Executa testes (se configurados).

### Frontend Mobile

- `npx expo start`: Inicia o app com Expo.
- `npx expo start --android`: Abre no emulador Android.
- `npx expo start --web`: Abre no navegador.
- `npx expo start --clear`: Limpa o cache.

---

## Solução de Problemas

### MongoDB não conecta:

- Verifique o serviço:

  ```bash
  net start MongoDB
  ```

- Confirme o `MONGO_URI` no `backend/.env`.

### API retorna erro 500:

- Veja os logs no terminal do backend.
- Teste endpoints com Postman para isolar o problema.

### WebSocket não funciona:

- Verifique logs no console do navegador (F12), Expo Go ou terminal do backend.
- Teste com `http://127.0.0.1:5000` no `socket.io-client`.
- Confirme que a porta 5000 está liberada:

  ```bash
  netstat -a -n -o | find "5000"
  ```

### Frontend Web não atualiza:

- Veja o console do navegador para erros.
- Recarregue a página para forçar a busca de tarefas.

### Frontend Mobile não carrega:

- Limpe o cache:

  ```bash
  npx expo start --clear
  ```

- Verifique erros no terminal do Expo ou no menu de desenvolvimento do Expo Go (agite o dispositivo).
- Confirme que `react-native-vector-icons` está instalado.

### Portas bloqueadas:

Verifique portas 19000 (Expo) e 5000 (backend):

```bash
netstat -a -n -o | find "19000"
```

---

## Próximos Passos

### Melhorias na Interface:

- Adicionar animações com `react-native-reanimated` ou `framer-motion` (web).
- Implementar tema claro/escuro.

### Funcionalidades:

- Adicionar autenticação de usuários.
- Implementar filtros (ex.: tarefas concluídas, pendentes).

### Deploy:

- Publicar o backend em serviços como Render ou Heroku.
- Gerar APK para o frontend mobile com Expo.

### Testes:

- Configurar testes unitários para backend e frontends.

---

## Autor

**Jônatas Camelo**
