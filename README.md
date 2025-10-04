#!/usr/bin/env node
/**
 * Build a full fancy README.md for Scare Fun Bomb (13+ SFW)
 * Combines the intro/setup text with all commands from COMMANDS.md.
 */

import fs from "fs";
import path from "path";
import { fileURLToPath } from "url";

const __filename = fileURLToPath(import.meta.url);
const __dirname = path.dirname(__filename);
const ROOT = path.resolve(__dirname, "..");
const CMD_FILE = path.join(ROOT, "COMMANDS.md");
const OUT_FILE = path.join(ROOT, "README.md");

const intro = `\
<h1 align="center">💣 Scare Fun Bomb</h1>
<p align="center">
  <b>The ultimate fun + AI Discord bot — created by Scare 😈</b><br>
  <i>Over 1 000 commands of games, memes, AI art, utilities, and chaos — all 13+ SFW.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Discord.js-v14-blue?logo=discord&logoColor=white">
  <img src="https://img.shields.io/badge/Node.js-20.x-green?logo=node.js&logoColor=white">
  <img src="https://img.shields.io/badge/License-MIT-yellow">
</p>

---

## ✨ What Is Scare Fun Bomb?

**Scare Fun Bomb** is a mega Discord bot built to blow boredom out of existence 💣  
It’s packed with:
- 🎮 **Games** (rps, tictactoe, trivia, slots, hangman…)
- 😂 **Fun & Random** (jokes, roasts, memes, cat/furry pics — SFW)
- 🎨 **AI Creativity** (imagine, style, furrify, story, poem)
- 🌐 **Internet/API** (reddit, robloxuser, linktree, subscribe)
- 👥 **Social** (invite, help, avatar, poll)
- 🛡️ **Admin Tools** (safe, permission-locked moderation)
- 💫 **Generators** (randomcolor, randomfact, randomidea)
- 🧘 **Wellness** (breathe, hydrate, stretch)

All **13+ SFW**, safe, and scalable — ready for Railway hosting and GitHub CI/CD.

---

## ⚙️ Setup & Installation

\`\`\`bash
git clone https://github.com/<your-username>/scare-fun-bomb.git
cd scare-fun-bomb
npm install
\`\`\`

Create a \`.env\` file:

\`\`\`
DISCORD_TOKEN=your_bot_token
DISCORD_CLIENT_ID=your_app_client_id
DEV_GUILD_ID=your_server_id
OPENAI_API_KEY=your_openai_api_key
OWNER_IDS=your_discord_id
BOT_NAME=Scare Fun Bomb
\`\`\`

Register commands & start:

\`\`\`bash
npm run dev:register
npm start
\`\`\`

Deploy easily with **Railway** → connect your GitHub repo, add the same \`.env\` vars.

---

## 🧱 Project Structure
\`\`\`
scare-fun-bomb/
├─ src/
│  ├─ commands/
│  ├─ utils/
│  ├─ index.js
│  └─ deploy-commands.js
├─ .env
├─ .gitignore
├─ package.json
├─ README.md
└─ COMMANDS.md
\`\`\`

---

## 🛡️ Security

✅ No dangerous perms (\`Administrator\` not required)  
✅ Owner-only restricted commands (via \`OWNER_IDS\`)  
✅ Cooldowns & input validation  
✅ SFW filtering for APIs and AI image prompts  
✅ Never commit \`.env\` — use \`.gitignore\` (and Railway Variables)

---

## 📜 License
MIT © 2025 Scare

---

## 💥 Full Command Reference (all categories)
`;

if (!fs.existsSync(CMD_FILE)) {
  console.error("❌ COMMANDS.md not found in project root.");
  process.exit(1);
}

const commands = fs.readFileSync(CMD_FILE, "utf8");
fs.writeFileSync(OUT_FILE, intro + "\n" + commands, "utf8");

console.log(`✅  README.md built successfully at ${OUT_FILE}`);
