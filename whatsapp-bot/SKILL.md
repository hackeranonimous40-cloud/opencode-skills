---
name: whatsapp-bot
description: Controla el bot de WhatsApp - enviar mensajes, cambiar modos, tomar fotos
license: MIT
compatibility: opencode
metadata:
  audience: users
  workflow: automation
---

## Qué hago

Permito controlar el bot de WhatsApp para:
- Enviar mensajes a través del bridge de WhatsApp
- Cambiar entre modos (bot, auto, code)
- Tomar fotos de la cámara
- Consultar estado del sistema
- Ejecutar comandos locales

## Cómo funcionan los modos

- **modo bot**: Comandos locales (foto, status, abre, YouTube)
- **modo auto**: IA autónoma con visión (comandos "haz [tarea]")
- **modo code**: Chat directo con OpenCode (todo va a IA)

## Para cambiar modo

Usa estos comandos en WhatsApp:
- "modo bot" → Cambiar a comandos locales
- "modo auto" → Cambiar a IA autónoma
- "modo code" → Cambiar a OpenCode

## Cuándo usarme

Usa esta skill cuando:
- Necesites enviar mensajes via WhatsApp
- Quieras controlar el sistema desde WhatsApp
- Necesites cambiar el modo de operación del bot
- Quieras tomar fotos o consultar status

## Herramientas disponibles

El bot proporciona:
- Envío de mensajes de texto
- Cambio de modos
- Captura de pantalla/fotos
- Control de aplicaciones
- Consulta de estado del sistema

## ⚠️ IMPORTANTE: Cómo enviar imágenes

**NUNCA intentes ejecutar `scrot` o `grim` directamente.** 

### Para tomar y enviar una captura de pantalla:

Simplemente **envía el texto "captura pantalla"** como mensaje de WhatsApp. El bot lo detectará automáticamente y:
1. Tomará la captura
2. La procesará
3. Te la enviará directamente

### Ejemplo:

Cuando el usuario dice "Mándame una captura", simplemente responde con el mensaje de texto:
```
captura pantalla
```

**NO** делаешь esto (incorrecto):
```bash
scrot /ruta/imagen.png
# ❌ NO FUNCIONA - el bot no detecta esto automáticamente
```

**SÍ** делаешь esto (correcto):
Simplemente envía "captura pantalla" como mensaje de texto y el bot lo procesará.

### Por qué esto funciona:

El bot tiene un detector que cuando recibe el texto "captura pantalla" (de cualquier fuente, incluso del bridge de OpenCode), ejecuta la función `takeScreenshot()` internamente Y ENVÍA la imagen automáticamente.
