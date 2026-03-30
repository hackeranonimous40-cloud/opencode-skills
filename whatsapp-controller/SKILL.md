---
name: whatsapp-controller
description: Controlar dos cuentas de WhatsApp - enviar mensajes, verificar estado
license: MIT
compatibility: opencode
metadata:
  audience: users
  workflow: automation
---

# WhatsApp Controller

Controla dos cuentas de WhatsApp desde aquí.

## Configuración

| Cuenta | Puerto | JID Envío |
|--------|--------|-----------|
| Bot (50686118790) | 3000 | 196838602834105@lid |
| Owner (50662027144) | 3002 | 50686118790@s.whatsapp.net |

## Enviar Mensajes

### Desde Bot al Owner (número principal):

```bash
curl -s http://localhost:3000/admin/send -X POST -H "Content-Type: application/json" -H "X-Admin-Key: change_this_to_secure_key" -d '{"jid": "196838602834105@lid", "message": "Tu mensaje"}'
```

### Desde Owner al Bot:

```bash
curl -s http://localhost:3002/admin/send -X POST -H "Content-Type: application/json" -H "X-Admin-Key: change_this_to_secure_key" -d '{"jid": "50686118790@s.whatsapp.net", "message": "Tu mensaje"}'
```

## Verificar Estado

```bash
# Ver si Bot está activo
curl -s http://localhost:3000/admin/health

# Ver si Owner está activo
curl -s http://localhost:3002/admin/health
```

## Errores Comunes

- Si el mensaje no llega, verificar el JID correcto
- Formatos de JID:
  - `@lid` = número principal
  - `@s.whatsapp.net` = número secundario

## Notes

- Puerto 3000 = Bot principal
- Puerto 3001 = Bridge
- Puerto 3002 = Owner (segunda sesión)
