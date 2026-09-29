# 🏥 Sistema de Agendamento de Consultas – Clínica RIGATTI

Este projeto full stack foi desenvolvido para a Clínica RIGATTI, permitindo que pacientes agendem consultas online e que o administrador aprove ou recuse agendamentos, além de controlar horários disponíveis.

---

## ⚙️ Tecnologias Utilizadas

### 🔹 Backend
- Node.js + Express
- MongoDB + Mongoose
- Jest + Supertest (testes automatizados)
- Dotenv, CORS

### 🔹 Frontend
- React (com Vite)
- Tailwind CSS
- React Router DOM
- Axios

---

## 📁 Estrutura do Projeto

```
agenda-clinica/
├── backend/
│   ├── config/              # Conexão com o banco MongoDB
│   ├── controllers/         # Regras de negócio
│   ├── models/              # Schemas do Mongoose (Agendamentos, Pacientes, Horários)
│   ├── routes/              # Endpoints REST organizados por entidade
│   ├── src/                 # Aplicação Express principal (app.js)
│   ├── tests/               # Testes unitários com Jest
│   ├── server.js            # Inicialização do servidor
│   ├── .env.example         # Exemplo de variáveis ambiente
│   └── jest.config.js       # Configuração dos testes
│
├── frontend/
│   ├── src/
│   │   ├── components/      # Componentes reutilizáveis (cards, badges, formulários)
│   │   ├── pages/           # Telas principais: Login, Admin, Paciente, AdminSchedules
│   │   ├── services/        # API service com Axios
│   │   ├── App.jsx          # Rotas da aplicação
│   │   ├── main.jsx         # Inicialização do React
│   │   └── index.css        # Estilos base do Tailwind
│   ├── tailwind.config.js   # Configuração do Tailwind
│   ├── postcss.config.js    # Processamento CSS
│   ├── vite.config.js       # Configuração do Vite
│   └── package.json         # Dependências do frontend
```

---

## 🚀 Como Rodar Localmente

### 1. Clonar o Projeto

```bash
git clone https://github.com/angelinogonsalves/agenda-clinica.git
cd agenda-clinica
```

### 2. Backend

```bash
cd backend
npm install
cp .env.example .env
# Edite o .env com suas URIs do MongoDB
npm run dev
```

Servidor: [http://localhost:3000](http://localhost:3000)

### 3. Frontend

```bash
cd ../frontend
npm install
npm run dev
```

App Web: [http://localhost:5173](http://localhost:5173)

---

## 🧪 Rodando Testes (Backend)

```bash
cd backend
npm test
```

Certifique-se de que a variável `MONGO_URI_TEST` esteja configurada corretamente.

---

## 📌 Funcionalidades

### Paciente
- Login simples apenas com nome
- Visualizar horários disponíveis
- Agendar consulta (data, especialidade, telefone)
- Visualizar seus agendamentos

### Administrador (login como “admin”)
- Visualizar todos os agendamentos pendentes
- Aprovar ou rejeitar agendamentos
- Cadastrar novos horários disponíveis
- Remover horários

---

## 🔗 Endpoints Principais

### 📅 `/api/appointments`
- `POST /` – Criar novo agendamento
- `GET /` – Listar todos os agendamentos
- `GET /patient/:patientName` – Buscar por paciente
- `PUT /:id/status` – Alterar status (admin)
- `DELETE /:id` – Remover agendamento

### 🕒 `/api/schedules`
- `POST /` – Criar novo horário
- `GET /` – Listar horários disponíveis
- `DELETE /:id` – Remover horário

### 👤 `/api/patients`
- `POST /` – Criar paciente (automático ao agendar)
- `GET /` – Listar todos
- `GET /phone/:phone` – Listar paciente por telefone
- `DELETE /:id` – Remover paciente

---

## 🧠 Observações Técnicas

- Nome do paciente é salvo no `localStorage`
- O backend impede agendamentos duplicados para o mesmo horário
- O frontend oculta horários já agendados por qualquer usuário
- Sem autenticação real (simulação com base no nome informado)
