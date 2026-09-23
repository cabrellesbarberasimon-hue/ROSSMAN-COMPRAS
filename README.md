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
