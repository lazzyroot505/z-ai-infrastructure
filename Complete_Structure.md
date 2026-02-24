# Z.ai Internal Infrastructure - Complete Structure

**Generated:** February 2024
**Version:** 1.0.0
**Archive File:** `z-ai-infrastructure-complete.tar.gz` (373 KB)

---

## 📁 Directory Overview

```
z-ai-infrastructure/
├── README.md                    # Main documentation
├── COMPLETE_STRUCTURE.md        # This file - complete file listing
├── source-code/                 # Frontend & Backend source code
├── skills/                      # AI Skills & Capabilities
├── shell-scripts/               # Build & Deployment scripts
├── configuration/               # Project configuration files
├── examples/                    # Example implementations
└── python-packages/             # Python dependencies
```

---

## 📂 Detailed File Structure

### 1. SOURCE CODE (`source-code/`)

#### Frontend - App Router (`app/`)
| File | Description |
|------|-------------|
| `page.tsx` | Main landing page component |
| `layout.tsx` | Root layout with fonts, metadata, and theme |
| `globals.css` | Global CSS with Tailwind and design tokens |
| `api/route.ts` | API route handler (GET endpoint) |

#### Frontend - UI Components (`components/ui/`)
| File | Description |
|------|-------------|
| `accordion.tsx` | Collapsible content panels |
| `alert-dialog.tsx` | Modal alerts with confirmations |
| `alert.tsx` | Inline alert notifications |
| `aspect-ratio.tsx` | Responsive container with fixed ratio |
| `avatar.tsx` | User avatar component |
| `badge.tsx` | Status badges and labels |
| `breadcrumb.tsx` | Navigation breadcrumb trail |
| `button.tsx` | Primary interactive button |
| `calendar.tsx` | Date picker calendar |
| `card.tsx` | Content card container |
| `carousel.tsx` | Image/content slider |
| `checkbox.tsx` | Checkbox input |
| `collapsible.tsx` | Show/hide content |
| `command.tsx` | Command palette (Cmd+K) |
| `context-menu.tsx` | Right-click context menu |
| `dialog.tsx` | Modal dialog |
| `drawer.tsx` | Side drawer panel |
| `dropdown-menu.tsx` | Dropdown navigation |
| `form.tsx` | Form wrapper with validation |
| `hover-card.tsx` | Hover tooltip card |
| `input-otp.tsx` | One-time password input |
| `input.tsx` | Text input field |
| `label.tsx` | Form label |
| `menubar.tsx` | Application menu bar |
| `navigation-menu.tsx` | Site navigation |
| `pagination.tsx` | Page navigation |
| `popover.tsx` | Floating popover |
| `progress.tsx` | Progress indicator |
| `radio-group.tsx` | Radio button group |
| `resizable.tsx` | Resizable panels |
| `scroll-area.tsx` | Custom scrollbar container |
| `select.tsx` | Dropdown select |
| `separator.tsx` | Horizontal/vertical divider |
| `sheet.tsx` | Side sheet modal |
| `sidebar.tsx` | Application sidebar |
| `skeleton.tsx` | Loading placeholder |
| `slider.tsx` | Range slider |
| `sonner.tsx` | Toast notifications |
| `switch.tsx` | Toggle switch |
| `table.tsx` | Data table |
| `tabs.tsx` | Tabbed content |
| `textarea.tsx` | Multi-line text input |
| `toast.tsx` | Toast notification |
| `toaster.tsx` | Toast container |
| `toggle-group.tsx` | Toggle button group |
| `toggle.tsx` | Toggle button |
| `tooltip.tsx` | Hover tooltip |
| `chart.tsx` | Data visualization charts |

#### Frontend - Hooks (`hooks/`)
| File | Description |
|------|-------------|
| `use-mobile.ts` | Detect mobile viewport |
| `use-toast.ts` | Toast notification state management |

#### Backend - Lib (`lib/`)
| File | Description |
|------|-------------|
| `db.ts` | Prisma database client |
| `utils.ts` | Utility functions (cn() for class merging) |

---

### 2. AI SKILLS (`skills/`)

#### ASR (Automatic Speech Recognition)
| File | Description |
|------|-------------|
| `SKILL.md` | Speech-to-text capability guide |
| `scripts/asr.ts` | ASR implementation using z-ai SDK |
| `LICENSE.txt` | MIT License |

#### LLM (Large Language Model)
| File | Description |
|------|-------------|
| `SKILL.md` | Chat completions guide |
| `scripts/chat.ts` | LLM chat implementation |
| `LICENSE.txt` | MIT License |

#### TTS (Text-to-Speech)
| File | Description |
|------|-------------|
| `SKILL.md` | TTS capability guide |
| `tts.ts` | Text-to-speech implementation |
| `LICENSE.txt` | MIT License |

#### VLM (Vision Language Model)
| File | Description |
|------|-------------|
| `SKILL.md` | Vision chat capability guide |
| `scripts/vlm.ts` | Vision model implementation |
| `LICENSE.txt` | MIT License |

#### Image Generation
| File | Description |
|------|-------------|
| `SKILL.md` | AI image generation guide |
| `scripts/image-generation.ts` | Image generation using z-ai SDK |
| `LICENSE.txt` | MIT License |

#### Video Generation
| File | Description |
|------|-------------|
| `SKILL.md` | AI video generation guide |
| `scripts/video.ts` | Video generation implementation |
| `LICENSE.txt` | MIT License |

#### Video Understanding
| File | Description |
|------|-------------|
| `SKILL.md` | Video analysis capability guide |
| `scripts/video-understand.ts` | Video understanding implementation |
| `LICENSE.txt` | MIT License |

#### Web Search
| File | Description |
|------|-------------|
| `SKILL.md` | Web search capability guide |
| `scripts/web_search.ts` | Web search implementation |
| `LICENSE.txt` | MIT License |

#### Web Reader
| File | Description |
|------|-------------|
| `SKILL.md` | Web page content extraction guide |
| `scripts/web-reader.ts` | Page reader implementation |
| `LICENSE.txt` | MIT License |

#### PDF Processing
| File | Description |
|------|-------------|
| `SKILL.md` | PDF manipulation guide |
| `reference.md` | Detailed PDF reference |
| `forms.md` | PDF form filling guide |
| `scripts/*.py` | Python PDF utilities |
| `LICENSE.txt` | Proprietary License |

#### DOCX (Word Documents)
| File | Description |
|------|-------------|
| `SKILL.md` | Word document creation/editing guide |
| `docx-js.md` | JavaScript docx library guide |
| `ooxml.md` | OOXML editing documentation |
| `scripts/*.py` | Python document utilities |
| `ooxml/schemas/*.xsd` | OOXML schema definitions |
| `LICENSE.txt` | Proprietary License |

#### XLSX (Excel Spreadsheets)
| File | Description |
|------|-------------|
| `SKILL.md` | Excel file guide |
| `recalc.py` | Formula recalculation script |
| `LICENSE.txt` | Proprietary License |

#### PPTX (PowerPoint)
| File | Description |
|------|-------------|
| `SKILL.md` | PowerPoint handling guide |

#### Finance
| File | Description |
|------|-------------|
| `SKILL.md` | Finance API integration guide |
| `Finance_API_Doc.md` | API documentation |

#### Podcast Generate
| File | Description |
|------|-------------|
| `SKILL.md` | Podcast generation capability |
| `generate.ts` | TypeScript podcast generator |
| `package.json` | Node.js dependencies |
| `tsconfig.json` | TypeScript config |
| `test_data/segments.jsonl` | Test data |

#### Frontend Design
| File | Description |
|------|-------------|
| `SKILL.md` | Frontend design system guide |
| `README.md` | Usage documentation |
| `package.json` | Dependencies |
| `examples/css/*.css` | CSS design tokens & components |
| `examples/typescript/*.tsx` | TS component examples |
| `templates/*.css` | Quick-start templates |

#### Gift Evaluator
| File | Description |
|------|-------------|
| `SKILL.md` | Gift analysis capability |
| `html_tools.py` | HTML card generation |

---

### 3. SHELL SCRIPTS (`shell-scripts/`)

| File | Description |
|------|-------------|
| `build.sh` | Full-stack build script for Next.js + mini-services |
| `start.sh` | Production server startup with Caddy |
| `mini-services-build.sh` | Build mini-services from package.json |
| `mini-services-install.sh` | Install dependencies for mini-services |
| `mini-services-start.sh` | Start all mini-services |

---

### 4. CONFIGURATION (`configuration/`)

| File | Description |
|------|-------------|
| `package.json` | NPM dependencies and scripts |
| `tsconfig.json` | TypeScript compiler configuration |
| `next.config.ts` | Next.js configuration (standalone output) |
| `tailwind.config.ts` | Tailwind CSS with design tokens |
| `postcss.config.mjs` | PostCSS configuration |
| `eslint.config.mjs` | ESLint configuration |
| `components.json` | shadcn/ui component configuration |
| `Caddyfile` | Caddy reverse proxy configuration |
| `.env` | Environment variables |
| `.gitignore` | Git ignore patterns |
| `schema.prisma` | Prisma database schema (SQLite) |

---

### 5. EXAMPLES (`examples/`)

#### WebSocket
| File | Description |
|------|-------------|
| `frontend.tsx` | React WebSocket chat client |
| `server.ts` | Node.js WebSocket server |

---

### 6. PYTHON PACKAGES (`python-packages/`)

| File | Description |
|------|-------------|
| `pyproject.toml` | Python 3.12 dependencies (197 packages) |

**Key Python Packages Include:**
- Data Science: numpy, pandas, scipy, matplotlib, seaborn
- Machine Learning: scikit-learn, xgboost, lightgbm, catboost
- NLP: nltk, spacy, gensim, textblob
- Web: fastapi, gradio, websockets, playwright
- Document Processing: python-docx, python-pptx, openpyxl, pypdf
- Audio/Video: moviepy, pydub, ffmpeg-python, librosa
- Image: Pillow, opencv-python-headless
- Database: prisma, snowflake-connector-python

---

## 🔧 Technology Stack

### Frontend
- **Framework:** Next.js 16 (App Router)
- **Language:** TypeScript 5
- **Styling:** Tailwind CSS 4
- **UI Library:** shadcn/ui (Radix UI)
- **State:** Zustand, TanStack Query
- **Forms:** React Hook Form + Zod

### Backend
- **Runtime:** Bun / Node.js
- **Database:** SQLite (Prisma ORM)
- **API:** Next.js API Routes
- **Real-time:** Socket.io

### AI/ML
- **SDK:** z-ai-web-dev-sdk
- **Capabilities:** LLM, VLM, ASR, TTS, Image/Video Generation

### DevOps
- **Reverse Proxy:** Caddy
- **Build:** Bun
- **Process Manager:** Shell scripts

---

## 📋 File Statistics

| Category | Files | Description |
|----------|-------|-------------|
| Source Code | 56 | Frontend components, hooks, lib |
| AI Skills | 100+ | SKILL.md files + implementations |
| Shell Scripts | 5 | Build and deployment |
| Configuration | 10 | Project config files |
| Examples | 2 | WebSocket demo |
| Python Packages | 1 | pyproject.toml |
| **Total** | **170+** | Complete infrastructure |

---

## 🚀 Quick Start

```bash
# Extract the archive
tar -xzf z-ai-infrastructure-complete.tar.gz

# Navigate to project
cd z-ai-infrastructure

# Install dependencies
bun install

# Setup database
bun run db:push

# Start development server
bun run dev
```

---

## 📝 License

- **Source Code & Skills:** MIT License (where LICENSE.txt is MIT)
- **PDF/DOCX/XLSX Skills:** Proprietary (see LICENSE.txt in each folder)
- **Finance & Gift Evaluator:** Internal Tool

---

**Archive Created By:** Z.ai Infrastructure Analysis
**Total Size:** 373 KB (compressed)
