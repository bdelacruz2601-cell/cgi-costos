\# CGI — Costos y Gestión Integral

\## Especificación de Requisitos



\*\*Proyecto:\*\* CGI — Costos y Gestión Integral  

\*\*Asignatura:\*\* Contabilidad II  

\*\*Tipo:\*\* Aplicación móvil multiusuario para gestión de ventas y costos  

\*\*Tecnologías:\*\* C++, Qt, QML, CMake, PostgreSQL/Supabase  

\*\*Estado:\*\* En desarrollo  



\---



\# 1. Propósito



CGI es un sistema diseñado para automatizar el registro, clasificación,

cálculo y análisis de la información generada durante una actividad comercial.



La primera implementación será utilizada en una venta de tacos, pero el

sistema será configurable para permitir modificar productos, precios,

ingredientes, costos, gastos y demás información sin modificar el código.



El sistema permitirá obtener información financiera y no financiera para

apoyar el control y la toma de decisiones.



\---



\# 2. Objetivos



\## Objetivo general



Desarrollar una aplicación móvil multiusuario que permita registrar las

operaciones de una venta y automatizar el control y análisis de sus costos.



\## Objetivos específicos



\- Registrar pedidos y ventas.

\- Administrar productos y precios.

\- Controlar ingredientes e inventario.

\- Registrar costos, gastos y pérdidas.

\- Clasificar los costos.

\- Determinar los elementos del costo de producción.

\- Calcular automáticamente resultados contables.

\- Controlar la mano de obra.

\- Mostrar información actualizada de la operación.

\- Generar reportes para la toma de decisiones.

\- Mantener un historial de las operaciones realizadas.

\- Restringir funciones según el rol del usuario.



\---



\# 3. Usuarios y roles



CGI tendrá inicialmente cinco usuarios distribuidos en tres niveles de acceso.



\## 3.1 Venta / Reparto



Cantidad inicial: 2 usuarios.



Funciones:

\- Visualizar pedidos asignados.

\- Consultar información necesaria para realizar la entrega.

\- Cambiar el estado de un pedido según los permisos otorgados.

\- Consultar únicamente las funciones necesarias para su trabajo.



No tendrá acceso a configuraciones, costos internos ni información

administrativa restringida.



\## 3.2 Encargado de Software / Pedidos



Cantidad inicial: 2 usuarios.



Funciones:

\- Registrar pedidos.

\- Consultar pedidos activos.

\- Registrar ventas.

\- Consultar productos.

\- Consultar información operativa permitida.

\- Dar seguimiento al flujo de los pedidos.



\## 3.3 Gerente



Cantidad inicial: 1 usuario.



Tendrá el nivel de acceso más alto.



Funciones:

\- Supervisar la operación completa.

\- Administrar usuarios.

\- Administrar productos.

\- Administrar ingredientes.

\- Administrar inventario.

\- Registrar y administrar costos.

\- Registrar gastos y pérdidas.

\- Consultar ventas.

\- Consultar cálculos contables.

\- Consultar reportes.

\- Modificar configuraciones permitidas.

\- Consultar el historial y auditoría del sistema.



\---



\# 4. Gestión de productos



El sistema permitirá:



\- Crear productos.

\- Editar productos.

\- Activar o desactivar productos.

\- Modificar precios.

\- Asociar ingredientes a cada producto.

\- Definir cantidades utilizadas de cada ingrediente.

\- Registrar diferentes unidades de medida.



Los productos de la venta actual no estarán escritos directamente en el

código fuente.



\---



\# 5. Pedidos



Cada pedido deberá almacenar como mínimo:



\- Identificador.

\- Fecha y hora.

\- Usuario que registró el pedido.

\- Productos.

\- Cantidades.

\- Precio correspondiente.

\- Total.

\- Estado del pedido.

\- Usuario responsable cuando corresponda.



Estados iniciales:



\- Pendiente.

\- En preparación.

\- Listo.

\- En entrega.

\- Entregado.

\- Cancelado.



Los cambios deberán reflejarse entre los usuarios del sistema.



\---



\# 6. Inventario



CGI permitirá registrar:



\- Ingredientes.

\- Unidad de medida.

\- Cantidad disponible.

\- Costo de adquisición.

\- Entradas.

\- Salidas.

\- Ajustes.

\- Mermas cuando corresponda.



El consumo de ingredientes podrá relacionarse con los productos vendidos.



\---



\# 7. Clasificación contable



CGI distinguirá inicialmente entre:



\- Costo.

\- Gasto.

\- Pérdida.



Los costos podrán analizarse además mediante dos clasificaciones

independientes.



\## Según comportamiento



\- Fijo.

\- Variable.

\- Semivariable.



\## Según identificación con el producto



\- Directo.

\- Indirecto.



Por lo tanto, un costo podrá almacenar simultáneamente su comportamiento y

su identificación.



\---



\# 8. Elementos del costo de producción



CGI manejará:



\## MPD — Materia Prima Directa



Materiales que pueden identificarse y cuantificarse en el producto.



\## MOD — Mano de Obra Directa



Trabajo directamente relacionado con la transformación del producto.



\## CIF — Costos Indirectos de Fabricación



Recursos necesarios para producir que no se identifican directamente con

una unidad específica.



El sistema deberá permitir registrar criterios de asignación cuando sean

necesarios para distribuir costos indirectos.



\---



\# 9. Cálculos automáticos iniciales



CGI calculará:



Costo Primo = MPD + MOD



Costo de Conversión = MOD + CIF



Costo Total de Producción = MPD + MOD + CIF



Costo Unitario = Costo Total de Producción / Unidades producidas



Los resultados se recalcularán cuando cambien los datos relacionados.



\---



\# 10. Mano de obra



El sistema contemplará:



\- Mano de obra directa.

\- Mano de obra indirecta.

\- Trabajadores.

\- Salarios o valores de mano de obra.

\- Horas trabajadas.

\- Horas hombre.

\- Horas fábrica.

\- Horas máquina cuando corresponda.

\- Costo o cuota de mano de obra.

\- Tiempo empleado en producción.



\---



\# 11. Otros costos y gastos



El sistema permitirá registrar conceptos adicionales como:



\- Gasolina.

\- Transporte.

\- Energía.

\- Servicios.

\- Empaque.

\- Compras.

\- Otros costos.

\- Otros gastos.



Cada registro deberá poder clasificarse según corresponda.



\---



\# 12. Resultados de la actividad



El sistema deberá mostrar como mínimo:



\- Ingresos por ventas.

\- Cantidad de productos vendidos.

\- Costos registrados.

\- Gastos registrados.

\- Pérdidas registradas.

\- Costo de producción.

\- Costo unitario.

\- Resultado económico de la actividad.



Los indicadores adicionales se incorporarán conforme avance el contenido

de Contabilidad II.



\---



\# 13. Tiempo real



Los usuarios podrán trabajar simultáneamente.



Ejemplo:



1\. Un encargado registra un pedido.

2\. El pedido se almacena en el sistema central.

3\. Los usuarios autorizados reciben la actualización.

4\. El pedido cambia de estado durante el proceso.

5\. El gerente puede supervisar la operación.



\---



\# 14. Seguridad y permisos



El sistema deberá:



\- Requerir autenticación.

\- Identificar al usuario.

\- Asociar cada usuario con un rol.

\- Restringir funciones según permisos.

\- Evitar que la interfaz muestre funciones no autorizadas.

\- Proteger también los datos en el backend.

\- Registrar operaciones importantes realizadas por los usuarios.



Ocultar un botón no será considerado un mecanismo suficiente de seguridad.



\---



\# 15. Auditoría



Las operaciones relevantes deberán poder registrar:



\- Usuario.

\- Acción.

\- Fecha.

\- Hora.

\- Registro afectado.

\- Información necesaria para identificar el cambio.



\---



\# 16. Configuración



Los datos variables del negocio deberán poder modificarse sin recompilar

la aplicación.



Entre ellos:



\- Productos.

\- Precios.

\- Ingredientes.

\- Recetas.

\- Costos.

\- Gastos.

\- Personal.

\- Valores de mano de obra.

\- Unidades de medida.

\- Otros parámetros permitidos.



\---



\# 17. Extensibilidad



CGI será desarrollado mediante módulos.



Los nuevos contenidos vistos durante el curso podrán incorporarse sin

reescribir los módulos existentes.



Ejemplos de futuras ampliaciones:



\- Nuevos cálculos contables.

\- Nuevas clasificaciones.

\- Nuevos reportes.

\- Nuevos indicadores.

\- Nuevos tipos de operación.



Las fórmulas contables fundamentales no podrán modificarse libremente por

usuarios comunes.



\---



\# 18. Requisitos técnicos



\- Lenguaje principal: C++.

\- Interfaz: Qt Quick / QML.

\- Compilación: CMake.

\- Plataforma principal: Android.

\- Plataforma de desarrollo y pruebas: Windows.

\- Base de datos centralizada: PostgreSQL mediante Supabase.

\- Control de versiones: Git.

\- Repositorio remoto: GitHub.

\- Comunicación segura mediante HTTPS.

\- Arquitectura preparada para múltiples usuarios.



\---



\# 19. Requisitos de calidad



CGI deberá buscar:



\- Exactitud en los cálculos.

\- Validación de datos.

\- Seguridad.

\- Facilidad de uso.

\- Interfaz visual clara.

\- Código organizado.

\- Mantenibilidad.

\- Trazabilidad de operaciones.

\- Consistencia de información.

\- Capacidad de ampliación.



\---



\# 20. Estado del documento



Versión: 1.0



Este documento evolucionará conforme se incorporen nuevos contenidos de

Contabilidad II y se definan los datos finales de la actividad comercial.

