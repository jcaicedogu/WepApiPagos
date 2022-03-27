# WepApiPagos
En una API Web que simula una operación de pago típica en una solución de comercio electrónico.
# Autor
Judy Ernestina Caicedo Gutierrez 
## Comenzando
 La APIWEB cuenta con dos servicios  llamados Pedido y Facturar.
 El servicio Pedido permitira crear un pedido.
 El servicio Facturar pertira facturar un pedido previamente creado.
 La api web cuenta con un ApiKey que permitira solo el acceso al servicio a quienes tenga esta llave.
### Como ejecutar el servicio Pedido
El servicio Pedido funciona como metodo Post(https://{url}/api/Pedido/Pedido)
Recibe como parametro una estructura tipo JSON que esta conformado por un encabezado y detalle del pedido de la siguiente forma:
{
   "pedidoenc": {
   "nombre":"judy Caicedo",
   "cedula":"12345678-9",
   "fecha":"2022-03-14"
   
 },
"detallePedidos":[
    {
       "item":185609,
       "cantidad":1,
       "precio_unit":12.99
     },
     {
       "item":185609,
       "cantidad":2,
       "precio_unit":12.99
     }
   ]

}
En el modo Authorizathion se debera indicar tipo ApiKey, en indicar  key:ApiKey  value:x-ekfepmbrt546215eed3g856jnhfpo
Si la creacion del pepido es exitosa, el servicio retornara el siguiente resultado:
{
    "numpedido": "14"
}

El servicio Factura funciona como metodo Post(https://{url}/api/Pedido/Facturar/?PedidoNum=14)
El servicio Facturar recibe como parametro el numero del pedido que se quiere facturar.
En el modo Authorizathion se debera indicar tipo ApiKey, en indicar  key:ApiKey  value:x-ekfepmbrt546215eed3g856jnhfpo.
Si el pedido fue facturado con exito el sistema dara como respuesta:
{
    "facturaNum": 4,
    "pedidoNum": 14,
    "total": 38.9700
}
si intentas facturar un pedido que no existe el servicio respondera:
{
    "isSuccess": false,
    "message": "Registro no encontrado",
    "result": "El Pedido Numero:12 No existe"
}
si intentas facturar un pedido que ya fue facturado el servicio respondera:
{
    "isSuccess": false,
    "message": "No se puede facturar.",
    "result": "El Pedido Numero:14 ya fue Facturada"
}
 
### Construido con 🛠️
 La Api web fue desarrollo en visual studio 2019, .net core 5.0.
 Base de datos sql server. 
### Ejecutando las pruebas ⚙️
Las pruebas fueron realizadas con el cliente Http PostMan

