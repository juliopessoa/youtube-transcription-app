# 🎬 Transcrição de Cursos YouTube - Aplicação Web

Uma aplicação web completa para transcrição automática de vídeos do YouTube com resumos gerados por Inteligência Artificial (OpenAI/Claude).

## ✨ Funcionalidades

- **Transcrição Automática**: Extrai automaticamente transcrições de vídeos do YouTube
- **Resumos com IA**: Gera resumos inteligentes usando OpenAI GPT ou Claude
- **Interface Moderna**: Interface web responsiva e intuitiva
- **Progresso em Tempo Real**: Barra de progresso para acompanhar o processamento
- **Visualização JSON**: Visualizador interativo dos dados transcritos
- **Download Automático**: Exporta resultados em formato JSON
- **Suporte a Cursos**: Processa múltiplos vídeos de uma vez
- **Validação de URLs**: Valida automaticamente URLs do YouTube

## 🚀 Tecnologias Utilizadas

### Backend
- **Node.js** - Runtime JavaScript
- **Express.js** - Framework web
- **YouTube Transcript API** - Extração de transcrições
- **OpenAI API** - Geração de resumos com GPT
- **Claude API** - Geração de resumos com Claude
- **Axios** - Cliente HTTP
- **CORS** - Cross-origin resource sharing
- **Helmet** - Segurança HTTP
- **Morgan** - Logging de requisições

### Frontend
- **React** - Biblioteca JavaScript
- **Styled Components** - Estilização CSS-in-JS
- **Framer Motion** - Animações
- **React Icons** - Ícones
- **React Toastify** - Notificações
- **React JSON View** - Visualizador JSON
- **Axios** - Cliente HTTP

## 📋 Pré-requisitos

- **Node.js** 18.0.0 ou superior
- **npm** ou **yarn**
- **Conta OpenAI** (opcional, para resumos com GPT)
- **Conta Anthropic** (opcional, para resumos com Claude)

## 🛠️ Instalação

### 1. Clone o repositório

```bash
git clone https://github.com/juliopessoa/youtube-transcription-app.git
cd youtube-transcription-app
```

### 2. Instale as dependências

```bash
# Instalar dependências do backend e frontend
npm run install:all
```

### 3. Configure as variáveis de ambiente

```bash
# Copie o arquivo de exemplo
cp env.example .env

# Edite o arquivo .env com suas configurações
nano .env
```

**Exemplo de configuração do `.env`:**

```env
# Configurações do Servidor
PORT=3001
NODE_ENV=development

# APIs de IA (pelo menos uma é recomendada)
OPENAI_API_KEY=sk-your-openai-api-key-here
ANTHROPIC_API_KEY=sk-ant-your-claude-api-key-here

# Configurações de Segurança
CORS_ORIGIN=http://localhost:3000

# Configurações de Log
LOG_LEVEL=info
```

### 4. Obtenha suas chaves de API

#### OpenAI API Key
1. Acesse [OpenAI Platform](https://platform.openai.com/)
2. Faça login ou crie uma conta
3. Vá para "API Keys"
4. Clique em "Create new secret key"
5. Copie a chave e cole no `.env`

#### Claude API Key
1. Acesse [Anthropic Console](https://console.anthropic.com/)
2. Faça login ou crie uma conta
3. Vá para "API Keys"
4. Clique em "Create Key"
5. Copie a chave e cole no `.env`

## 🚀 Como Executar

### Desenvolvimento

```bash
# Terminal 1: Backend
npm run dev

# Terminal 2: Frontend (em outro terminal)
cd client
npm start
```

### Produção

```bash
# Construir o frontend
npm run build

# Iniciar servidor de produção
npm start
```

A aplicação estará disponível em:
- **Frontend**: http://localhost:3000
- **Backend**: http://localhost:3001

## 📖 Como Usar

### 1. Acesse a aplicação
Abra http://localhost:3000 no seu navegador

### 2. Configure o curso
- Digite o título do curso
- Adicione as URLs dos vídeos do YouTube
- (Opcional) Adicione títulos personalizados para os vídeos

### 3. Configure a IA
- Marque a opção "Usar IA para gerar resumos"
- Verifique o status das APIs de IA

### 4. Inicie a transcrição
- Clique em "Iniciar Transcrição"
- Acompanhe o progresso na barra
- Aguarde a conclusão do processamento

### 5. Visualize e baixe os resultados
- Visualize o JSON gerado
- Baixe o arquivo JSON completo

## 📁 Estrutura do Projeto

```
youtube-transcription-app/
├── client/                 # Frontend React
│   ├── public/
│   ├── src/
│   │   ├── App.js         # Componente principal
│   │   └── index.js       # Ponto de entrada
│   └── package.json
├── routes/                 # Rotas da API
│   ├── transcription.js   # Rotas de transcrição
│   └── ai.js             # Rotas de IA
├── services/              # Serviços
│   └── aiService.js      # Serviço de IA
├── server.js             # Servidor Express
├── package.json          # Dependências do backend
├── env.example           # Exemplo de variáveis de ambiente
└── README.md            # Este arquivo
```

## 🔧 Configurações Avançadas

### Personalizar Portas

Edite o arquivo `.env`:

```env
PORT=3001          # Porta do backend
REACT_APP_PORT=3000 # Porta do frontend
```

### Configurar CORS

Para permitir acesso de outros domínios:

```env
CORS_ORIGIN=https://seudominio.com
```

### Configurar Logs

```env
LOG_LEVEL=debug  # debug, info, warn, error
```

## 🐛 Solução de Problemas

### Erro: "Cannot find module"
```bash
# Reinstale as dependências
rm -rf node_modules package-lock.json
npm install
```

### Erro: "API key not configured"
- Verifique se as chaves de API estão corretas no `.env`
- Certifique-se de que o arquivo `.env` está na raiz do projeto

### Erro: "CORS policy"
- Verifique se o `CORS_ORIGIN` está configurado corretamente
- Em desenvolvimento, use `http://localhost:3000`

### Vídeos não transcritos
- Verifique se as URLs do YouTube são válidas
- Certifique-se de que os vídeos têm legendas disponíveis
- Alguns vídeos podem ter restrições de acesso

## 📊 Formato do JSON Gerado

```json
{
  "curso_oratoria": {
    "titulo": "Nome do Curso",
    "descricao": "Descrição do curso",
    "canal": "Nome do Canal",
    "instrutor": "Nome do Instrutor",
    "videos": [
      {
        "numero": 1,
        "titulo": "Título do Vídeo",
        "url": "URL do YouTube",
        "duracao": "12:34",
        "resumo": "Resumo gerado pela IA",
        "pontos_principais": ["Ponto 1", "Ponto 2"],
        "transcricao_completa": "Transcrição completa..."
      }
    ],
    "estatisticas": {
      "total_videos": 14,
      "videos_transcritos": 14,
      "tempo_total_estimado": "4:30:00",
      "temas_principais": ["Tema 1", "Tema 2"]
    }
  }
}
```

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📝 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 🙏 Agradecimentos

- [YouTube Transcript API](https://github.com/jdepoix/youtube-transcript-api) - Para extração de transcrições
- [OpenAI](https://openai.com/) - Para a API GPT
- [Anthropic](https://www.anthropic.com/) - Para a API Claude
- [React](https://reactjs.org/) - Para o framework frontend
- [Express](https://expressjs.com/) - Para o framework backend

## 📞 Suporte

Se você encontrar algum problema ou tiver dúvidas:

1. Verifique a seção [Solução de Problemas](#-solução-de-problemas)
2. Abra uma [Issue](https://github.com/juliopessoa/youtube-transcription-app/issues)
3. Entre em contato: [julio@example.com](mailto:julio@example.com)

---

**Desenvolvido com ❤️ por Julio Pessoa**