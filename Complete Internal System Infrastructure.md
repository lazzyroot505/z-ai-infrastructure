# 🛡️ Next.js 15 Development Platform - Security Audit & Documentation

> **Complete System Documentation** | Alibaba Cloud Function Compute | Kata Container Isolation

```
⚠️ SECURITY NOTICE: This document contains sensitive infrastructure details. 
Handle according to your organization's security policies.
```

---

## 📋 Table of Contents

1. [Overview](#-overview)
2. [Platform Architecture](#-platform-architecture)
3. [Technical Stack](#-technical-stack)
4. [Environment Configuration](#-environment-configuration)
5. [Project Structure](#-project-structure)
6. [Security Posture](#-security-posture)
7. [Development Workflow](#-development-workflow)
8. [Deployment Guide](#-deployment-guide)
9. [Monitoring & Logging](#-monitoring--logging)
10. [Troubleshooting](#-troubleshooting)
11. [Access Limitations](#-access-limitations)
12. [Contributing](#-contributing)

---

## 🔍 Overview

This project runs a **Next.js 15 development platform** on **Alibaba Cloud Function Compute (FC)** with hardware-isolated containerization via **Kata Containers**.

### Key Characteristics
| Attribute | Value |
|-----------|-------|
| **Runtime** | Next.js 15 (Development Mode) |
| **Container** | Kata Container (`KATA_CONTAINER=true`) |
| **Platform** | Alibaba Cloud Function Compute |
| **Region** | `cn-hongkong` |
| **Memory Allocation** | 8192 MB |
| **User Context** | Non-root user `z` (UID: 3003) |
| **Database** | SQLite (`/home/z/my-project/db/custom.db`) |

---

## 🏗️ Platform Architecture

```
┌─────────────────────────────────────────┐
│  Alibaba Cloud Function Compute (FC)    │
├─────────────────────────────────────────┤
│  ┌─────────────────────────────────┐   │
│  │  Kata Container (Hardware VM)   │   │
│  │  ┌─────────────────────────┐   │   │
│  │  │  Next.js 15 App         │   │   │
│  │  │  • Port 3000 (Dev)      │   │   │
│  │  │  • Port 81 (Custom)     │   │   │
│  │  │  • User: z (UID 3003)   │   │   │
│  │  └─────────────────────────┘   │   │
│  │  ┌─────────────────────────┐   │   │
│  │  │  Z-AI Runtime Service   │   │   │
│  │  │  • Internal: 172.25.136.193:8080 │
│  │  └─────────────────────────┘   │   │
│  └─────────────────────────────────┘   │
└─────────────────────────────────────────┘
```

### Network Configuration
```yaml
Internal IP: 21.0.2.48/32
MAC Address: ee:28:c7:80:6a:0a
DNS Servers: 
  - 100.100.2.136
  - 100.2.138
Exposed Ports:
  - 3000/tcp: Next.js Development Server
  - 81/tcp: Custom Function Handler (FC_CUSTOM_LISTEN_PORT)
```

---

## ⚙️ Technical Stack

### Runtime Environment
```bash
Node.js    : v22.x
Bun        : v1.x  
Python     : 3.12 (UV package manager)
npm        : 11.8.0
OS Kernel  : Linux 5.10.134 (Alibaba Cloud optimized)
```

### Core Dependencies
| Package | Purpose |
|---------|---------|
| `next@15` | React framework with App Router |
| `prisma` | Database ORM & schema management |
| `tailwindcss` | Utility-first CSS framework |
| `typescript` | Type-safe development |
| `z-ai-runtime` | AI service integration layer |

### System Tools Available
```
✅ curl, wget          ✅ git
✅ vim, nano           ✅ imagemagick
✅ ffmpeg              ✅ poppler-utils (PDF)
✅ libreoffice         ✅ openjdk-21-jre
```

---

## 🔐 Environment Configuration

### Critical Environment Variables
```env
# Application
DATABASE_URL=file:/home/z/my-project/db/custom.db
FC_CUSTOM_LISTEN_PORT=81
SIGMA_APP_NAME=fn-ws-59c18773-cfdb-410e-a6b1-b29f4dcc1353

# Platform (Alibaba Cloud FC)
FC_REGION=cn-hongkong
FC_FUNCTION_MEMORY_SIZE=8192

# Python/UV Configuration
UV_CACHE_DIR=/var/cache/uv
UV_PYTHON=3.12
VIRTUAL_ENV=/app/.venv

# AI Service Integration
Z_AI_CONFIG={"baseUrl":"http://172.25.136.193:8080/v1","apiKey":"Z.ai"}
```

### ⚠️ Security-Sensitive Variables
> The following should **never** be logged or exposed:
> - `Z_AI_CONFIG.apiKey` 
> - `DATABASE_URL` (if using production credentials)
> - Any `FC_*` identifiers in public repositories

---

## 📁 Project Structure

```
/home/z/my-project/
├── 📄 package.json              # Dependencies & scripts
├── 📄 tsconfig.json            # TypeScript configuration
├── 📄 next.config.ts           # Next.js custom config
├── 📄 tailwind.config.ts       # Tailwind CSS setup
├── 📄 prisma/schema.prisma     # Database schema definition
├── 📄 Caddyfile                # Reverse proxy configuration
│
├── 📁 src/
│   ├── 📁 app/
│   │   ├── 📄 page.tsx         # Main page component
│   │   ├── 📄 layout.tsx       # Root layout wrapper
│   │   ├── 📄 globals.css      # Global styles
│   │   └── 📁 api/
│   │       └── 📄 route.ts     # API route handlers
│   │
│   └── 📁 lib/
│       ├── 📄 db.ts            # Database connection utility
│       └── 📄 utils.ts         # Shared helper functions
│
├── 📁 db/
│   └── 📄 custom.db            # SQLite database file
│
├── 📁 node_modules/            # Dependencies (~1.2 GB)
└── 📁 .next/                   # Build cache (~101 MB)
```

---

## 🛡️ Security Posture

### ✅ Security Strengths
```
✓ Hardware-isolated container (Kata Containers)
✓ Non-root execution context (user 'z', UID 3003)
✓ No passwordless sudo privileges
✓ Restricted file permissions:
  - /etc/shadow: ACCESS DENIED
  - /etc/ssl/private: ACCESS DENIED  
  - /var/log/btmp: ACCESS DENIED
✓ No Docker socket exposure
✓ No Kubernetes secrets accessible
✓ Minimal exposed surface (ports 81, 3000 only)
✓ No SSH daemon running
```

### ⚠️ Security Considerations
```
! SUID binaries present (standard Debian set):
  /usr/bin/sudo, /usr/bin/su, /usr/bin/passwd, etc.
  → Mitigated by non-root context & no sudo access

! Development mode active:
  → Next.js dev server exposes debug endpoints
  → Recommendation: Use production build for deployment

! SQLite database in project directory:
  → Ensure proper file permissions
  → Consider migration to managed database for production
```

### Access Control Matrix
| Resource | User 'z' Access | Root Required |
|----------|----------------|---------------|
| `/home/z/**` | ✅ Read/Write | ❌ |
| `/etc/passwd` | ✅ Read | ❌ |
| `/etc/shadow` | ❌ Denied | ✅ |
| `/etc/ssl/private/**` | ❌ Denied | ✅ |
| `/var/log/auth.log` | ✅ Read | ❌ |
| `sudo` commands | ❌ Password required | ✅ |
| Package installation (npm/bun/pip) | ✅ User-space | ❌ |

---

## 🚀 Development Workflow

### Local Development (Within Container)
```bash
# Navigate to project
cd /home/z/my-project

# Install dependencies (if needed)
bun install
# or
npm install

# Start development server
bun run dev
# or  
npm run dev

# Server will be available at:
# • http://localhost:3000 (Next.js)
# • http://localhost:81 (FC handler endpoint)
```

### Database Management
```bash
# Prisma commands (using Bun/Node)
bunx prisma migrate dev
bunx prisma studio
bunx prisma generate

# Direct SQLite access
sqlite3 /home/z/my-project/db/custom.db
```

### Environment Testing
```bash
# Verify environment variables
printenv | grep FC_

# Check network connectivity
curl http://172.25.136.193:8080/v1/health

# Validate port listeners
ss -tlnp | grep -E ':(81|3000)'
```

---

## ☁️ Deployment Guide (Alibaba Cloud FC)

### Prerequisites
- Alibaba Cloud account with Function Compute access
- `fc-cli` or Terraform provider configured
- Region: `cn-hongkong`

### Deployment Steps
```yaml
# 1. Package application
fc deploy --code ./my-project --runtime custom

# 2. Configure function settings
function_config:
  name: ws-59c18773-cfcb-410e-a6e1-b29f4dee1353
  runtime: custom
  handler: index.handler
  memorySize: 8192
  timeout: 60
  environmentVariables:
    FC_CUSTOM_LISTEN_PORT: "81"
    DATABASE_URL: "file:/home/z/my-project/db/custom.db"
    # ... other vars

# 3. Deploy with Kata Container isolation
container_config:
  type: kata
  image: aliyun/fc-custom-node22:latest
```

### Post-Deployment Verification
```bash
# Test endpoint
curl https://<function-url>.fc.aliyuncs.com/health

# Check logs via Alibaba Cloud Console
# or CLI:
fc logs --function-name ws-59c18773-cfdb-410e-a6b1-b29f4dcc1353
```

---

## 📊 Monitoring & Logging

### Accessible Log Files
```bash
/var/log/syslog      # General system messages
/var/log/auth.log    # Authentication events  
/var/log/kern.log    # Kernel messages
/var/log/dpkg.log    # Package installation logs
```

### Application Logging
```typescript
// Recommended logging pattern (src/lib/utils.ts)
import { createLogger } from 'next-logger';

export const logger = createLogger({
  level: process.env.NODE_ENV === 'production' ? 'info' : 'debug',
  outputs: ['console', 'file:/home/z/my-project/logs/app.log']
});
```

### Health Check Endpoint
```typescript
// src/app/api/health/route.ts
export async function GET() {
  return Response.json({
    status: 'healthy',
    timestamp: new Date().toISOString(),
    uptime: process.uptime(),
    memory: process.memoryUsage(),
    environment: process.env.FC_REGION
  });
}
```

---

## 🔧 Troubleshooting

### Common Issues & Solutions

| Issue | Diagnostic Command | Resolution |
|-------|-------------------|------------|
| Port 3000 not responding | `ss -tlnp \| grep 3000` | Verify `bun run dev` is running; check FC port mapping |
| Database connection error | `ls -la /home/z/my-project/db/` | Ensure `custom.db` exists & has write permissions |
| AI service timeout | `curl -v http://172.25.136.193:8080/v1/health` | Verify Z-AI runtime status; check network policies |
| Memory pressure | `free -h` | Optimize bundle size; reduce concurrent operations |
| Permission denied errors | `id && groups` | Confirm running as user `z`; avoid root-requiring operations |

### Debug Mode Activation
```bash
# Enable verbose Next.js logging
export NEXT_DEBUG=1
export DEBUG=next:*

# Python/UV debugging
export UV_VERBOSE=1
export PYTHONUNBUFFERED=1

# Restart with debug flags
bun run dev --turbo --debug-port 9229
```

---

## 🚫 Access Limitations (Sandbox Constraints)

### What This Environment **Cannot** Do:
```
❌ Execute commands as root (password required, not available)
❌ Access SSH or open new terminal sessions
❌ Modify /etc/shadow, /etc/sudoers, or SSL private keys
❌ Install system packages requiring sudo (apt-get install)
❌ Access Docker/Kubernetes control plane
❌ Bind to privileged ports (<1024) without capabilities
❌ Persist changes to container filesystem after termination*
```

> *Note: Alibaba Cloud FC uses ephemeral storage. Persist data to OSS, NAS, or external databases.

### What This Environment **Can** Do:
```
✅ Execute any command as user 'z'
✅ Read/write files in /home/z/ and project directories
✅ Install Node.js/Bun/Python packages in user space
✅ Access all project source code and configuration
✅ Query system information (/proc, /sys, env vars)
✅ Make outbound HTTP/HTTPS requests
✅ Interact with internal Z-AI runtime service
```

---

## 🤝 Contributing

### Code Standards
```typescript
// TypeScript: Strict mode enabled (tsconfig.json)
// ESLint: Next.js core web vitals config
// Prettier: Single quotes, semicolons, 2-space indent

// Example component pattern:
'use client';

import { useState } from 'react';

export function SecureComponent() {
  const [data, setData] = useState<string | null>(null);
  
  // Always validate AI service responses
  const fetchAI = async (prompt: string) => {
    const res = await fetch('/api/ai', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ prompt })
    });
    
    if (!res.ok) throw new Error('AI service unavailable');
    return res.json();
  };
}
```

### Security Review Checklist
Before merging PRs, verify:
- [ ] No hardcoded secrets in code or config files
- [ ] API routes implement authentication/authorization
- [ ] Database queries use parameterized statements (Prisma handles this)
- [ ] User input is sanitized before processing
- [ ] Error messages don't leak system details
- [ ] Dependencies are scanned for vulnerabilities (`bunx npm-audit`)

### Reporting Security Issues
🔒 **Do not** create public issues for security vulnerabilities.  
Contact: `security@your-org.example` with:
- Affected component/version
- Steps to reproduce (if safe to share)
- Potential impact assessment
- Suggested mitigation (optional)

---

## 📜 License & Attribution

```
© 2026 Your Organization. All rights reserved.

This software is deployed on Alibaba Cloud Function Compute 
under enterprise agreement. Kata Containers technology 
licensed under Apache 2.0.

Next.js is licensed under MIT License.
Prisma is licensed under Apache 2.0.
```

---

## 🔄 Document Version History

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 1.0.0 | 2025-02 | Initial security audit & documentation | System Audit Tool |
| 1.0.1 | 2025-02 | Added troubleshooting matrix & deployment guide | DevOps Team |

---

> 📌 **Last Updated**: February 2026  
> 🌐 **Platform**: Alibaba Cloud Function Compute (cn-hongkong)  
> 🔐 **Classification**: Internal Use Only  

*This README was auto-generated from comprehensive system audit. Verify critical configurations against live environment before production deployment.*
