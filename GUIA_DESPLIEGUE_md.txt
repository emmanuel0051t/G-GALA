# 📚 Guía Completa: Subir a GitHub y Desplegar en Netlify

Esta guía te llevará paso a paso desde cero hasta tener tu aplicación publicada en internet.

## 📋 Requisitos Previos

1. ✅ Tener una cuenta en GitHub ([Crear cuenta gratis](https://github.com/signup))
2. ✅ Tener Git instalado en tu computadora ([Descargar Git](https://git-scm.com/downloads))

---

## 🎯 PARTE 1: Subir a GitHub desde tu Computadora

### **Paso 1: Verificar que Git está instalado**

Abre tu terminal/CMD y ejecuta:

```bash
git --version
```

Si ves un número de versión (ej: `git version 2.40.0`), ¡perfecto! Si no, descarga Git desde [git-scm.com](https://git-scm.com/downloads)

### **Paso 2: Configurar Git (solo la primera vez)**

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu-email@ejemplo.com"
```

> ⚠️ Usa el mismo email que usaste en GitHub

### **Paso 3: Descargar los archivos del proyecto**

1. Descarga los archivos adjuntos de esta conversación:
   - `index.html`
   - `README.md`
   - `.gitignore`
   - `eslint.config.cjs`

2. Crea una carpeta nueva en tu computadora (ej: `barberia-app`)

3. Coloca todos los archivos dentro de esa carpeta

### **Paso 4: Abrir la terminal en la carpeta del proyecto**

**En Windows:**
- Entra a la carpeta `barberia-app`
- Shift + Clic derecho → "Abrir ventana de PowerShell aquí"

**En Mac/Linux:**
- Abre la Terminal
- Navega a la carpeta: `cd ruta/a/barberia-app`

### **Paso 5: Inicializar Git**

Ejecuta estos comandos uno por uno:

```bash
# Inicializar repositorio Git
git init

# Ver archivos listos para agregar
git status

# Agregar todos los archivos
git add .

# Crear el primer commit
git commit -m "🎉 Primer commit: Sistema de gestión de citas para barbería"
```

### **Paso 6: Crear repositorio en GitHub**

**Opción A: Desde la Web (Más fácil)**

1. Ve a [github.com](https://github.com) e inicia sesión
2. Haz clic en el botón **"+"** (arriba a la derecha) → **"New repository"**
3. Rellena los datos:
   - **Repository name**: `barberia-app` (o el nombre que prefieras)
   - **Description**: "Sistema de gestión de citas para barbería"
   - **Visibility**: Public (para que funcione gratis en Netlify)
   - ❌ **NO marques** "Add a README file" (ya lo tenemos)
4. Clic en **"Create repository"**

**Opción B: Desde la Terminal (si tienes GitHub CLI)**

```bash
gh repo create barberia-app --public --source=. --remote=origin --push
```

### **Paso 7: Conectar tu carpeta local con GitHub**

Después de crear el repo en GitHub, verás instrucciones. Copia y ejecuta estos comandos:

```bash
# Agregar el repositorio remoto (REEMPLAZA "tu-usuario" con tu nombre de usuario de GitHub)
git remote add origin https://github.com/tu-usuario/barberia-app.git

# Renombrar la rama principal a "main" (estándar actual de GitHub)
git branch -M main

# Subir el código a GitHub
git push -u origin main
```

> 💡 **Tip**: GitHub te pedirá tu usuario y contraseña. Si tienes autenticación de dos factores, necesitarás crear un [Personal Access Token](https://github.com/settings/tokens).

### **Paso 8: Verificar que se subió correctamente**

1. Ve a `https://github.com/tu-usuario/barberia-app`
2. Deberías ver todos tus archivos
3. ¡Listo! Tu código está en GitHub 🎉

---

## 🌐 PARTE 2: Desplegar en Netlify

### **Método A: Conectar GitHub con Netlify (RECOMENDADO)**

Este método permite que cada vez que hagas cambios en GitHub, se actualice automáticamente en Netlify.

**Paso 1: Crear cuenta en Netlify**

1. Ve a [netlify.com](https://netlify.com)
2. Haz clic en **"Sign up"**
3. Selecciona **"Sign up with GitHub"** (más fácil)
4. Autoriza a Netlify

**Paso 2: Importar tu repositorio**

1. En Netlify, haz clic en **"Add new site"** → **"Import an existing project"**
2. Selecciona **"Deploy with GitHub"**
3. Autoriza a Netlify para acceder a tus repositorios
4. Busca y selecciona `barberia-app`

**Paso 3: Configurar el despliegue**

No necesitas cambiar nada, pero verifica:

- **Branch to deploy**: `main`
- **Build command**: (déjalo vacío)
- **Publish directory**: (déjalo vacío o pon `.`)

Haz clic en **"Deploy site"**

**Paso 4: ¡Tu sitio está en vivo!**

- Netlify te dará un enlace aleatorio como: `https://random-name-123.netlify.app`
- Espera 30-60 segundos para que se despliegue
- ¡Listo! Tu app está en internet 🚀

**Paso 5 (Opcional): Personalizar el dominio**

1. En Netlify, ve a **"Site settings"** → **"Domain management"**
2. Haz clic en **"Options"** → **"Edit site name"**
3. Cambia el nombre a algo como: `barberia-nombre.netlify.app`

---

### **Método B: Netlify Drop (Rápido, sin GitHub)**

Si solo quieres probar rápido:

1. Ve a [app.netlify.com/drop](https://app.netlify.com/drop)
2. Arrastra **solo** el archivo `index.html`
3. Obtendrás un enlace inmediato

> ⚠️ **Desventaja**: No se actualiza automáticamente. Tendrías que volver a arrastrar el archivo cada vez que hagas cambios.

---

## 🔄 Flujo de Trabajo: Actualizar tu Aplicación

Una vez conectado GitHub + Netlify, cada vez que quieras hacer cambios:

```bash
# 1. Edita tus archivos localmente

# 2. Ver qué cambió
git status

# 3. Agregar cambios
git add .

# 4. Crear commit
git commit -m "✨ Descripción de los cambios"

# 5. Subir a GitHub
git push

# 6. ¡Netlify actualiza automáticamente en ~30 segundos!
```

---

## 🎓 Comandos Git Útiles

```bash
# Ver el historial de commits
git log --oneline

# Ver diferencias antes de hacer commit
git diff

# Deshacer cambios locales (CUIDADO!)
git checkout -- archivo.html

# Ver repositorios remotos
git remote -v

# Actualizar desde GitHub (si trabajas en equipo)
git pull
```

---

## ❓ Solución de Problemas Comunes

### **Error: "git: command not found"**
- Instala Git desde [git-scm.com](https://git-scm.com/downloads)
- Reinicia tu terminal

### **Error: "remote origin already exists"**
```bash
git remote remove origin
git remote add origin https://github.com/tu-usuario/barberia-app.git
```

### **Error: "Permission denied" al hacer push**
- Verifica tu usuario y contraseña
- Si tienes 2FA, usa un [Personal Access Token](https://github.com/settings/tokens) en lugar de tu contraseña

### **Netlify no actualiza automáticamente**
- Verifica que el webhook esté activo en GitHub:
  - GitHub → Repo → Settings → Webhooks
  - Debería haber un webhook de Netlify

---

## 🎯 Próximos Pasos

Una vez desplegado, puedes:

1. ✅ Compartir el enlace con tus clientes
2. ✅ Agregar un dominio personalizado (ej: `mibarberia.com`)
3. ✅ Configurar HTTPS (Netlify lo hace automático)
4. ✅ Agregar más funcionalidades al código
5. ✅ Implementar un backend real en el futuro

---

## 📞 ¿Necesitas Ayuda?

Si tienes problemas en algún paso:

1. Lee los mensajes de error completos
2. Busca en Google el mensaje exacto
3. Consulta la documentación oficial:
   - [GitHub Docs](https://docs.github.com)
   - [Netlify Docs](https://docs.netlify.com)

---

¡Felicidades! 🎉 Has aprendido a desplegar una aplicación web profesionalmente.
