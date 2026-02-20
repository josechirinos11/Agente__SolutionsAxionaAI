 1. Instalar en tu PC (obligatorio)                                                                                                                                                ┌─────────────┬────────────────┬─────────────────────┐                                   │ Herramienta │ Version minima │    Como instalar    │                                   ├─────────────┼────────────────┼─────────────────────┤                                   │ Node.js     │ 22.12.0+       │ https://nodejs.org  │                                 
  ├─────────────┼────────────────┼─────────────────────┤
  │ pnpm        │ 10.23.0+       │ npm install -g pnpm │
  ├─────────────┼────────────────┼─────────────────────┤
  │ Git         │ cualquiera     │ ya lo tienes        │
  └─────────────┴────────────────┴─────────────────────┘

  ---
  2. Crear tu archivo de configuracion

  Crea el archivo ~/.openclaw/.env con tus claves. Al menos una API de IA es obligatoria:

  # ~/.openclaw/.env

  # === OBLIGATORIO: elige al menos uno ===
  ANTHROPIC_API_KEY=sk-ant-...        # Claude (recomendado)
  # OPENAI_API_KEY=sk-...             # ChatGPT
  # GEMINI_API_KEY=...                # Google Gemini

  # === SEGURIDAD del Gateway ===
  OPENCLAW_GATEWAY_TOKEN=pon-aqui-un-token-largo-y-aleatorio

  # === CANALES (opcionales, solo los que vayas a usar) ===
  # TELEGRAM_BOT_TOKEN=123456:ABCDEF...
  # DISCORD_BOT_TOKEN=...
  # SLACK_BOT_TOKEN=xoxb-...
  # SLACK_APP_TOKEN=xapp-...

  # === HERRAMIENTAS OPCIONALES ===
  # BRAVE_API_KEY=...                 # Busqueda web
  # ELEVENLABS_API_KEY=...            # Voz
  # FIRECRAWL_API_KEY=...             # Scraping web

  ---
  3. Construir e instalar desde tu repositorio

  # Clonar TU repo
  git clone https://github.com/josechirinos11/Agente__SolutionsAxionaAI.git
  cd Agente__SolutionsAxionaAI

  # Instalar dependencias
  pnpm install

  # Construir
  pnpm build

  # Instalar globalmente en tu PC
  npm install -g .

  # Configurar el agente
  openclaw onboard --install-daemon

  ---
  4. Lo que se crea automaticamente fuera del repo

  ~/.openclaw/
  ├── .env                  ← tus claves (lo creas tú)
  ├── openclaw.json         ← config del agente (se genera)
  ├── workspace/            ← sesiones y datos del agente
  ├── credentials/          ← tokens OAuth de canales
  └── logs/                 ← logs del gateway

  ---
  5. Cambio pendiente importante: el nombre del binario

  Actualmente el comando que se ejecuta en terminal es openclaw. Para que sea tu propio
  producto deberias cambiarlo en package.json:

  "bin": {
    "solutionsaxionaai": "openclaw.mjs"   ← cambiar esto
  }

  Esto requiere un cambio en el codigo + reconstruir. ¿Quieres que lo haga ahora?        

  ---
  Resumen rapido: checklist para empezar

  - Instalar Node.js 22+
  - Instalar pnpm
  - Crear ~/.openclaw/.env con tu API key de Anthropic u OpenAI
  - Clonar tu repo y ejecutar pnpm install && pnpm build
  - Ejecutar openclaw onboard --install-daemon
  - Abrir http://127.0.0.1:18789 en el navegador
