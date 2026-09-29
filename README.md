# cierre-mes-tarjetas

Una skill para Claude que cierra el mes de tus tarjetas de crédito: abre el portal de tu banco en
el navegador, lee los movimientos facturados, los **cuadra al peso contra el total que imprime el
banco** y te dice en qué se fue la plata.

Tú inicias sesión en el banco. La skill solo lee: no escribe tus claves, no paga tarjetas y no
mueve plata.

## Qué hace

1. Abre el portal de cada banco y espera a que entres con tu clave.
2. Lee los movimientos facturados de cada tarjeta y los guarda en un CSV.
3. Suma todo y lo compara con el "monto facturado" del estado de cuenta. **Si no cuadra al peso,
   se detiene** y te muestra la diferencia en vez de darte un número que parece bueno.
4. Clasifica cada gasto con tus reglas. Si aparece un comercio que no conoce, no adivina: te
   pregunta, y tu respuesta queda como regla para los meses siguientes.
5. Te entrega el resumen: total del mes, gasto por categoría, cuánto pagar y hasta cuándo.

## Requisitos

- **Claude Code**, o Claude en el escritorio con la extensión de Chrome: la skill necesita un
  agente que pueda ver y recorrer páginas web.
- Tu sesión del banco abierta, iniciada por ti.

## Instalación

```bash
git clone https://github.com/clabza16/cierre-mes-tarjetas ~/.claude/skills/cierre-mes-tarjetas
```

Después abre `~/.claude/skills/cierre-mes-tarjetas/SKILL.md` y cambia lo que está entre
`[corchetes]`: tus bancos, las tarjetas y la carpeta donde quieres guardar los gastos. Copia
`reglas.ejemplo.csv` a esa carpeta como `reglas.csv`.

Reinicia tu agente (las skills se cargan al arrancar) y dile:

> Cerremos el mes

## La primera vez

- **Quédate mirando.** Cada banco esconde los movimientos en un menú distinto. Cuando el agente
  encuentre el camino, pídele que lo agregue a la skill: la segunda vez va directo.
- **Casi todo va a caer en "Otros".** Es normal: `reglas.csv` parte casi vacío. Respóndele la
  lista de comercios una vez y desde el segundo mes solo pregunta por los nuevos.
- **Córrela después de la fecha de facturación.** Antes solo hay movimientos "no facturados", que
  no tienen un total contra el cual cuadrar.

## Si la suma no cuadra

Casi siempre es una de tres cosas: el pago del mes anterior contado como gasto, una fila de
cuotas `00/NN` (informa una compra en cuotas nueva, no es cargo del mes), o una fila leída dos
veces porque la tabla tenía varias páginas. Ojo: dos cargos iguales el mismo día suelen ser
reales; no los borres como duplicados.

## Guía paso a paso

https://www.consultoria-info.cl/guia-gastos

---

Hecha por [Claudio Albornoz](https://www.instagram.com/calbornoz.ia/) · ConsultorIA.
No es asesoría financiera. Nunca le des a un agente acceso para pagar ni transferir.
