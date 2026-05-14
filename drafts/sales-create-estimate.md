---
title: Crear un presupuesto
description: >-
  Genera un presupuesto para un cliente. No tiene efectos fiscales y se puede convertir en factura o
  albarán cuando se acepta.
state: draft
parent_ids:
  - 19634621
meta:
  sources_of_truth:
    docs:
      - facturadirecta3:docs/content/front/sales/create-estimate.md
  owner: dev
  last_review: '2026-05-14'
  publisher: scripts/docs/publish-help-center.ts
---
<h1 id="crear-un-presupuesto"><b>Crear un presupuesto</b></h1>
<p class="no-margin"></p>
<p class="no-margin">Un presupuesto es la <b>propuesta económica</b> que mandas a un cliente
antes de prestar el servicio o entregar la mercancía. Sirve como
oferta cerrada (cliente + concepto + importes) que el cliente acepta
o rechaza, y como base para convertirla luego en factura o albarán.</p>
<p class="no-margin"></p>
<p class="no-margin"><b>No tiene efectos fiscales</b>: no genera asiento contable, no se
envía a la AEAT (ni VeriFactu, ni TicketBAI), no entra en libros de
IVA. Por eso el formulario es bastante más simple que el de factura.</p>
<p class="no-margin"></p>
<h2 id="antes-de-empezar"><b>Antes de empezar</b></h2>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin">Necesitas al menos una <b>serie</b> para presupuestos. Si no la tienes
todavía, créala antes (ver <b>Crear una nueva serie de numeración</b>).</p></li>
<li><p class="no-margin">El <b>cliente</b> debe existir en Contactos (o lo creas sobre la
marcha desde el propio formulario).</p></li>
</ul>
<p class="no-margin"></p>
<h2 id="dnde-se-crea"><b>Dónde se crea</b></h2>
<p class="no-margin"></p>
<p class="no-margin">La forma habitual es desde el listado de <b>Presupuestos</b> (Ventas →
Presupuestos, ruta <code>/company/&lt;id&gt;/estimates</code>). En el listado pulsa el
botón de crear nuevo. También puedes llegar desde:</p>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin">El menú <b>Crear</b> del dashboard → <b>Presupuesto</b>.</p></li>
<li><p class="no-margin">La vista unificada <b>Todas las ventas</b>.</p></li>
</ul>
<p class="no-margin"></p>
<p class="no-margin">Para <b>editar</b> un presupuesto existente, haz clic sobre él en el
listado.</p>
<p class="no-margin"></p>
<h2 id="cmo-est-estructurado-el-formulario"><b>Cómo está estructurado el formulario</b></h2>
<p class="no-margin"></p>
<p class="no-margin">Al abrir o crear un presupuesto, FacturaDirecta despacha el diálogo
adecuado según el tipo de documento. Para presupuestos usa el mismo
formulario genérico que comparte con facturas y albaranes — lo que
cambia son <b>las pestañas que se muestran</b> (en presupuestos solo dos)
y la <b>ausencia de cualquier lógica fiscal</b>.</p>
<p class="no-margin"></p>
<h2 id="cabecera-del-documento"><b>Cabecera del documento</b></h2>
<p class="no-margin"></p>
<p class="no-margin">La cabecera del diálogo muestra:</p>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin">El <b>título y número</b> del documento (por ejemplo, <b>Presupuesto
2026-001</b>) — se asigna al guardar la primera vez según la serie
elegida.</p></li>
<li><p class="no-margin">Las <b>etiquetas (tags)</b> asociadas — visibles cuando el documento
ya está guardado.</p></li>
<li><p class="no-margin">Un botón para <b>expandir</b> el diálogo a pantalla completa.</p></li>
</ul>
<p class="no-margin"></p>
<h2 id="pestaas-del-formulario"><b>Pestañas del formulario</b></h2>
<p class="no-margin"></p>
<p class="no-margin">El diálogo de presupuesto es más simple que el de factura, porque no
tiene componente fiscal. Solo dos pestañas:</p>
<p class="no-margin"></p>
<div class="intercom-interblocks-table-container">
<table>
<thead>
<tr>
<th>Pestaña</th>
<th>Cuándo aparece</th>
<th>Qué cubre</th>
</tr>
</thead>
<tbody>
<tr>
<td>(Pestaña principal con el número)</td>
<td>Siempre</td>
<td>Datos generales, otros datos, líneas, totales.</td>
</tr>
<tr>
<td><b>Más información</b></td>
<td>Siempre</td>
<td>Comentarios internos, archivos adjuntos y registro de actividad.</td>
</tr>
</tbody>
</table>
</div>
<p class="no-margin"></p>
<p class="no-margin">No aparecen las pestañas fiscales (VeriFactu, TicketBAI, Facturae,
Vencimientos, Contabilidad, Impuestos): un presupuesto no genera
obligaciones fiscales.</p>
<p class="no-margin"></p>
<h2 id="pestaa-principal-cuerpo-del-documento"><b>Pestaña principal: cuerpo del documento</b></h2>
<p class="no-margin"></p>
<p class="no-margin">Es la pestaña que ves al abrir el diálogo. Se compone de:</p>
<p class="no-margin"></p>
<ol>
<li><p class="no-margin"><b>Datos generales</b> — cliente, serie, número, fecha, validez.</p></li>
<li><p class="no-margin"><b>Otros datos del documento</b> — operación, moneda, plantilla,
bandera proforma.</p></li>
<li><p class="no-margin"><b>Líneas</b> — los conceptos del presupuesto.</p></li>
<li><p class="no-margin"><b>Totales</b> — base, IVA por tipo, total final (informativo, no se
contabiliza).</p></li>
</ol>
<p class="no-margin"></p>
<h3 id="datos-generales"><b>Datos generales</b></h3>
<p class="no-margin"></p>
<p class="no-margin">En la zona superior del cuerpo:</p>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin"><b>Cliente</b> — selector con búsqueda. Si no existe, lo creas en
línea desde el mismo selector.</p></li>
<li><p class="no-margin"><b>Serie</b> — la serie de numeración para presupuestos.</p></li>
<li><p class="no-margin"><b>Número</b> — se asigna al guardar.</p></li>
<li><p class="no-margin"><b>Fecha</b> — fecha de emisión del presupuesto. Por defecto hoy.</p></li>
<li><p class="no-margin"><b>Validez / Caducidad</b> (opcional) — fecha hasta la que el cliente
puede aceptar el presupuesto a los precios indicados.</p></li>
</ul>
<p class="no-margin"></p>
<h3 id="otros-datos-del-documento-toolbar-resumida"><b>Otros datos del documento (toolbar resumida)</b></h3>
<p class="no-margin"></p>
<p class="no-margin">Inmediatamente debajo de los datos generales hay una <b>toolbar
horizontal</b> con un resumen y un botón <b>Cambiar</b> al final para
editarlos en bloque.</p>
<p class="no-margin"></p>
<p class="no-margin">Los campos que se muestran en esta toolbar para un presupuesto:</p>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin"><b>Operación</b> — la posición fiscal de la operación. Aunque el
presupuesto no genere asiento, la operación se conserva para
precomputar el IVA y para pasarla a la factura cuando se convierta.</p></li>
<li><p class="no-margin"><b>Moneda</b> — solo si tu empresa tiene la multidivisa activada.</p></li>
<li><p class="no-margin"><b>Tipo de cambio</b> — solo si la moneda del documento difiere de la
moneda de la empresa.</p></li>
<li><p class="no-margin"><b>Plantilla</b> — el nombre de la plantilla visual (tema) aplicada
al PDF del presupuesto.</p></li>
<li><p class="no-margin"><b>Factura Proforma</b> — etiqueta visible solo si has marcado el
presupuesto como <b>proforma</b>. Cambia el aspecto del PDF para que
parezca una factura sin serlo (útil para aduanas y trámites).</p></li>
</ul>
<p class="no-margin"></p>
<p class="no-margin">En vista compacta (móvil) los valores se concatenan en una sola línea
separados por comas en el orden: Operación, Moneda, Proforma (si
aplica).</p>
<p class="no-margin"></p>
<h3 id="cambiar-otros-datos-dilogo-de-configuracin-del-header"><b>Cambiar otros datos: diálogo de configuración del header</b></h3>
<p class="no-margin"></p>
<p class="no-margin">Cuando pulsas <b>Cambiar</b> en la toolbar de otros datos, se abre un
diálogo que te permite editar todos los anteriores en bloque:</p>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin"><b>Operación</b> (posición fiscal): selector con las opciones
aplicables a presupuestos.</p></li>
<li><p class="no-margin"><b>Moneda</b> y <b>Tipo de cambio</b> — activos si tu empresa tiene
multidivisa.</p></li>
<li><p class="no-margin"><b>Plantilla</b> — selector entre las plantillas visuales configuradas
en Ajustes.</p></li>
<li><p class="no-margin">Marcar como <b>Factura Proforma</b> — cambia la apariencia del PDF.</p></li>
</ul>
<p class="no-margin"></p>
<p class="no-margin">Los cambios se aplican al confirmar.</p>
<p class="no-margin"></p>
<h3 id="lneas"><b>Líneas</b></h3>
<p class="no-margin"></p>
<p class="no-margin">Bajo los datos generales y la toolbar viene el editor de líneas, con
la misma estructura que en facturas:</p>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin"><b>Producto</b> — selector con búsqueda. Si pones un nombre que no
existe, puedes crearlo al vuelo.</p></li>
<li><p class="no-margin"><b>Descripción</b> — texto libre que se imprime en el presupuesto.</p></li>
<li><p class="no-margin"><b>Cantidad</b> y <b>Precio unitario</b>.</p></li>
<li><p class="no-margin"><b>Descuento</b> — porcentaje o importe sobre la línea.</p></li>
<li><p class="no-margin"><b>Impuesto</b> — IVA aplicable (informativo: aunque no se contabiliza,
se muestra para que el cliente vea el importe final).</p></li>
</ul>
<p class="no-margin"></p>
<p class="no-margin">Acciones por línea: reordenar arrastrando, eliminar desde menú,
insertar una línea nueva al pie.</p>
<p class="no-margin"></p>
<h3 id="configurar-columnas-de-lneas-botn-engranaje"><b>Configurar columnas de líneas (botón engranaje)</b></h3>
<p class="no-margin"></p>
<p class="no-margin">Junto a la tabla de líneas hay un <b>icono de engranaje</b> que abre el
diálogo <b>Configurar columnas</b>. Las opciones son las mismas que en
factura — ver el patrón en <b>Crear una factura de venta</b> — con las
diferencias:</p>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin">La <b>Columna de contabilidad</b> no aplica al presupuesto (no hay
asiento). Probablemente no se muestre o no tenga efecto.</p></li>
<li><p class="no-margin">El resto (precios con IVA incluido, modo de cálculo de impuestos,
columnas de producto / cantidad-precio / descuento, decimales) se
comporta igual.</p></li>
</ul>
<p class="no-margin"></p>
<h3 id="totales"><b>Totales</b></h3>
<p class="no-margin"></p>
<p class="no-margin">Al pie del cuerpo del presupuesto se muestran los totales calculados
en tiempo real (base imponible, IVA por tipo, total final). En el
caso del presupuesto son <b>informativos</b>: no entran en libros ni
generan asiento. Sirven para que el cliente vea el importe que pagaría
si acepta.</p>
<p class="no-margin"></p>
<h2 id="pestaa-ms-informacin"><b>Pestaña Más información</b></h2>
<p class="no-margin"></p>
<p class="no-margin">Etiqueta literal: <b>Más información</b>. Agrupa tres sub-bloques:</p>
<p class="no-margin"></p>
<h3 id="comentarios"><b>Comentarios</b></h3>
<p class="no-margin"></p>
<p class="no-margin">Notas internas que tu equipo deja sobre el presupuesto. No se
imprimen en el PDF ni se envían al cliente. Útil para anotar el
contexto comercial (&quot;cliente quiere descuento si firma este mes&quot;,
&quot;pendiente confirmar plazo de entrega&quot;, etc.).</p>
<p class="no-margin"></p>
<h3 id="adjuntos"><b>Adjuntos</b></h3>
<p class="no-margin"></p>
<p class="no-margin">Archivos asociados al documento. En presupuestos suele ser muy
relevante: planos, fichas técnicas, documentación de proyecto,
términos legales. Los adjuntos pueden enviarse con el email al
cliente.</p>
<p class="no-margin"></p>
<h3 id="actividad"><b>Actividad</b></h3>
<p class="no-margin"></p>
<p class="no-margin">Historial de cambios sobre el documento (quién y cuándo modificó
qué). Útil para auditoría interna.</p>
<p class="no-margin"></p>
<h2 id="crear-el-presupuesto-paso-a-paso"><b>Crear el presupuesto paso a paso</b></h2>
<p class="no-margin"></p>
<ol>
<li><p class="no-margin">Desde el listado de <b>Presupuestos</b> pulsa el botón para crear
uno nuevo.</p></li>
<li><p class="no-margin">En <b>datos generales</b>, elige <b>Cliente</b>, <b>Serie</b> y revisa la
<b>Fecha</b> (y la validez si la usas).</p></li>
<li><p class="no-margin">En <b>otros datos</b> (toolbar resumida) pulsa <b>Cambiar</b> si
necesitas ajustar posición fiscal, moneda, plantilla o marcarlo
como <b>proforma</b>.</p></li>
<li><p class="no-margin">Añade <b>líneas</b>: producto, descripción, cantidad, precio,
impuesto, descuento. Los totales se actualizan al instante.</p></li>
<li><p class="no-margin">Si necesitas columnas distintas (sin descuento, sin producto,
etc.) usa el <b>engranaje</b> sobre la tabla.</p></li>
<li><p class="no-margin">Pulsa Guardar. El número se asigna en ese momento. <b>No se genera
asiento ni envío fiscal</b>.</p></li>
</ol>
<p class="no-margin"></p>
<h2 id="acciones-tras-crear"><b>Acciones tras crear</b></h2>
<p class="no-margin"></p>
<p class="no-margin">Desde el detalle del presupuesto puedes:</p>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin"><b>Enviar por email</b> al cliente con el PDF.</p></li>
<li><p class="no-margin"><b>Compartir</b> un enlace de descarga.</p></li>
<li><p class="no-margin"><b>Descargar el PDF</b>.</p></li>
<li><p class="no-margin"><b>Convertir en factura</b> — cuando el cliente acepta, se crea una
factura a partir del presupuesto preservando líneas, importes y
cliente. El presupuesto queda enlazado a la factura resultante.</p></li>
<li><p class="no-margin"><b>Convertir en albarán</b> — si vas a entregar antes de facturar.</p></li>
<li><p class="no-margin"><b>Cancelar</b> — si finalmente no se ejecuta. Queda marcado pero
no se borra (mantiene el número para trazabilidad).</p></li>
</ul>
<p class="no-margin"></p>
<h2 id="estados-de-un-presupuesto"><b>Estados de un presupuesto</b></h2>
<p class="no-margin"></p>
<p class="no-margin">Los estados visibles en el listado:</p>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin"><b>Borrador</b> — todavía no enviado al cliente.</p></li>
<li><p class="no-margin"><b>Enviado</b> — ya se envió por email o se compartió.</p></li>
<li><p class="no-margin"><b>Aceptado</b> — el cliente lo aprobó.</p></li>
<li><p class="no-margin"><b>Rechazado</b> — el cliente lo rechazó.</p></li>
<li><p class="no-margin"><b>Convertido</b> — ya generó una factura o un albarán a partir de él.</p></li>
<li><p class="no-margin"><b>Cancelado</b> — descartado sin convertir.</p></li>
</ul>
<p class="no-margin"></p>
<h2 id="recursos-relacionados"><b>Recursos relacionados</b></h2>
<p class="no-margin"></p>
<ul>
<li><p class="no-margin"><b>Crear una factura de venta</b> — el paso natural cuando el
presupuesto se acepta.</p></li>
<li><p class="no-margin"><b>Crear un albarán</b> — alternativa antes de facturar.</p></li>
<li><p class="no-margin"><b>Crear o editar un contacto</b> — gestión de los clientes.</p></li>
<li><p class="no-margin"><b>API: Presupuestos</b> — referencia técnica para integraciones.</p></li>
</ul>
