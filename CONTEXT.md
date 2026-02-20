# SolutionsAxionaAI — Contexto del Proyecto

## ¿Qué es este proyecto?
Es un fork de **OpenClaw** (asistente AI personal de código abierto) adaptado como producto propio bajo la marca **SolutionsAxionaAI**, propiedad de **josechirinos11**.

## Repositorio
- **Original:** https://github.com/openclaw/openclaw
- **Este fork:** https://github.com/josechirinos11/Agente__SolutionsAxionaAI

## Cambios de marca realizados (Nivel 1 — Interfaz visible)

| Archivo | Cambio |
|---------|--------|
| `ui/index.html` | Título del navegador → `SolutionsAxionaAI` |
| `ui/src/ui/app-render.ts` | Logo alt y título del dashboard → `SolutionsAxionaAI` |
| `src/cli/banner.ts` | Banner del CLI reemplazado con arte ASCII propio |
| `src/canvas-host/server.ts` | Título de página canvas → `SolutionsAxionaAI Canvas` |
| `assets/chrome-extension/manifest.json` | Nombre extensión Chrome → `SolutionsAxionaAI Browser Relay` |
| `extensions/matrix/src/matrix/client/config.ts` | Dispositivo Matrix → `SolutionsAxionaAI Gateway` |
| `src/infra/bonjour.ts` | Nombre mDNS → `SolutionsAxionaAI` |
| `README.md` | Título, badges, links y créditos actualizados |

## Cambios pendientes (Nivel 2 — Internos)
- Variables de entorno `OPENCLAW_*` → mantener por ahora (renombrar rompe dependencias)
- Directorio `~/.openclaw/` → configurable con `OPENCLAW_STATE_DIR`
- Nombre del binario CLI `openclaw` → pendiente de renombrar
- Paquetes internos `@openclaw/*` → pendiente

## Instalación local (desarrollo)
```bash
# Prerrequisitos
nvm install 22          # Node.js 22+
npm install -g pnpm     # pnpm 10+

# Proyecto instalado en:
/home/user/solutionsaxionaai/

# Construir
cd /home/user/solutionsaxionaai
pnpm install
pnpm build
pnpm ui:build
npm install -g .        # instala comando `openclaw` globalmente
```

## Configuración (~/.openclaw/)
```
~/.openclaw/
├── .env               # API keys y token del gateway
└── openclaw.json      # Modelo de IA configurado
```

### ~/.openclaw/.env
```
GEMINI_API_KEY=...                    # API key de Google (problemas de cuota)
OPENCLAW_GATEWAY_TOKEN=aeb7ea39...    # Token de seguridad del gateway
```

### ~/.openclaw/openclaw.json
```json
{
  "agents": {
    "defaults": {
      "model": { "primary": "google/gemini-2.0-flash" }
    }
  },
  "gateway": { "mode": "local" }
}
```

## Estado actual del proveedor de IA
- **Gemini API** — cuota gratuita bloqueada (limit: 0) en la cuenta del usuario
- **Pendiente:** configurar OpenRouter con modelo gratuito (`meta-llama/llama-3.1-8b-instruct:free`)
- Para OpenRouter: cambiar `OPENROUTER_API_KEY` en `.env` y modelo en `openclaw.json`

## Arrancar el gateway
```bash
source ~/.nvm/nvm.sh
openclaw gateway --port 18789
# Abrir: http://127.0.0.1:18789/?token=aeb7ea39b9e39fe605cb2ee4b651b485ebd289fb03082e659a2715c9f46ab3bc
```

## Tecnología base
- **Runtime:** Node.js 22, TypeScript, pnpm monorepo
- **Gateway:** WebSocket en puerto 18789
- **UI:** Lit (Web Components), Vite
- **Canales soportados:** WhatsApp, Telegram, Slack, Discord, Signal, iMessage, Teams, Matrix, Zalo, WebChat
- **Modelos soportados:** Anthropic, OpenAI, Google Gemini, OpenRouter, AWS Bedrock, etc.

## Propietario
- **Usuario:** josechirinos11
- **Email:** josechirinos11@gmail.com
