# PROYECTO: Alas Uniformex — Sistema de Cotización y Precios
## Archivo de contexto para continuar en nueva sesión de IA

---

## 🏢 NEGOCIO

- **Empresa:** Alas Uniformex — Maquila y Suministro de Uniformes Industriales
- **Web:** alasuniformex.com | **Email:** ventas@alasuniformex.com | **Tel:** 8110155997 / 8115088362
- **Modelo:** B2B, uniformes corporativos con bordado/serigrafía personalizada
- **Operación:** Pedidos por WhatsApp y correo. Tienda Nube solo como catálogo visual de referencia
- **Vendedores:** Debanhi Jiménez, Catarino Gómez, Margarita Gómez, Margarita Carreño
- **Colores corporativos:** Rosa/Magenta `#E91E8C` y Morado `#9C27B0`

---

## ⚙️ SISTEMA DE PRECIOS — 3 FUENTES

### 1. Google Sheet C25 (archivo maestro)
- **Hoja clave:** `PriceAutomaticScript` (antes Sheet12)
- **Columnas:** A=Code, B=Brand, C=Name, D=Price (USD)
- **Marcas activas:** SanMar, SanMar Premium, SportsWear, BAW, Alas (interna)
- **Precios:** en USD, se convierten a MXN con TC + margen por tipo

### 2. Apps Script — Actualización automática de precios
- **Archivo:** `ActualizarPrecios.gs`
- **Menú creado:** `⚡ Precios` en Google Sheets
- **SanMar/SanMar Premium:** fetch automático desde `companycasuals.com/fully/b.jsp?customer=fully&todo=search&showPrice=Yes&query={CODE}` — FUNCIONA ✅
- **SportsWear (SS Active Wear):** ssactivewear.com devuelve **403** al fetch de Apps Script — actualización MANUAL
- **BAW:** precios no públicos, requiere lista de precio de proveedor — actualización MANUAL
- **Toast de progreso:** visible durante ejecución con contador X de Y
- **Al terminar:** alerta con resumen de actualizados y no encontrados

### 3. React App — ConsultaPrecios.jsx
- Herramienta interna de consulta y cotización (ver sección completa abajo)

---

## 📋 ESTRUCTURA DE DATOS RECOMENDADA — BASE DE PRODUCTOS

### Campo `sinTalla: boolean`
- `false` = producto con tallas (ropa): tiene price, price2xl, price3xl, price4xl
- `true` = producto sin talla (servicios, bordado, productos custom): price único aplica a todas

### Estructura completa por producto:
```json
{
  "code": "K500",
  "brand": "Port Authority",       // Marca visible al cliente
  "name": "Silk Touch Polo",       // Nombre completo
  "desc": "Polo básico corporativo, el más pedido",  // Descripción INTERNA equipo
  "type": "Polo",                  // Categoría: Polo|Chamarra|Playera|Camisa|Servicio|Custom
  "sinTalla": false,
  "price": 320,                    // XS-XL en MXN
  "price2xl": 352,                 // 2XL en MXN
  "price3xl": 384,                 // 3XL en MXN
  "price4xl": 416,                 // 4XL en MXN
  "proveedor": "SanMar"           // Campo interno (NO mostrar al cliente)
}
```

---

## 📱 REACT APP — ConsultaPrecios.jsx

### Estado actual (versión más reciente):
**3 vistas:** Catálogo → Selección → Cotización

#### ✅ Funcionalidades implementadas:
- Búsqueda por código, nombre, descripción interna, marca, tipo
- Tags rápidos de categoría
- Multi-selección de productos con cantidades
- Tallas: XS-XL y 2XL **obligatorias**, 3XL y 4XL **opcionales** (botón +)
- Edición de precio inline con opción "Actualizar en catálogo" (solo Custom/Alas)
- Productos sin talla (Servicio/Custom): solo cantidad, sin selector de talla
- Agregar producto no encontrado: nombre + precio + descripción → código CUST-XXX auto-generado
- Toggle Persona Moral / Física → ISR aplica solo a morales
- Cálculo automático: subtotal, ISR (1.25% morales), IVA (16%), total
- Copiar resumen formateado para WhatsApp
- Buscador de clientes (por nombre, empresa, correo)
- Detección de cliente nuevo con alerta + botón guardar
- PDF con formato exacto de cotizaciones Alas (encabezado, tabla, términos, firma)
- Validación de correo con modal antes de abrir mailto
- Botón "＋ Nueva" para limpiar todo con confirmación
- Branding: colores rosa #E91E8C y morado #9C27B0

#### ⏳ Pendiente de implementar:
- Conexión con Google Sheet como backend (Google Sheets API o Apps Script Web App)
- Guardar PDFs en Google Drive / iCloud (requiere OAuth)
- Persistencia de clientes y catálogo entre sesiones (localStorage o Sheets)

---

**Última actualización:** Mayo 2026
