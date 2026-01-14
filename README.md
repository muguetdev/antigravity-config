# Antigravity Config

Repositório de configuração remota do [Antigravity Browser](https://github.com/muguetdev/antigravity).

## 📋 Estrutura

### `config.json`

Arquivo principal de configuração de feature flags e estado do beta.

```json
{
  "version": "1.0.9",
  "updatedAt": "2026-01-14T01:00:00Z",
  "beta": {
    "active": true,
    "message": "🚀 Antigravity está em BETA ABERTO...",
    "expiresAt": null
  },
  "flags": {
    "profiles_unlimited": true,
    "cookie_import": true,
    ...
  }
}
```

## 🚩 Feature Flags

### Beta Features (ativas durante beta)
- `profiles_unlimited` - Perfis ilimitados
- `cookie_import` - Importação de cookies
- `multi_tab` - Múltiplas abas por perfil

### Premium Features (waitlist/desativadas)
- `cloud_sync` - Sincronização na nuvem
- `team_workspace` - Workspaces compartilhados
- `api_access` - API para automação
- `proxy_integration` - Integração de proxies

### System Flags
- `force_update` - Forçar atualização obrigatória
- `maintenance_mode` - Modo manutenção
- `kill_switch` - 🚨 Emergência: desliga features críticas em caso de bug/exploit

## 🔧 Como funciona

1. **Fetch remoto**: App busca este config ao iniciar
2. **Cache local**: Guarda em cache por 1 hora
3. **Fallback**: Se falhar, usa config local padrão
4. **Refresh**: Pode forçar refresh via IPC

## 🎯 Uso

O app consulta:
```
https://raw.githubusercontent.com/muguetdev/antigravity-config/main/config.json
```

**Sem necessidade de rebuild** para mudanças de features.

## ⚠️ Importante

- Mudanças aqui afetam TODOS os usuários ativos
- Sempre testar localmente antes de commitar
- `beta.active = false` = sai do beta (impacto grande)
- `force_update = true` = obriga todos a atualizarem

## 🔐 Segurança

- Repositório público (read-only para usuários)
- Apenas maintainers podem modificar
- Apps validam estrutura antes de aplicar
- Cache local previne lock-out se GitHub cair

---

**Versão atual**: 1.0.9  
**Última atualização**: 2026-01-14
