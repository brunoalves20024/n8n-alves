# n8n-alves - N8N com PostgreSQL

Este é um fork do n8n com configuração otimizada para PostgreSQL, fornecendo persistência de dados e performance superior para automação de workflows.

## 🚀 Início Rápido

### Pré-requisitos
- Docker e Docker Compose instalados
- Node.js 22+ (para desenvolvimento local)

### Com Docker (Recomendado)

1. **Iniciar os serviços:**
```bash
docker-compose -f docker-compose-postgres.yaml up -d
```

2. **Acessar o n8n:**
- URL: http://localhost:5678
- Usuário: `admin`
- Senha: `admin_password`

3. **Verificar status:**
```bash
docker-compose -f docker-compose-postgres.yaml ps
```

### Parar os serviços:
```bash
docker-compose -f docker-compose-postgres.yaml down
```

## 🐘 Configuração PostgreSQL

### Variáveis de Ambiente
- `DB_TYPE=postgresdb` - Tipo de banco de dados
- `DB_POSTGRESDB_HOST=postgres` - Host do PostgreSQL
- `DB_POSTGRESDB_PORT=5432` - Porta do PostgreSQL
- `DB_POSTGRESDB_DATABASE=n8n` - Nome do banco
- `DB_POSTGRESDB_USER=n8n` - Usuário do banco
- `DB_POSTGRESDB_PASSWORD=n8n_password` - Senha do banco

### Volumes de Dados
- `postgres_data` - Dados persistentes do PostgreSQL
- `n8n_data` - Configurações e workflows do n8n

## 🔧 Desenvolvimento Local

### Instalar dependências:
```bash
pnpm install
```

### Build do projeto:
```bash
pnpm build
```

### Executar testes:
```bash
pnpm test
```

### Lint e typecheck:
```bash
pnpm lint
pnpm typecheck
```

## 🌐 Serviços

| Serviço | Porta | Descrição |
|---------|------|-----------|
| n8n | 5678 | Interface web do n8n |
| PostgreSQL | 5432 | Banco de dados |

## 🔒 Segurança

- Autenticação básica configurada
- Senhas personalizáveis no docker-compose
- Dados persistidos em volumes Docker

## 📈 Benefícios do PostgreSQL

- ✅ **Persistência real** - Dados sobrevivem a reinicializações
- ✅ **Performance superior** - Otimizado para grandes volumes
- ✅ **Concorrência** - Múltiplos usuários simultâneos
- ✅ **Backup fácil** - Ferramentas PostgreSQL nativas
- ✅ **Escalabilidade** - Suporte a clustering

## 🤝 Contribuições

Este fork inclui:
- Configuração Docker otimizada
- PostgreSQL integrado
- Health checks automatizados
- Documentação melhorada

## 📝 Licença

Mantida a licença original do n8n (Sustainable Use License).

---

**Acesso rápido:** http://localhost:5678
