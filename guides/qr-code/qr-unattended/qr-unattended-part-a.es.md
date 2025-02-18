---
sites_supported:
  - mla
  - mpe
  - mco
  - mlu
  - mlm
  - mlc
---

# Pagos QR modelo desatendido

## ¿Qué es QR por modelo desatendido?

Este modelo te **permite que no se tenga que crear explícitamente la orden de cobro en Mercado Pago**. La orden es generada con la selección de un producto o servicio y el escaneo del QR de la caja. 

Se recomienda para estaciones de servicios, máquinas expendedoras o para sistemas integrados con múltiples billeteras.

## Características del modelo 

Las características principales son: 

- Cada caja tiene una URL asociada a la que Mercado Pago consultará si hay una orden lista para pagar.
- Cuando el cliente escanea el QR de la caja, Mercado Pago realiza un request de manera recurrente a la URL asociada a la caja, y cuando la orden esté lista, mostrará el monto a pagar en la app al cliente.
- El cliente podrá pagar solamente si hay una orden creada para el QR que escaneó.

> NOTE
> 
> Nota
> 
> La URL deberá apuntar a un servicio de tu dominio donde expongas por cada caja de tu sucursal si hay un orden lista de ser paga o no.

## Flujo del modelo

Te explicamos cómo funciona el modelo desatendido: 

>![Flujo de pago en punto de venta QR Mercado Pago](/images/qr_flujo_desatendido.es.png)


1. El cliente escanea el código QR desde su aplicación.
2. En función de la URL asociada a la caja, Mercado Pago busca la orden en el servidor del vendedor.
3. (A) El punto de venta informa su estado al servidor del vendedor.<br/>
   (B) Si la información no está disponible, el servidor del vendedor responderá `HTTP 400`.<br/>
   (C) Mercado Pago muestra una pantalla de espera en la aplicación.<br/>
   (D) Y vuelve a busca la orden en el servidor del vendedor. 
4. (A) El punto de venta envía los datos de la orden al servidor del vendedor.<br/>
   (B) Al estar la orden disponible, el servidor del vendedor responde `HTTP 200` con la información de la orden a cobrar.
5. (A) Luego, muestra la pantalla de pago en la app del cliente.<br/>
   (B) El servidor del vendedor recibe una notificación de la orden.<br/>
   (C) Y confirma su recepción. 
6. Finalmente, el cliente paga la orden. 
7. (A) El cliente verá la confirmación del pago.<br/>
   (B) El servidor del vendedor recibe una notificación con la orden.<br/> 
   (C) Y confirma su recepción. 
8. (A) El servidor del vendedor consulta el estado de la orden con el ID recibido en la última notificación para saber si está cerrada o si sigue abierta, pendiente de pago.<br/>
   (B) Mercado Pago devuelve los datos correspondientes como su estado, información de pagos, entre otros.
9. Si la orden se encuentra cerrada (**closed**), se puede imprimir el comprobante para finalizar la transacción.

> NOTE
> 
> Nota
> 
> En el punto 5 deberás ejecutar los pasos 8A y 8B para obtener el estado de la orden.

### Próximos pasos

<div>
<a href="https://www.mercadopago.com.ar/developers/es/guides/qr-code/qr-unattended/qr-unattended-part-b/" style="text-decoration:none;color:inherit">       
<blockquote class="next-step-card next-step-card-left">
<p class="card-note-title">Cómo integrar QR modelo desatendido<span class="card-status-tag card-status-tag-required">REQUERIDO</span></p>
 <p>Conoce paso a paso como integrar este modelo.</p>
</blockquote>
</div>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
