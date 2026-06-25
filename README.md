# Assistcargo + Chubb · Landing de captación

Landing page para captar AVLs/empresas GPS interesadas en monetizar su cartera de transportistas con seguro de carga por viaje de Chubb.

## Stack

- HTML/CSS/JS vanilla (sin frameworks)
- Form conectado a Base44 (entidad `Lead` del proyecto Tryger Agentes)
- Redirige a Calendly después del submit

## Cómo funciona el flujo

1. Visitor entra a la landing
2. Llena el form (nombre, empresa, email)
3. Submit → `POST` a la API de Base44 → crea un `Lead` con `origen: landing_assistcargo`
4. Redirige a Calendly con `name`, `email` y `empresa` pre-cargados
5. Visitor agenda → Calendly notifica a los organizadores

## Deploy en Vercel

1. Subir el repo a GitHub (manual desde github.com → "New repository" → `assistcargo-landing`)
2. Entrar a [vercel.com](https://vercel.com) con tu cuenta de GitHub
3. Click "Add New..." → "Project"
4. Importar el repo `natsanro/assistcargo-landing`
5. Click "Deploy" (sin configuración adicional, es estático)
6. Listo: te queda en `assistcargo-landing.vercel.app`

## Custom domain (opcional)

En Vercel → Project Settings → Domains → Agregar el dominio que quieras.

## Variables a actualizar

En `index.html`, dentro del `<script>` al final:

- `BASE44_API_URL`: URL del endpoint Lead (ya configurado para Tryger Agentes)
- `BASE44_API_KEY`: api_key de Base44
- `CALENDLY_URL`: link de Calendly (actualmente `https://calendly.com/hola-tryger/30min`)

## ⚠️ Nota de seguridad

La API key de Base44 está expuesta en el cliente. Como el único permiso necesario es `create Lead`, el riesgo es bajo (alguien podría crear leads basura, pero no leer ni borrar datos). Si querés más seguridad, migrar el POST a una serverless function de Vercel.
