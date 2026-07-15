# Campaña de captación AVL · Assistcargo + Chubb

Secuencia de 3 mails que Assistcargo envía a sus **empresas de GPS integradas**
para ofrecerles el seguro de carga por viaje (operado por Chubb, plataforma Tryger)
como nueva fuente de ingresos sobre su cartera actual.

Los 3 mails llevan a la **landing** (`../index.html` → https://assistcargo-landing.vercel.app),
que amplía el detalle. La landing y los mails se actualizan juntos.

## La secuencia

| # | Archivo | Cuándo | Objetivo |
|---|---------|--------|----------|
| 1 | `CAPTACION_01_ANUNCIO` | Día 1 | Presentar la oportunidad y contar la historia (por qué existe) |
| 2 | `CAPTACION_02_CASOS` | Día 4–5, a quienes abrieron | De dónde sale el ingreso + los 4 beneficios |
| 3 | `CAPTACION_03_ULTIMA_CHANCE` | Día 8–10, sin respuesta | Cierre con urgencia (grupo piloto) |

Cada uno tiene su `.html` (editable) y su `.pdf` (regenerado desde el HTML con Chrome).

## Decisiones de la reunión con José Luis aplicadas

- **Audiencia fría:** son empresas de GPS que no saben nada de seguros. Primero se
  despierta intriga y se cuenta la historia; recién después el cálculo.
- **Arranque corregido (mail 1):** se eliminó la frase "estar integrado con Assistcargo
  no te traía ningún beneficio". Ahora arranca reconociendo el prestigio que ya da
  Assistcargo y sumando la propuesta de negocio.
- **Sin protagonismo de Chubb:** a una empresa de GPS le da igual la marca de la
  aseguradora. Chubb aparece como respaldo, no como titular.
- **Foco en la cartera actual:** rentabilizar el stock de clientes que ya tienen; no es
  salir a vender seguros, no es exclusividad. Los productos son para SUS clientes.
- **Sin nombrar empresas:** no se mencionan otros AVLs (Ontracking / Atlántida) por
  privacidad y para no desincentivar. Se habla de "otras empresas de GPS" en genérico.
- **4 beneficios:** capitalizas tu cartera · fidelizas a tus clientes · aumentas el valor
  de tu marca · reactivas prospectos.

## Antes de enviar

- Reemplazar `[NOMBRE]` por el nombre del contacto (campo de combinación del ESP).
- Verificar que el link de la landing apunte al dominio final (hoy: `assistcargo-landing.vercel.app`).
- Remitente reconocible de Assistcargo. Firma: **Equipo Assistcargo · En alianza con Chubb**.

## Regenerar los PDF

```bash
cd emails
CHROME="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
for f in CAPTACION_01_ANUNCIO CAPTACION_02_CASOS CAPTACION_03_ULTIMA_CHANCE; do
  "$CHROME" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf="$f.pdf" "file://$PWD/$f.html"
done
```
