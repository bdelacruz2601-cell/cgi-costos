\# CGI — Costos y Gestión Integral

\## Diseño de Base de Datos



\*\*Versión:\*\* 1.0

\*\*Motor:\*\* PostgreSQL

\*\*Backend:\*\* Supabase

\*\*Estado:\*\* Diseño inicial



\---



\# 1. Objetivo



La base de datos almacenará de forma centralizada la información de CGI.



Los datos variables de la venta serán configurables y no dependerán

directamente del código de la aplicación.



\---



\# 2. Usuarios y roles



\## roles



\- id

\- nombre

\- descripcion

\- nivel\_acceso

\- activo



Roles iniciales:

\- venta\_reparto

\- software\_pedidos

\- gerente



\## perfiles



\- id

\- usuario\_auth\_id

\- nombre

\- rol\_id

\- activo

\- creado\_en

\- actualizado\_en



Las credenciales de acceso serán administradas mediante el sistema

de autenticación y no se guardarán como contraseñas de texto en perfiles.



\---



\# 3. Productos



\## productos



\- id

\- nombre

\- descripcion

\- precio\_venta

\- activo

\- creado\_en

\- actualizado\_en



Los productos podrán agregarse o modificarse sin cambiar el código.



\---



\# 4. Ingredientes



\## ingredientes



\- id

\- nombre

\- unidad\_medida\_id

\- activo

\- creado\_en

\- actualizado\_en



\## unidades\_medida



\- id

\- nombre

\- simbolo

\- activo



Ejemplos:

\- kilogramo / kg

\- gramo / g

\- litro / L

\- mililitro / mL

\- unidad / u



\---



\# 5. Recetas



\## recetas



\- id

\- producto\_id

\- ingrediente\_id

\- cantidad

\- activo



Una receta determina cuánto ingrediente requiere una unidad de producto.



\---



\# 6. Compras de ingredientes



\## compras



\- id

\- fecha

\- proveedor

\- total

\- usuario\_id

\- observacion

\- creado\_en



\## detalle\_compras



\- id

\- compra\_id

\- ingrediente\_id

\- cantidad

\- costo\_unitario

\- subtotal



Esto permitirá conservar el costo real de las compras realizadas.



\---



\# 7. Inventario



\## movimientos\_inventario



\- id

\- ingrediente\_id

\- tipo\_movimiento

\- cantidad

\- costo\_referencia

\- referencia\_tipo

\- referencia\_id

\- usuario\_id

\- fecha

\- observacion



Tipos iniciales:

\- entrada

\- consumo

\- ajuste\_positivo

\- ajuste\_negativo

\- merma



El inventario podrá calcularse a partir de sus movimientos.



\---



\# 8. Pedidos



\## pedidos



\- id

\- numero\_pedido

\- fecha\_hora

\- usuario\_registro\_id

\- usuario\_asignado\_id

\- estado

\- subtotal

\- total

\- observacion

\- creado\_en

\- actualizado\_en



Estados iniciales:

\- pendiente

\- en\_preparacion

\- listo

\- en\_entrega

\- entregado

\- cancelado



\---



\# 9. Detalle de pedidos



\## detalle\_pedidos



\- id

\- pedido\_id

\- producto\_id

\- cantidad

\- precio\_unitario

\- subtotal



El precio\_unitario se conservará en el detalle para mantener el valor

histórico de la venta aunque posteriormente cambie el precio del producto.



\---



\# 10. Registros contables



\## registros\_contables



\- id

\- concepto

\- descripcion

\- monto

\- tipo\_registro

\- comportamiento

\- identificacion

\- elemento\_costo

\- fecha

\- usuario\_id

\- observacion

\- creado\_en

\- actualizado\_en



tipo\_registro:

\- costo

\- gasto

\- perdida



comportamiento:

\- fijo

\- variable

\- semivariable



identificacion:

\- directo

\- indirecto



elemento\_costo:

\- MPD

\- MOD

\- CIF

\- no\_aplica



Las diferentes clasificaciones se almacenarán por separado.



\---



\# 11. Mano de obra



\## mano\_obra



\- id

\- nombre\_trabajador

\- tipo

\- salario\_o\_valor

\- horas\_trabajadas

\- horas\_hombre

\- horas\_fabrica

\- horas\_maquina

\- fecha

\- usuario\_id

\- observacion



tipo:

\- directa

\- indirecta



\---



\# 12. Auditoría



\## auditoria



\- id

\- usuario\_id

\- accion

\- tabla\_afectada

\- registro\_id

\- fecha\_hora

\- detalle



Permitirá identificar operaciones importantes realizadas en CGI.



\---



\# 13. Configuración



\## configuracion



\- id

\- clave

\- valor

\- descripcion

\- actualizado\_por

\- actualizado\_en



Solo almacenará parámetros que sea seguro y lógico modificar desde

la aplicación.



Las reglas contables fundamentales no deberán depender de valores

editables libremente.



\---



\# 14. Relaciones principales



roles

&#x20; |

&#x20; +--- perfiles



productos

&#x20; |

&#x20; +--- recetas --- ingredientes

&#x20; |                  |

&#x20; |                  +--- unidades\_medida

&#x20; |

&#x20; +--- detalle\_pedidos --- pedidos



ingredientes

&#x20; |

&#x20; +--- detalle\_compras --- compras

&#x20; |

&#x20; +--- movimientos\_inventario



perfiles

&#x20; |

&#x20; +--- pedidos

&#x20; +--- compras

&#x20; +--- registros\_contables

&#x20; +--- mano\_obra

&#x20; +--- auditoria



\---



\# 15. Principios de diseño



1\. Los productos no estarán escritos directamente en el código.

2\. Los precios podrán modificarse.

3\. Las recetas podrán modificarse.

4\. Los movimientos conservarán información histórica.

5\. Los registros contables admitirán varias clasificaciones simultáneas.

6\. Los permisos dependerán del usuario y su rol.

7\. Las operaciones importantes podrán auditarse.

8\. Los nuevos módulos podrán relacionarse con las tablas existentes.

9\. La eliminación de información histórica deberá evitarse cuando pueda

&#x20;  afectar cálculos o reportes.

10\. La seguridad también será aplicada desde la base de datos.



\---



\# 16. Evolución



Este modelo corresponde a la versión 1.0.



Podrán incorporarse nuevas tablas y relaciones cuando Contabilidad II

introduzca nuevos temas o cuando cambien los requisitos de la actividad.

