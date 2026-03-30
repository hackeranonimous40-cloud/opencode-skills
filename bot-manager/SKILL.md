---
name: bot-manager
description: Gestión del bot de WhatsApp - start, stop, restart, status
license: MIT
compatibility: opencode
metadata:
  audience: users
  workflow: automation
---

# Bot Manager

Gestión del bot de WhatsApp OpenCarbo.

## Ubicación del script

El script de gestión está en: `/media/disco1tb/mcp-opencode-bot/run.sh`

## Comandos disponibles

| Comando | Descripción |
|---------|-------------|
| `./run.sh start` | Inicia todos los servicios con auto-reinicio |
| `./run.sh stop` | Detiene todos los servicios |
| `./run.sh restart` | Reinicia todos los servicios |
| `./run.sh status` | Muestra estado de todos los servicios |

## Cómo usar

Para ejecutar comandos, usa:
```bash
cd /media/disco1tb/mcp-opencode-bot && ./run.sh [comando]
```

## Auto-reinicio

El bot tiene auto-reinicio habilitado cuando se inicia con `./run.sh start`:
- Usa un loop `while true; do node bot.js; done` 
- Si el bot muere, se reinicia automáticamente en 2 segundos
- El self-healing interno también detecta y recovering errores

## Estado de servicios

Usa `./run.sh status` para ver:
- OpenCode Server
- Bot
- Bridge (OpenCode)
- Watcher (Cámara)
- Monitor
- Admin Panel (puerto 3000)
- Self-Healing System

## Cuándo usar

- Si el usuario dice que el bot está muerto → verificar con `./run.sh status`
- Si el bot está inactivo → reiniciar con `./run.sh start`
- Para ver qué servicios están corriendo → `./run.sh status`

## Notas importantes

- SIEMPRE usa `./run.sh start` para iniciar, NO `node bot.js` directo
- El auto-reinicio solo funciona con el loop del run.sh
- El self-healing interno del bot es complementario, no sustituye el loop
