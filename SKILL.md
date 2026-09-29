---
name: cierre-mes-tarjetas
description: Cierra el mes de gastos leyendo los movimientos
  facturados de mis tarjetas de crédito en el portal del banco
  (yo inicio sesión, tú lees), los cuadra al peso contra el total
  facturado y me dice en qué se fue la plata. Úsala cuando diga
  "cerremos el mes", "en qué gasté", "actualiza mis gastos" o
  "ya facturó la tarjeta". NO pagas tarjetas ni mueves plata.
---

# Cierre del mes de tarjetas

Mis tarjetas: [BANCO 1, tarjeta terminada en XXXX] y
[BANCO 2, tarjeta terminada en XXXX].
Mis gastos viven en [carpeta, ej: ~/finanzas/].

## Regla que no se rompe
Ninguna cifra entra al resumen sin cuadrar AL PESO contra el
"monto facturado" que imprime el banco. Si no cuadra, detente,
muéstrame la diferencia y no sigas. Nunca ajustes una fila para
que cuadre.

## Autenticación
Mis claves no pasan por ti. Abre el portal de cada banco y
espera a que yo diga "listo". No escribas mi RUT ni toques los
campos de clave.

## Cuándo correrla
Después de la fecha de facturación de cada tarjeta. Antes, el
mes todavía no existe: solo hay "no facturados".

## Bajar los movimientos
Por cada tarjeta, entra a MOVIMIENTOS FACTURADOS (no a los no
facturados) y anota el "monto total facturado" y la fecha
límite de pago.
Si el banco tiene botón de descarga (Excel), úsalo. Si no,
lee la tabla de la página. Guarda cada tarjeta como
[carpeta]/AAAA-MM-banco.csv con columnas fecha,detalle,monto.
Si una fila no trae fecha, lleva la de la fila anterior.

## Qué NO es gasto (sácalo antes de sumar)
- El pago del mes anterior ("monto cancelado", "pago", "abono").
- Las filas de cuotas 00/NN: informan una compra en cuotas nueva,
  pero no son cargo de este mes.
- Nunca borres filas "repetidas": dos cargos iguales el mismo
  día (el metro, un café) suelen ser reales.
Con eso: suma de compras + comisiones = monto facturado.

## Compras en dólares
Si la tarjeta factura aparte en USD, cuádrala en USD contra su
propio total. No la conviertas antes de cuadrar.

## Clasificar
Usa las reglas de [carpeta]/reglas.csv (patrón,categoría).
Si un comercio no calza con ninguna, NO adivines: júntalos todos
y pregúntame en una sola lista. Mis respuestas se agregan a
reglas.csv para que no me vuelvas a preguntar.

## Resumen
Entrégame: total gastado del mes y variación contra el mes
anterior; gasto por categoría, de mayor a menor; cuánto pagar
en cada tarjeta y hasta cuándo; y una tabla por tarjeta con
total del banco, suma leída y si cuadró.

## Al terminar
Recuérdame cerrar sesión en los bancos.
