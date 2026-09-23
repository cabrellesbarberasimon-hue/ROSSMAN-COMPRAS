# Calendario de Displays · Dpto. Compras Rossmann

App web creada a partir del libro Excel `lorena.xlsx` (hojas *Instrucciones*, *Resumen*, *Calendario Displays*, *Vista Anual KW* y *Listas*).

Abre `index.html` en el navegador: no necesita instalación ni servidor.

## Qué hace

| Pestaña | Equivale en el Excel a | Función |
|---|---|---|
| **Resumen** | Resumen | Indicadores (activos, planificados, finalizados, arrancan/terminan en 4 semanas, acciones pendientes, sin marca/EAN, tiendas y unidades), recuento por tipo × estado y lista de displays activos y próximos. |
| **Calendario** | Calendario Displays | Tabla de displays con búsqueda y filtros (estado, tipo, acciones pendientes, datos incompletos). Alta, edición, duplicado y borrado en un panel lateral. |
| **Vista anual KW** | Vista Anual KW | Gantt por semanas ISO (1–52/53) con la KW actual resaltada y recuento de displays por semana para ver solapamientos. |
| **Listas** | Listas | Opciones editables de *Tipo display*. |
| **Instrucciones** | Instrucciones | Guía de uso. |

Cálculos automáticos (igual que las fórmulas del Excel):

- **ID**: D001, D002… por orden de alta.
- **Fecha inicio / fin**: lunes de la KW de inicio y domingo de la KW de fin (semanas ISO).
- **Semanas**: `KW fin − KW inicio + 1`.
- **Estado**: Planificado / Activo / Finalizado según la fecha de hoy.
- **Acciones pendientes**: acciones MKT-RRSS, promo instore y promo folleto marcadas «Sí» cuyo *Gestionado* no es «Sí».

Validaciones: descripción obligatoria, EAN de 8 o 13 dígitos, KW entre 1 y 52/53, KW fin ≥ KW inicio. Marca y EAN vacíos se marcan en amarillo.

## Excel

- **Importar Excel…** lee la hoja *Calendario Displays* del libro original (u otro con la misma cabecera) y añade los displays que no existan ya.
- **Exportar Excel** genera un `.xlsx` con todas las columnas, incluidas las calculadas.

## Datos

Abierta localmente, la app guarda los datos en el navegador (`localStorage`) y arranca con los 4 displays del Excel como ejemplo. Publicada como artifact de claude.ai, usa una base de datos compartida por todo el equipo.

---

# Análisis de Golpes · `golpes.html`

App web creada a partir del libro `ANALISIS_GOLPES_DESDE_MARZO_26.xlsx` (hojas *Análisis golpes*, *Hoja1* y *Hoja2*). Abre `golpes.html` en el navegador; arranca con las 61 incidencias de *Hoja1*.

| Pestaña | Equivale en el Excel a | Función |
|---|---|---|
| **Resumen** | Análisis golpes (resúmenes) y Hoja2 | Indicadores (incidencias, golpes, pérdidas de agencia, transporte y familia con más incidencias, provincias, clientes repetidos), barras por familia + modelo, transporte y provincia, evolución mensual y matriz transporte × provincia (sustituye al «desglose MEDITERRANEO por provincia» para todos los transportes). Pulsa cualquier barra o celda para ver esas incidencias. |
| **Incidencias** | Hoja1 / detalle | Tabla con búsqueda y filtros por transporte, provincia, familia y tipo. Alta, edición y borrado en un panel lateral. |
| **Normalización** | Notas de la hoja *Análisis golpes* | Reglas editables que agrupan transportes (`TRANSP. MEDITERR. EXPRES, S.L.` → mediterraneo), localidades → provincia (`VIGO` → Pontevedra) y artículo → familia + modelo, más una lista de lo que falta por revisar. |

- **Periodo**: el selector de la cabecera filtra por *fecha albarán* (por defecto desde 01/03/2026, como el Excel; también desde febrero, año 2026, últimos 90 días, todo o rango personalizado).
- **Tipo**: «Pérdida» cuando el artículo dice *pierde agencia* / *perdida*; si no, «Golpe».
- **Familia + modelo**: gana el patrón que aparece antes en la descripción; se puede fijar a mano en cada incidencia (igual que la columna D editable del Excel).
- **Importar Excel…** lee una hoja con las columnas de *Hoja1* (`fecha albaran`, `ARTICULOS GOLPEADOS`, `Su número`…) y añade solo las incidencias nuevas. **Exportar Excel** genera *Detalle*, *Resumen* y *Transporte x Provincia* del periodo y filtros activos.
