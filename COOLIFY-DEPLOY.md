# Deploy n8n-alves com Coolify

## 🚀 Setup no Coolify

### 1. Preparar Repositório
```bash
git add docker-compose-prod.yaml .env.example COOLIFY-DEPLOY.md
git commit -m "feat: Add production deployment files for Coolify"
git push
```

### 2. Configurar Coolify
1. **Acessar** seu painel Coolify
2. **Adicionar** GitHub como source
3. **Selecionar** repositório `brunoalves20024/n8n-alves`
4. **Criar** novo projeto:
   - **Type**: Docker Compose
   - **Compose File**: `docker-compose-prod.yaml`
   - **Environment**: Production

### 3. Variáveis de Ambiente
Copiar `.env.example` e configurar no Coolify:
```bash
POSTGRES_DB=n8n
POSTGRES_USER=n8n
POSTGRES_PASSWORD=sua_senha_super_segura_aqui
N8N_BASIC_AUTH_USER=seu_email@dominio.com
N8N_BASIC_AUTH_PASSWORD=sua_senha_super_segura_aqui
N8N_HOST=seu-dominio.com
WEBHOOK_URL=https://seu-dominio.com/
```

### 4. Configurações de Deploy
- **Port**: 5678 (ou 80/443 se usar Nginx)
- **Health Check**: `/healthz`
- **Auto-deploy**: ✅ Ativar
- **SSL**: ✅ Ativar Let's Encrypt

## 🔧 Configurações Avançadas

### Domínio Personalizado
1. **DNS**: Apontar `seu-dominio.com` para IP do servidor
2. **Coolify**: Configurar domínio no projeto
3. **SSL**: Automático via Let's Encrypt

### Backup Automático
- **PostgreSQL**: `pg_dump` diário
- **n8n**: Backup do volume `n8n_data`
- **Storage**: S3/Backblaze (configurar no Coolify)

### Monitoramento
- **Logs**: Via interface Coolify
- **Métricas**: N8N Metrics ativado
- **Alertas**: Email/Slack (configurar)

## 🛡️ Segurança

### Senhas Fortes
```bash
# Gerar senhas seguras
openssl rand -base64 32
```

### Firewall
```bash
# No servidor Linux
ufw allow 22    # SSH
ufw allow 80    # HTTP
ufw allow 443   # HTTPS
ufw enable
```

### Updates Automáticos
- **Coolify**: Auto-update containers
- **Security**: Patch semanal automático

## 📊 Performance

### Recursos Recomendados
- **CPU**: 2+ cores
- **RAM**: 4GB+
- **Storage**: 50GB+ SSD

### PostgreSQL Tuning
```yaml
# Adicionar ao docker-compose-prod.yaml
environment:
  - POSTGRES_SHARED_PRELOAD_LIBRARIES=pg_stat_statements
  - POSTGRES_MAX_CONNECTIONS=200
  - POSTGRES_SHARED_BUFFERS=256MB
  - POSTGRES_EFFECTIVE_CACHE_SIZE=1GB
```

## 🔄 CI/CD Pipeline

### Branch Strategy
- **main** → Produção
- **develop** → Staging
- **feature/*** → Development

### Auto-deploy Rules
```yaml
# .coolify/deploy.yml
main:
  auto_deploy: true
  environment: production
develop:
  auto_deploy: false
  environment: staging
```

## 🚨 Troubleshooting

### Logs Rápidos
```bash
# Via Coolify UI ou SSH
docker-compose logs -f n8n
docker-compose logs -f postgres
```

### Reset Completo
```bash
# Apenas se necessário
docker-compose down -v
docker-compose up -d
```

### Performance Issues
1. **Check** recursos do servidor
2. **Monitor** PostgreSQL connections
3. **Review** workflow complexity
4. **Scale** horizontal se necessário

---

**Próximo passo:** Configure no Coolify e faça primeiro deploy! 🚀
