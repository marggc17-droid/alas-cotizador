# 📘 Guía Completa: Subir a GitHub y Acceder desde Celular

## 🎯 Objetivo
Publicar tu app de cotización en GitHub Pages para que tus vendedoras puedan acceder desde cualquier celular con solo abrir un link.

---

## 📋 REQUISITOS PREVIOS

### 1. Crear cuenta en GitHub (si no tienes)
1. Ve a [github.com](https://github.com)
2. Click en **"Sign up"**
3. Completa el registro con tu email
4. Verifica tu correo

### 2. Instalar Git en tu computadora

#### Windows:
1. Descarga desde [git-scm.com](https://git-scm.com/download/win)
2. Ejecuta el instalador
3. Acepta todas las opciones por defecto
4. Abre **Git Bash** (se instaló con Git)

#### Mac:
1. Abre **Terminal** (Cmd + Espacio → escribe "Terminal")
2. Escribe: `git --version`
3. Si no está instalado, te pedirá instalarlo automáticamente

---

## 🚀 PASO A PASO COMPLETO

### PASO 1: Preparar tu proyecto local

#### Opción A: Si descargaste esta carpeta completa
```bash
# Abre Terminal/Git Bash
# Navega a la carpeta del proyecto
cd /ruta/donde/descargaste/alas-cotizador

# Verifica que estés en la carpeta correcta (debe mostrar index.html)
ls
```

#### Opción B: Si solo tienes el archivo HTML
```bash
# Crea una carpeta nueva
mkdir alas-cotizador
cd alas-cotizador

# Copia el archivo HTML y renómbralo
# En Windows:
copy "C:\ruta\ConsultaPrecios-v3.html" index.html

# En Mac:
cp ~/Downloads/ConsultaPrecios-v3.html index.html
```

---

### PASO 2: Inicializar Git en tu proyecto

```bash
# Dentro de la carpeta alas-cotizador
git init

# Configurar tu identidad (solo la primera vez)
git config --global user.name "Tu Nombre"
git config --global user.email "tu-email@example.com"
```

**✅ Resultado esperado:**
```
Initialized empty Git repository in /ruta/alas-cotizador/.git/
```

---

### PASO 3: Agregar archivos al repositorio

```bash
# Ver qué archivos tienes
ls

# Agregar TODOS los archivos al staging
git add .

# Verificar qué se agregó (debe mostrar todos los archivos en verde)
git status

# Hacer el primer commit
git commit -m "Primera versión del cotizador Alas Uniformex"
```

**✅ Resultado esperado:**
```
[main (root-commit) abc1234] Primera versión del cotizador Alas Uniformex
 4 files changed, 850 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 README.md
 create mode 100644 PROJECT_MEMORY.md
 create mode 100644 index.html
```

---

### PASO 4: Crear repositorio en GitHub

1. Ve a [github.com](https://github.com) e inicia sesión
2. Click en el **＋** (arriba a la derecha) → **"New repository"**
3. Llena el formulario:
   - **Repository name:** `alas-cotizador`
   - **Description:** "Sistema de cotización - Alas Uniformex"
   - **Visibilidad:** 
     - ✅ **Public** (si quieres que sea accesible con solo el link)
     - 🔒 **Private** (si prefieres control de acceso — tus vendedoras necesitarán cuenta GitHub)
   - ⚠️ **NO marques:** "Add a README file" (ya lo tienes)
4. Click en **"Create repository"**

**📸 Captura de lo que verás:**
```
Quick setup — if you've done this kind of thing before
HTTPS | SSH
https://github.com/TU-USUARIO/alas-cotizador.git
```

---

### PASO 5: Conectar tu proyecto local con GitHub

Copia los comandos que GitHub te muestra (sección "push an existing repository"):

```bash
# Agregar el repositorio remoto (REEMPLAZA TU-USUARIO)
git remote add origin https://github.com/TU-USUARIO/alas-cotizador.git

# Renombrar la rama principal a "main" (si no lo está)
git branch -M main

# Subir tu código a GitHub
git push -u origin main
```

**🔐 Autenticación:**
- GitHub te pedirá usuario y contraseña
- Si tienes autenticación de dos factores, necesitarás un **Personal Access Token**:
  1. Ve a GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
  2. Generate new token → Marca `repo` → Generate
  3. Copia el token y úsalo en lugar de tu contraseña

**✅ Resultado esperado:**
```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (5/5), 25.3 KiB | 2.5 MiB/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To https://github.com/TU-USUARIO/alas-cotizador.git
 * [new branch]      main -> main
```

---

### PASO 6: Activar GitHub Pages

1. Ve a tu repositorio en GitHub
2. Click en **"Settings"** (⚙️ arriba a la derecha)
3. En el menú lateral izquierdo, busca **"Pages"** (abajo)
4. En **"Source"**, selecciona:
   - Branch: **main**
   - Folder: **/ (root)**
5. Click en **"Save"**

**⏱️ Espera 2-3 minutos** mientras GitHub despliega tu sitio.

**✅ Verás un mensaje:**
```
Your site is live at https://TU-USUARIO.github.io/alas-cotizador/
```

---

### PASO 7: Verificar que funciona

1. Abre el link en tu navegador
2. Deberías ver tu app funcionando
3. Prueba desde tu celular también

⚠️ **Si ves error 404:**
- Espera 5 minutos más
- Verifica que el archivo se llame **exactamente** `index.html` (no `Index.html` ni `index.htm`)
- Refresca con Ctrl+Shift+R (o Cmd+Shift+R en Mac)

---

## 📱 COMPARTIR CON TUS VENDEDORAS

### Opción 1: Link directo
Compárteles el link por WhatsApp:
```
🦅 Alas Cotizador
https://TU-USUARIO.github.io/alas-cotizador/

Ábrelo en Safari (iOS) o Chrome (Android) 
y agrégalo a tu pantalla de inicio.
```

### Opción 2: QR Code
1. Ve a [qr-code-generator.com](https://www.qr-code-generator.com/)
2. Pega tu URL
3. Descarga el QR
4. Imprímelo y ponlo en la oficina

---

## 🔄 ACTUALIZAR LA APP EN EL FUTURO

Cuando hagas cambios al código:

```bash
# 1. Edita el archivo index.html

# 2. Guarda los cambios
git add index.html

# 3. Crea un commit
git commit -m "Descripción de lo que cambiaste"

# 4. Sube a GitHub
git push

# 5. Espera 2-3 minutos y refresca la app
```

**💡 Tip:** Tus vendedoras deberán refrescar la página (o borrar caché) para ver los cambios.

---

## ❓ RESOLUCIÓN DE PROBLEMAS

### Problema: "Permission denied (publickey)"
**Solución:** Usa HTTPS en lugar de SSH:
```bash
git remote set-url origin https://github.com/TU-USUARIO/alas-cotizador.git
```

### Problema: "src refspec main does not match any"
**Solución:** Asegúrate de haber hecho commit:
```bash
git commit -m "Initial commit"
git push -u origin main
```

### Problema: La app carga pero no funciona
**Solución:** 
1. Abre la consola del navegador (F12)
2. Busca errores rojos
3. Revisa que el `API_URL` en línea 49 del HTML sea correcto

### Problema: "Refusing to merge unrelated histories"
**Solución:**
```bash
git pull origin main --allow-unrelated-histories
git push
```

---

## 🎓 RECURSOS ADICIONALES

- **Git Tutorial:** [learngitbranching.js.org](https://learngitbranching.js.org/)
- **GitHub Docs:** [docs.github.com/es](https://docs.github.com/es)
- **Video Tutorial:** Busca "GitHub Pages tutorial español" en YouTube

---

## 📞 SOPORTE

Si tienes problemas:
1. Lee la sección de problemas comunes arriba
2. Busca el error en Google
3. Pregunta en la comunidad: [stackoverflow.com](https://stackoverflow.com)

---

**¡Listo! 🎉** Tu app ya está en línea y accesible desde cualquier dispositivo.
