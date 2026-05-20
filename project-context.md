# Project Context — Actualización de Precios Tienda Nube

> Documento de transferencia. Cárgalo al inicio de cualquier proyecto/conversación nueva con Claude para que tenga todo el contexto del sistema sin re-explicar.

---

## 1. Resumen ejecutivo

Sistema automatizado para mantener los precios de la tienda online (Tienda Nube) sincronizados con los precios maestros del Cotizador. Resuelve el problema de **importaciones CSV con formato incompatible** que dejaban precios en blanco.

- **Negocio:** Apparel / uniformes B2B con personalización (marca "Alas" / similar)
- **Plataforma e-commerce:** Tienda Nube
- **Proveedores principales:** SanMar, SanMar Premium, SportsWear, BAW
- **Stack técnico:** Google Sheets + Google Apps Script + Google Drive
- **Usuario / owner:** Margarita Gómez (margarita.gomez@metalsa.com)

---

## 2. Arquitectura — flujo de 3 capas

```
┌──────────────────┐     ┌─────────────────────┐     ┌──────────────────┐
│ CAPA 1 · MAESTRA │ ──> │ CAPA 2 · STAGING    │ ──> │ CAPA 3 · OUTPUT  │
│ Cotizador        │     │ TiendaNube_Export   │     │ Apps Script CSV  │
│ (precios fuente) │     │ (30 cols + 3 aux)   │     │ (carpeta Drive)  │
└──────────────────┘     └─────────────────────┘     └──────────────────┘
```

**Principio clave:** una sola fuente de verdad (Cotizador) → staging que respeta el esquema oficial de TN → script que blinda el formato al generar CSV. Cero edición manual del archivo final.

---

## 3. Apps Script — 2 archivos en un proyecto

### `ActualizarPrecios.gs`
Scraping de SanMar + menú principal.

### `GenerarCSV_TiendaNube.gs`
Flujo de exportación a TN.

### Menú resultante en el spreadsheet

```
⚡ Precios                                    🛒 Tienda Nube
├── 💲 Actualizar TODOS — solo precios        ├── 📋 Aplicar nuevos precios (AE → J)
├── 💲📝 Actualizar TODOS — precios + nombres ├── 🔍 Validar hoja TiendaNube_Export
├── 💲 Actualizar MARCADOS — solo precios     ├── 🛒 Generar CSV para Tienda Nube
├── 💲📝 Actualizar MARCADOS — precios + nom. └── 📁 Abrir carpeta de CSVs
├── Ver instrucciones SportsWear
└── Ver instrucciones BAW
```

---

## 4. Flujo de trabajo recurrente

| # | Acción | Dónde |
|---|---|---|
| 1 | `⚡ Precios → Actualizar MARCADOS` | Google Sheets |
| 2 | Revisar `TiendaNube_Export` | Google Sheets |
| 3 | `🛒 Tienda Nube → Aplicar nuevos precios` | Google Sheets |
| 4 | `🛒 Tienda Nube → Generar CSV` | Google Sheets |
| 5 | Descargar CSV desde Drive | Google Drive |
| 6 | Importar CSV en Tienda Nube | Tienda Nube |
| 7 | Validar productos | Tienda Nube |

---

**Última actualización:** Mayo 2026
