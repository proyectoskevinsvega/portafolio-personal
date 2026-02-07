# Portafolio Profesional

Stack moderno con **Next.js 16** + **React 18** + **PostgreSQL** + **Redis** + **TailwindCSS**

## 📋 Estructura del Proyecto

```
project/
├── app/                             ← Next.js App Router
│   ├── api/
│   │   ├── admin/
│   │   │   └── projects/            ← Admin: CRUD proyectos
│   │   ├── analytics/               ← Google Analytics events
│   │   ├── auth/
│   │   │   ├── login/                ← POST: Iniciar sesión
│   │   │   ├── register/             ← POST: Registrar usuario
│   │   │   ├── logout/               ← POST: Cerrar sesión
│   │   │   ├── me/                   ← GET: Obtener perfil actual
│   │   │   ├── refresh/              ← POST: Refrescar token JWT
│   │   │   ├── forgot-password/      ← POST: Solicitar recuperación
│   │   │   ├── reset-password/       ← POST: Resetear contraseña
│   │   │   └── verify-recovery-code/ ← POST: Verificar código recovery
│   │   ├── blog/
│   │   │   └── [slug]/              ← Blog post
│   │   ├── config/                  ← Configuración general
│   │   ├── contact/                 ← Formulario contacto
│   │   ├── education/               ← Educación
│   │   │   └── [id]/
│   │   ├── emails/
│   │   │   └── send/                ← Envío de emails (Resend)
│   │   ├── experiences/             ← Experiencias laborales
│   │   │   └── [id]/
│   │   ├── profiles/                ← Perfiles de usuario
│   │   │   └── [id]/
│   │   ├── project-buttons/         ← Config botones proyectos
│   │   │   └── [id]/
│   │   ├── projects/                ← Proyectos
│   │   │   └── [slug]/
│   │   ├── sitemap/                 ← Sitemap dinámico XML
│   │   ├── skills/                  ← Habilidades técnicas
│   │   └── visits/                  ← Tracking de visitas
│   ├── admin/                       ← Panel administrativo (rutas protegidas)
│   │   ├── blog/                    ← Gestionar blog posts
│   │   ├── dashboard/               ← Panel principal
│   │   ├── education/               ← Gestionar educación
│   │   ├── experience/              ← Gestionar experiencia
│   │   ├── forgot-password/         ← Recuperar contraseña
│   │   ├── login/                   ← Login admin
│   │   ├── messages/                ← Mensajes de contacto
│   │   ├── profile/                 ← Perfil del usuario
│   │   ├── projects/                ← Gestionar proyectos
│   │   ├── reset-password/          ← Resetear contraseña
│   │   ├── settings/                ← Configuraciones
│   │   └── skills/                  ← Gestionar habilidades
│   ├── blog/                        ← Blog público
│   ├── contact/                     ← Formulario contacto público
│   ├── experiences/                 ← Experiencias públicas
│   │   └── [id]/                    ← Detalles experiencia
│   ├── projects/                    ← Proyectos públicos
│   │   └── [slug]/
│   │       └── readme/
│   ├── layout.tsx                   ← Layout raíz
│   └── page.tsx                     ← Home (landing page)
│
├── lib/                             ← Backend utilities
│   ├── db.ts                        ← Pool PostgreSQL
│   ├── redis.ts                     ← Cliente Redis (ioredis)
│   ├── cache.ts                     ← Utilidades de caché (cacheGet, cacheSet, cacheOrFetch)
│   ├── auth.ts                      ← JWT + bcrypt
│   ├── security.ts                  ← Rate limiting Redis, IP blocking, refresh tokens
│   ├── google-analytics.ts          ← GA4 tracking utilities + useGoogleAnalytics hook
│   ├── email.ts                     ← Email config (Resend)
│   ├── types.ts                     ← Tipos TypeScript
│   ├── analytics.ts                 ← Sistema de eventos antiguo (deprecated)
│   └── analytics.examples.tsx       ← Ejemplos de uso
│
├── src/                             ← Frontend React
│   ├── components/
│   │   ├── Blog.tsx                 ← Blog preview
│   │   ├── Contact.tsx              ← Formulario contacto
│   │   ├── Experience.tsx           ← Experiencia preview
│   │   ├── Footer.tsx               ← Footer
│   │   ├── Hero.tsx                 ← Sección hero
│   │   ├── Navbar.tsx               ← Navegación
│   │   ├── Projects.tsx             ← Grid proyectos
│   │   ├── Skills.tsx               ← Habilidades
│   │   ├── WhatsAppButton.tsx       ← Botón WhatsApp flotante
│   │   └── NotificationToast.tsx    ← Notificaciones
│   ├── contexts/
│   │   ├── AuthContext.tsx
│   │   └── ThemeContext.tsx
│   ├── hooks/                       ← Custom React hooks
│   ├── views/
│   │   ├── AllProjects.tsx          ← Página todos los proyectos
│   │   ├── BlogPage.tsx             ← Blog completo
│   │   ├── ContactPage.tsx          ← Página contacto
│   │   ├── ExperienceDetails.tsx    ← Detalles de una experiencia
│   │   ├── ProjectDetails.tsx       ← Detalles de proyecto (con tracking GA4)
│   │   ├── ProjectReadme.tsx        ← README del proyecto
│   │   └── admin/                   ← Componentes admin
│   ├── index.css                    ← Estilos globales
│   └── globals.d.ts
│
├── postgresSQL/
│   └── migrations/                  ← SQL migrations
│       ├── 20251008043402_portfolio_schema.sql
│       ├── 20251008043403_example_schema.sql
│       ├── 20251008043404_email_notifications.sql
│       ├── 20251008043405_refresh_tokens.sql
│       └── 20260205_password_recovery.sql
│
├── tests/
│   ├── unit/
│   │   └── analytics.test.ts        ← Tests Google Analytics (5/5 passing ✅)
│   └── e2e/
│       └── navigation.spec.ts       ← Tests navegación Playwright
│
├── public/                          ← Assets estáticos
│
├── scripts/                         ← Scripts de utilidad
│   └── migrate.sh                   ← Script migraciones BD
│
├── .github/
│   └── workflows/                   ← CI/CD con GitHub Actions
│       ├── ci.yml                   ← Lint, type check, build, security
│       └── deploy.yml               ← Deploy automático a Vercel
│
├── middleware.ts                    ← Security headers (CSP, X-Frame-Options, HSTS)
├── vitest.config.ts                 ← Config testing unitario
├── playwright.config.ts             ← Config testing E2E
├── next.config.ts                   ← Config Next.js
├── tailwind.config.js               ← Config Tailwind CSS
├── tsconfig.json                    ← Config TypeScript (strict mode)
├── jsconfig.json
├── postcss.config.js
├── .env.example                     ← Variables de entorno (template)
├── .env.local                       ← Variables de entorno (local - no versionar)
├── .gitignore
├── package.json
├── pnpm-lock.yaml
├── README.md                        ← Documentación principal
├── TESTING_REFERENCE.md             ← Guía completa de testing
├── GOOGLE_ANALYTICS_SETUP.md        ← Configuración GA4 (Measurement Protocol)
├── MIGRATION_GUIDE.md               ← Guía de migraciones
├── NEXT_STEPS.md                    ← Próximas tareas
└── next-env.d.ts                    ← Types Next.js
```

## 🚀 Quick Start

### 1. Instalar dependencias
```bash
pnpm install
```

### 2. Crear database (Docker)
```bash
docker run --name portfolio_db \
  -e POSTGRES_DB=portfolio \
  -e POSTGRES_PASSWORD=postgres \
  -p 5432:5432 -d postgres:15

# Ejecutar migraciones
cat postgresSQL/migrations/*.sql | docker exec -i portfolio_db psql -U postgres -d portfolio
```

### 3. Configurar `.env.local`
```env
# Database
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=postgres
DB_NAME=portfolio

# Redis (para rate limiting, caché, tokens)
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_DB=4

# Auth
JWT_SECRET=tu-secreto-cambiar-en-produccion

# API (producción con Cloudflare Tunnel)
NEXT_PUBLIC_API_URL=http://localhost:3004
# En producción: NEXT_PUBLIC_API_URL=https://tu-dominio.com

# Google Analytics (Opcional)
NEXT_PUBLIC_GA_ID=G-XXXXXXXXXX
GA_API_SECRET=tu-api-secret

# Email (Opcional)
RESEND_API_KEY=re_xxxxxxxxxx
RESEND_FROM_EMAIL=noreply@tudominio.com
```

### 4. Ejecutar
```bash
pnpm run dev
```

Acceder a: **http://localhost:3004**

## 📚 Scripts

```bash
pnpm run dev          # Desarrollo
pnpm run build        # Build producción
pnpm start            # Ejecutar producción
pnpm run lint         # Linting (ESLint)

# Testing
pnpm run test:unit              # Tests unitarios
pnpm run test:unit --watch      # Watch mode
pnpm run test:unit --coverage   # Con coverage report
pnpm run test:e2e               # Tests E2E
pnpm run test:e2e --ui          # UI interactiva
```

## � Documentación

- **[TESTING_REFERENCE.md](/TESTING_REFERENCE.md)** - Guía de testing, setup, ejecución y troubleshooting
- **[GOOGLE_ANALYTICS_SETUP.md](/GOOGLE_ANALYTICS_SETUP.md)** - Configurar Google Analytics 4 (Measurement Protocol)
- **[SEO_SETUP.md](/SEO_SETUP.md)** - Configuración de SEO (metadata, robots.txt, sitemap)
## �🔗 API Endpoints

**Autenticación:**
```
POST   /api/auth/register              - Registrar usuario
POST   /api/auth/login                 - Iniciar sesión
POST   /api/auth/logout                - Cerrar sesión
POST   /api/auth/forgot-password       - Solicitar recuperación
POST   /api/auth/reset-password        - Resetear contraseña
GET    /api/auth/me                    - Perfil del usuario actual
GET    /api/auth/refresh               - Refrescar token
```

**Proyectos (Público):**
```
GET    /api/projects                   - Listar proyectos públicos
GET    /api/projects/:slug             - Obtener proyecto por slug
```

**Proyectos (Admin - Autenticado):**
```
GET    /api/admin/projects/:id         - Obtener proyecto por ID
PATCH  /api/admin/projects/:id         - Actualizar proyecto (parcial)
PUT    /api/admin/projects/:id         - Actualizar proyecto (completo)
DELETE /api/admin/projects/:id         - Eliminar proyecto
```

**Configuración de Botones:**
```
GET    /api/project-buttons?projectIds=...    - Obtener botones por proyectos
GET    /api/project-buttons?userId=...        - Obtener botones por usuario
PATCH  /api/project-buttons/:id               - Actualizar botones
```

**Otros:**
```
GET    /api/experiences                - Experiencias
GET    /api/skills                     - Habilidades
GET    /api/blog                       - Blog posts
GET    /api/blog/:slug                 - Artículo por slug
POST   /api/contact                    - Enviar mensaje
GET    /api/emails/send                - Enviar email (admin)
POST   /api/analytics                  - Registrar evento de analytics
GET    /api/analytics                  - Obtener métricas (requiere auth)
```

## 🛠 Stack Tecnológico

- **Frontend**: React 18.3 + Next.js 16.1 (Con Turbopack)
- **Backend**: Next.js API Routes
- **Database**: PostgreSQL 12+ + Redis 6+
- **Bundler**: Turbopack (por defecto)
- **Estilos**: TailwindCSS 3.4 + PostCSS
- **Auth**: JWT + bcrypt + Redis (refresh tokens)
- **Caché**: Redis (perfiles, rate limiting, IP blocking)
- **Markdown**: react-markdown + remark-gfm + rehype
- **Tipos**: TypeScript 5.9
- **Package Manager**: pnpm 9.x

## 📦 Dependencias principales

```json
{
  "next": "16.1.6",
  "react": "18.3.1",
  "react-dom": "18.3.1",
  "pg": "8.18.0",
  "ioredis": "5.4.2",
  "bcryptjs": "2.4.3",
  "jsonwebtoken": "9.0.2",
  "tailwindcss": "3.4.1",
  "typescript": "5.5.3",
  "react-markdown": "10.1.0",
  "remark-gfm": "4.0.1",
  "rehype-raw": "7.0.0",
  "rehype-sanitize": "6.0.0",
  "lucide-react": "0.344.0",
  "resend": "6.9.1",
  "dotenv": "16.3.1"
}
```

## 🔐 Seguridad

- ✅ Contraseñas hasheadas con bcrypt
- ✅ JWT tokens (15 min + refresh 30d)
- ✅ Refresh tokens almacenados en Redis con rotación
- ✅ Cookies HTTP-only + secure in prod
- ✅ CORS automático (same origin)
- ✅ SQL con parameterized queries
- ✅ Rate limiting con Redis (5/15min login, 3/60min register, 3/60min contacto)
- ✅ IP blocking con Redis (bloqueo automático tras múltiples intentos fallidos)
- ✅ Validación de email y password (12+ chars, complejidad)
- ✅ Middleware con headers de seguridad (CSP, X-Frame-Options, HSTS)
- ✅ Autenticación requerida en endpoints admin

## 🚢 Deployment

### Vercel (Recomendado)

1. Conectar repo a Vercel
2. Agregar variables de entorno en Project Settings
3. Deploy automático en cada push a main

### Cloudflare Tunnel (Self-hosted)

1. Configurar Cloudflare Tunnel apuntando a `http://localhost:3004`
2. Configurar `NEXT_PUBLIC_API_URL=https://tu-dominio.com`
3. Asegurar que Redis esté corriendo
4. Deploy:

```bash
pnpm install
pnpm run build
pnpm start
```

### Self-hosted básico

```bash
pnpm install
pnpm run build
pnpm start
```

## 📝 Notas

- **Turbopack**: Bundler por defecto en Next.js 16+. Más rápido que webpack.
- **JWT expiral**: Tokens con duración de 7 días configurable en `lib/auth.ts`
- **Rutas Admin**: Requieren autenticación via JWT en cookies o header `Authorization`
- **Rutas Públicas**: Accesibles sin autenticación
- **Markdown**: Soporta CommonMark + GFM (tablas, strikethrough) + HTML raw

## 🔍 SEO Optimización

El sitio implementa las mejores prácticas de SEO:

- **Sitemap dinámico**: `/sitemap.xml` genera automáticamente un sitemap con todos los proyectos publicados
- **Robots.txt**: `/robots.txt` permite indexación de buscadores y define áreas prohibidas
- **Metadata mejorada**: 
  - Open Graph para redes sociales (Facebook, LinkedIn, WhatsApp)
  - Twitter Card para vista previa en Twitter/X
  - Canonical URLs para evitar duplicación
  - Keywords y descripción optimizados
- **Rotas dinámicas**: Las páginas de proyectos incluyen metadata individual
- **Caché optimizado**: Sitemap se cachea 1 hora en el navegador + 24h en CDN

### Endpoints SEO

```
GET /robots.txt                    - Configuración para buscadores
GET /sitemap.xml                   - Sitemap dinámico (XML)
```

### Variables de entorno para SEO

```env
NEXT_PUBLIC_API_URL=https://tudominio.com  # URL base para canonical + OpenGraph
```

## 🚀 CI/CD con GitHub Actions

El proyecto incluye workflows automáticos para testing, linting y deployment:

### Workflow: CI (`.github/workflows/ci.yml`)

Se ejecuta en cada **push** y **pull request** a `main` y `develop`:

- ✅ **Linting**: ESLint validation
- ✅ **Type checking**: TypeScript validation
- ✅ **Build**: Compila el proyecto
- ✅ **Security scan**: Trivy vulnerability scanner

```yaml
Triggered on:
  - push a main o develop
  - Pull request a main o develop
```

### Workflow: Deploy (`.github/workflows/deploy.yml`)

Se ejecuta automáticamente después de CI exitoso en `main`:

- 🚀 **Deploy automático**: A Vercel en cada push a main
- 📝 **Comentario en PR**: Notifica URL de preview
- ⏱️ Solo deploy si CI pasó exitosamente

### Configuración Requerida

Para que funcione el deployment, agregá estos **secrets** en GitHub:

**Settings → Secrets and variables → Actions → New repository secret:**

```
VERCEL_TOKEN        → Token de Vercel (https://vercel.com/account/tokens)
VERCEL_ORG_ID       → ID de tu organización en Vercel
VERCEL_PROJECT_ID   → ID del proyecto en Vercel
```

### Cómo obtener los secrets de Vercel

1. **VERCEL_TOKEN**:
   - Ve a https://vercel.com/account/tokens
   - Crea un nuevo token
   - Cópialo a GitHub Secrets

2. **VERCEL_ORG_ID**:
   ```bash
   # Desde la CLI de Vercel
   vercel whoami --team
   ```

3. **VERCEL_PROJECT_ID**:
   - En Vercel, Settings → Project → Project ID
   - O desde `.vercel/project.json` después de `vercel link`

### Flujo de CI/CD

```
1. Haces push a main
   ↓
2. GitHub Actions ejecuta CI:
   - Lint
   - Type Check
   - Build
   - Security Scan
   ↓
3. Si CI pasa ✅:
   - Trigger Deploy workflow
   - Deploy a Vercel
   ↓
4. Si CI falla ❌:
   - No hace deploy
   - Notifica el error
```

### Ver logs

Ve a **GitHub → Actions** para ver el estado de los workflows

## 📊 Google Analytics 4 Integrado

El proyecto incluye integración completa con **Google Analytics 4** via Measurement Protocol API:

### Eventos de tracking implementados

**Proyectos:**
```typescript
'project_viewed'              // Página de detalles de proyecto
'project_demo_clicked'        // Click en botón Demo
'project_github_clicked'      // Click en botón GitHub
'project_readme_viewed'       // Lectura de README
```

**Contenido:**
```typescript
'blog_post_viewed'            // Lectura de artículo
'experience_section_viewed'   // Sección de experiencia visible
'experience_details_viewed'   // Detalles de experiencia individ.
'profile_view'                // Vista del perfil
'all_projects_view'           // Página con todos los proyectos
```

**Usuario:**
```typescript
'contact_form_submitted'      // Envío de formulario
'admin_login'                 // Login en panel admin
'admin_project_created'       // Creación de proyecto
'admin_project_updated'       // Actualización de proyecto
'admin_project_deleted'       // Eliminación de proyecto
```

### Utilidades de tracking

```typescript
import { 
  trackProjectView,
  trackDemoClic,
  trackGitHubClick,
  trackContactSubmit,
  useGoogleAnalytics
} from '@/lib/google-analytics';

// Uso directo
await trackProjectView('mi-proyecto');
await trackDemoClic('slug', 'https://demo.com');

// Con hook React
const { trackEvent, trackBlogView } = useGoogleAnalytics();
```

### Configuración

1. **Google Analytics**: obtener `NEXT_PUBLIC_GA_ID` de tu propiedad GA4
2. **Service Account**: crear key JSON en Google Cloud Console
3. **Variables de entorno**: agregar `GA_API_SECRET`

Ver **[GOOGLE_ANALYTICS_SETUP.md](/GOOGLE_ANALYTICS_SETUP.md)** para pasos detallados.

### Seguridad

- ✅ API secret no se expone al cliente
- ✅ Measurement Protocol API (servidor seguro)
- ✅ Endpoint `/api/analytics` valida requests
- ✅ Eventos sin datos sensibles ni identificables
- ✅ Compatible con GDPR

## 🧪 Testing

El proyecto incluye infraestructura completa para testing unitario y E2E:

### Estado actual

✅ **Vitest**: Tests unitarios configurados (5/5 tests passing)
✅ **Playwright**: E2E configurado con browsers instalados  
✅ **Coverage**: Coverage reports configurados
✅ **CI/CD**: Tests automáticos en cada push

### Tests Unitarios con Vitest

**Configuración**: `vitest.config.ts`

- Framework: Vitest (rápido, compatible con Turbopack)
- Ambiente: jsdom para componentes React
- Coverage: Reporte HTML incluido
- Setup automático: `vitest.setup.ts`

**Ejecutar**:

```bash
pnpm run test:unit              # Ejecutar tests
pnpm run test:unit --ui         # UI interactiva
pnpm run test:unit --coverage   # Con reporte de coverage
pnpm run test:unit --watch      # Watch mode
```

Para ejemplos detallados, ver [TESTING_REFERENCE.md](/TESTING_REFERENCE.md).

### Tests E2E con Playwright

**Configuración**: `playwright.config.ts`

- Framework: Playwright (cross-browser)
- Navegadores: Chromium, Firefox, Safari, Mobile
- Screenshots: Automáticos en fallos
- Traces: Debugging visual de fallos

**Ejecutar**:

```bash
pnpm run test:e2e                  # Ejecutar tests E2E
pnpm run test:e2e --ui             # UI interactiva
pnpm run test:e2e --headed         # Con navegador visible
pnpm run test:e2e --debug          # Modo debug
pnpm run test:e2e --project=firefox # Específico a Firefox
```

Para ejemplos detallados, ver [TESTING_REFERENCE.md](/TESTING_REFERENCE.md).

### Structure de tests

```
tests/
├── unit/                      ← Tests unitarios
│   ├── analytics.test.ts
│   ├── auth.test.ts
│   └── ...
├── e2e/                       ← Tests E2E
│   ├── navigation.spec.ts
│   ├── auth.spec.ts
│   └── ...
└── fixtures/                  ← Datos para tests
```

### Cobertura de tests

Archivos cubiertos pueden variar, pero enfocados en:

- **Unitarios**: Utilidades, funciones helper, lógica de negocio
- **E2E**: Flujos de usuario completos, navegación, formularios, auth

**Ver reporte**:

```bash
pnpm run test:unit --coverage
# Abre: coverage/index.html
```

### CI/CD Integration

El workflow `.github/workflows/tests.yml`:

- ✅ Ejecuta tests en cada push/PR
- ✅ Paralleliza unit tests + E2E
- ✅ Espera a que DB esté lista (PostgreSQL service)
- ✅ Sube reports a artifacts (30 días)
- ✅ Integra con Codecov para coverage

**Requerimientos para E2E en CI**:

```env
DATABASE_URL=postgresql://postgres:postgres@localhost:5432/portfolio_test
NEXT_PUBLIC_API_URL=http://localhost:3004
```

### Best Practices

1. **Tests unitarios**: Una función = un test
2. **Tests E2E**: Flujos de usuario reales
3. **Mocking**: Mock externos (APIs, DB), test comportamiento real
4. **Antes de commit**: `pnpm run test:unit`
5. **Antes de push**: CI corre automáticamente

### Debugging

**Vitest**:

```bash
# Debug en VSCode
pnpm run test:unit --inspect-brk
```

**Playwright**:

```bash
# Debug visual
pnpm run test:e2e --debug

# Ver video de ejecución
pnpm run test:e2e --headed
```

### Próxima: Aumentar cobertura

- Agregar más tests unitarios para funciones criticas
- Agregar tests de autenticación (login/logout)
- Tests de CRUD de proyectos
- Tests de API routes
- Performance tests con Lighthouse

## 📋 Características

✨ Portafolio profesional completamente funcional
🔐 Sistema de autenticación con JWT
📊 Panel administrativo para gestionar todo el contenido
🎨 Tema claro/oscuro
📱 Diseño responsivo con TailwindCSS
🚀 API REST completa con validación
📝 Sistema de blog con markdown
♻️ Context API para manejo de estado
⚡ Turbopack para compilación rápida
📧 Sistema de emails integrado
📊 Sistema de analíticas de eventos
🔄 CI/CD automático con GitHub Actions
🌐 SEO optimizado (sitemap + robots.txt)
🧪 Testing (Vitest + Playwright)
📈 Cobertura de código reportada a Codecov


## � Próximas Mejoras

- [ ] GA4 Reporting API para dashboard de métricas
- [ ] Dark mode persistence
- [ ] PWA support
- [ ] Redis caching para rate limiting distribuido
- [ ] OAuth2 social login
- [ ] 2FA implementation

## �👤 Autor

**Kevins Yesid Vega Marmolejo** - Full Stack Developer

- 🌐 Portfolio: https://portafolio.kevinsvega.online
- 🐙 GitHub: https://github.com/proyectoskevinsvega
- 💼 LinkedIn: https://linkedin.com/in/kevins-yesid-vega-marmolejo-b403753ab
- 📧 Email: programadorkevinsvega@gmail.com

## 📄 Licencia

Proyecto personal - Todos los derechos reservados © 2026 Kevins Yesid Vega Marmolejo

---

**Última actualización**: Febrero 5, 2026

**Versión**: 1.0.0 - Production Ready ✅

Construido con ❤️ usando Next.js 16 + React 18 + PostgreSQL

