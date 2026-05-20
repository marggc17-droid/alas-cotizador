# 🦅 Alas Uniformex - Sistema de Cotización

Sistema web de cotización y consulta de precios para uniformes industriales B2B.

![Version](https://img.shields.io/badge/version-3.0-E91E8C)
![Status](https://img.shields.io/badge/status-production-9C27B0)

## 🚀 Acceso Rápido

**🔗 Abrir App:** [https://TU-USUARIO.github.io/alas-cotizador](https://TU-USUARIO.github.io/alas-cotizador)

> ⚠️ Reemplaza `TU-USUARIO` con tu nombre de usuario de GitHub después de subir el proyecto

---

## 📱 Uso desde Celular

### Para iOS (iPhone/iPad):
1. Abre Safari y ve a la URL de la app
2. Toca el botón de compartir (cuadro con flecha)
3. Selecciona **"Agregar a pantalla de inicio"**
4. ¡Listo! Ahora tienes un ícono como app nativa

### Para Android:
1. Abre Chrome y ve a la URL de la app
2. Toca el menú (tres puntos)
3. Selecciona **"Agregar a pantalla de inicio"**
4. ¡Listo! Funciona como una app instalada

---

## ✨ Características

### 🔍 Catálogo Inteligente
- Búsqueda por código, nombre, marca o descripción
- Filtros rápidos por categoría (Polo, Chamarra, Playera, etc.)
- Scoring inteligente: resultados exactos primero
- Sincronización automática con Google Sheets

### 💰 Cotización Profesional
- Multi-selección de productos con cantidades
- Tallas obligatorias (XS-XL, 2XL) y opcionales (3XL, 4XL)
- Cálculo automático: Subtotal + ISR (morales) + IVA
- Productos sin talla (servicios, bordado)
- Edición de precios para productos custom

### 👥 Gestión de Clientes
- Base de clientes con autocompletado
- Detección automática de clientes nuevos
- Razón social y tipo de persona (Moral/Física)
- Validación de correo antes de enviar

### 📄 Exportación
- PDF con formato corporativo de Alas Uniformex
- Resumen formateado para WhatsApp (un toque para copiar)
- Email con cotización adjunta
- Guardado automático en Google Drive

---

## 🎨 Colores Corporativos

- **Rosa/Magenta:** `#E91E8C`
- **Morado:** `#9C27B0`

---

## 🔧 Configuración Técnica

### API Google Apps Script

La app se conecta a Google Sheets mediante Apps Script Web App:

```javascript
const API_URL = "https://script.google.com/macros/s/TU_SCRIPT_ID/exec";
const API_TOKEN = "alas2026xyz";
```

**Para actualizar tu propio backend:**
1. Abre tu Google Sheet
2. Ve a **Extensiones → Apps Script**
3. Despliega como Web App
4. Copia la URL y reemplázala en `index.html` línea 49

### Estructura de Datos

#### Producto
```json
{
  "code": "K500",
  "brand": "Port Authority",
  "name": "Silk Touch Polo",
  "desc": "Polo básico corporativo, el más pedido",
  "type": "Polo",
  "sinTalla": false,
  "price": 320,
  "price2xl": 352,
  "price3xl": 384,
  "price4xl": 416
}
```

#### Cliente
```json
{
  "nombre": "Juan Pérez",
  "empresa": "Acme Corp",
  "correo": "juan@acme.com",
  "telefono": "8112345678",
  "cuenta": "Acme Corp SA de CV"
}
```

---

## 📊 Backend (Google Sheets)

### Hojas Requeridas:

1. **Cotizador**: Precios maestros por talla
2. **PriceAutomaticScript**: Lista de productos actualizable
3. **TiendaNube_Export**: Sincronización con tienda online
4. **Clientes**: Base de datos de clientes
5. **Cotizaciones**: Historial de cotizaciones generadas

### Apps Script Menús:
- **⚡ Precios**: Actualización automática (SanMar, SportsWear, BAW)
- **🛒 Tienda Nube**: Exportación CSV para importar precios

---

## 👥 Equipo

**Vendedores:**
- Debanhi Jiménez
- Catarino Gómez
- Margarita Gómez
- Margarita Carreño

**Contacto:**
- 📧 ventas@alasuniformex.com
- 📱 8110155997 / 8115088362
- 🌐 [alasuniformex.com](https://alasuniformex.com)

---

## 📁 Archivos del Proyecto

```
alas-cotizador/
├── index.html              # App principal (React standalone)
├── README.md               # Este archivo
├── PROJECT_MEMORY.md       # Contexto del sistema de cotización
├── project-context.md      # Contexto del sistema de precios
└── docs/
    └── (documentación adicional)
```

---

## 🛠️ Desarrollo Local

Para probar cambios localmente:

```bash
# Opción 1: Abrir directamente en el navegador
open index.html

# Opción 2: Servidor local simple
python3 -m http.server 8000
# Luego abre http://localhost:8000
```

---

## 🔐 Seguridad

- ✅ Token de API incluido (para backend controlado)
- ✅ Validación de correos antes de envío
- ✅ Sin datos sensibles en el código
- ⚠️ Si expones públicamente, considera autenticación adicional

---

## 📝 Notas Técnicas

### Stack:
- **Frontend**: React 18 (standalone, sin build)
- **PDF**: jsPDF + autoTable
- **Backend**: Google Apps Script
- **Storage**: Google Drive + Sheets
- **Responsive**: Mobile-first design

### Browser Support:
- ✅ Chrome/Edge (recomendado)
- ✅ Safari iOS
- ✅ Chrome Android
- ⚠️ Firefox (puede requerir ajustes en PDF)

---

## 🚀 Próximas Mejoras

- [ ] PWA completa (service worker para offline)
- [ ] Notificaciones push para nuevas cotizaciones
- [ ] Firma digital en PDFs
- [ ] Exportación a Excel
- [ ] Dashboard de estadísticas de ventas
- [ ] Integración con WhatsApp Business API

---

## 📄 Licencia

© 2026 Alas Uniformex. Todos los derechos reservados.

Uso interno exclusivo del equipo de ventas.

---

## 🆘 Soporte

¿Problemas con la app?

1. Revisa que tengas conexión a internet
2. Verifica que el API_URL esté actualizado
3. Borra caché del navegador (Ctrl+Shift+R)
4. Contacta a sistemas: margarita.gomez@metalsa.com

---

**Última actualización:** Mayo 2026 | **Versión:** 3.0
