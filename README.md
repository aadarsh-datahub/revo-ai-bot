#  Pixel — AI Chatbot with Smart GIF Reactions
Pixel is a friendly AI companion chatbot built with **TanStack Start**, **React 19**, and **Tailwind CSS v4**.
It features a cute walking companion character on a beautiful dark animated background, and every reply comes with a relevant reaction GIF fetched from Tenor.
> Created by **AADARSH MISHRA**
---
##  Features
-  **Conversational AI** powered by `google/gemini-3-flash-preview` via the Lovable AI Gateway
-  **Smart GIF reactions** — every answer is paired with a context-aware GIF from Tenor
-  **Walking companion (Pixel)** — animated SVG character that walks across a dark starry scene
-  **Beautiful dark UI** — gradient sky, moon glow, stars, mountains, and animated hills
-  **Server functions** using `createServerFn` (TanStack Start) — no Edge Functions needed
-  Backend powered by **Lovable Cloud**
---
## 🛠️ Tech Stack
| Layer        | Tech                                       |
| ------------ | ------------------------------------------ |
| Framework    | TanStack Start v1 + React 19               |
| Build tool   | Vite 7                                     |
| Styling      | Tailwind CSS v4 (via `src/styles.css`)     |
| UI Kit       | shadcn/ui + Lucide icons                   |
| AI Model     | `google/gemini-3-flash-preview` (Lovable AI Gateway) |
| GIFs         | Tenor public API                           |
| Backend      | Lovable Cloud (Supabase under the hood)    |
| Deploy       | Cloudflare Workers (edge)                  |
---
## 🚀 Getting Started
### 1. Clone
```bash
git clone <your-repo-url>
cd <your-repo>
```
### 2. Install dependencies
```bash
bun install
# or
npm install
```
### 3. Environment variables
Create a `.env` file in the project root (values are provided by Lovable Cloud automatically when running on Lovable):
```env
VITE_SUPABASE_URL="https://<your-project>.supabase.co"
VITE_SUPABASE_PUBLISHABLE_KEY="<your-anon-key>"
VITE_SUPABASE_PROJECT_ID="<your-project-id>"
SUPABASE_URL="https://<your-project>.supabase.co"
SUPABASE_PUBLISHABLE_KEY="<your-anon-key>"
# Required at runtime for the AI chat server function
LOVABLE_API_KEY="<your-lovable-ai-gateway-key>"
```
> `LOVABLE_API_KEY` is auto-injected when using Lovable Cloud. For self-hosting, generate one in your Lovable workspace settings.
### 4. Run the dev server
```bash
bun run dev
```
Open <http://localhost:5173>.
---
##  Project Structure
```
src/
├── components/
│   ├── ChatBox.tsx        # Main chat UI
│   ├── Companion.tsx      # Walking Pixel character + dark scene
│   └── ui/                # shadcn/ui components
├── server/
│   └── chat.functions.ts  # Server function: AI + Tenor GIF fetch
├── routes/
│   ├── __root.tsx         # Root layout
│   └── index.tsx          # Home page ("Meet Pixel")
├── integrations/supabase/ # Auto-generated Supabase clients
└── styles.css             # Tailwind v4 + design tokens + keyframes
```
---
##  How It Works
1. The user types a question in `ChatBox`.
2. The frontend calls the `chatWithGif` server function.
3. The server calls the Lovable AI Gateway with a forced tool call (`reply_with_gif`) so the model returns both an `answer` and a `gifKeyword`.
4. The server fetches a random matching GIF from Tenor.
5. The response (`{ answer, gifKeyword, gifUrl }`) is rendered, and Pixel's mood/animation updates.
If you ask Pixel *"who made you?"*, it will always reply: **AADARSH MISHRA MADE ME** 😎
---
##  Deployment
This project is configured for **Cloudflare Workers** via `wrangler.jsonc`.
You can also deploy directly from Lovable with one click — **Publish** in the editor.
---
##  License
MIT — see [LICENSE](./LICENSE).
---
##  Credits
- Built by **AADARSH MISHRA**
- GIFs by [Tenor](https://tenor.com)
