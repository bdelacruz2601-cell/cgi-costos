\# CGI — Costos y Gestión Integral

\## Arquitectura del Sistema



\*\*Versión:\*\* 1.0  

\*\*Estado:\*\* En desarrollo  

\*\*Arquitectura:\*\* Aplicación cliente-servidor modular



\---



\# 1. Objetivo de la arquitectura



CGI utilizará una arquitectura modular que permita separar la interfaz,

la lógica del negocio, los cálculos contables y el almacenamiento de datos.



El objetivo es facilitar el mantenimiento, las pruebas y la incorporación

de nuevos contenidos de Contabilidad II sin reconstruir el sistema completo.



\---



\# 2. Arquitectura general



CGI estará compuesto por dos partes principales:



\## Aplicación cliente



Desarrollada utilizando:



\- C++

\- Qt

\- Qt Quick

\- QML

\- CMake



Será ejecutada principalmente en dispositivos Android.



\## Backend



Supabase proporcionará:



\- Base de datos PostgreSQL.

\- Autenticación.

\- Seguridad de acceso a datos.

\- Comunicación con la aplicación.

\- Actualizaciones en tiempo real cuando corresponda.



La comunicación entre la aplicación y el backend utilizará HTTPS.



\---



\# 3. Capas de la aplicación



\## 3.1 Presentación — QML



Responsable de la interfaz gráfica.



Funciones:



\- Mostrar pantallas.

\- Mostrar formularios.

\- Recibir datos del usuario.

\- Mostrar pedidos.

\- Mostrar productos.

\- Mostrar indicadores.

\- Mostrar reportes.

\- Adaptar la interfaz según el rol.



QML no será responsable de realizar la lógica contable principal.



\---



\## 3.2 Controladores — C++



Los controladores comunicarán la interfaz QML con la lógica del sistema.



Ejemplos:



\- AuthController

\- PedidoController

\- ProductoController

\- InventarioController

\- CostoController

\- ReporteController



Los controladores recibirán solicitudes desde la interfaz y coordinarán

las operaciones necesarias.



\---



\## 3.3 Modelos — C++



Representarán las entidades utilizadas por CGI.



Modelos iniciales previstos:



\- Usuario

\- Rol

\- Producto

\- Ingrediente

\- Receta

\- Pedido

\- DetallePedido

\- Inventario

\- MovimientoInventario

\- RegistroContable

\- ManoObra

\- Auditoria



Los modelos podrán ampliarse conforme evolucione el proyecto.



\---



\## 3.4 Núcleo contable — C++



Contendrá las reglas y cálculos relacionados con Contabilidad II.



Inicialmente incluirá:



\- Clasificación de registros.

\- Materia Prima Directa.

\- Mano de Obra Directa.

\- Costos Indirectos de Fabricación.

\- Costo Primo.

\- Costo de Conversión.

\- Costo Total de Producción.

\- Costo Unitario.

\- Control de mano de obra.



Esta capa será independiente de la interfaz visual.



\---



\## 3.5 Servicios — C++



Los servicios manejarán la comunicación con recursos externos.



Servicios previstos:



\- SupabaseService

\- AuthService

\- DatabaseService

\- RealtimeService



La interfaz QML no se comunicará directamente con Supabase.



\---



\# 4. Flujo de información



Ejemplo de registro de un pedido:



Usuario

&#x20;  ↓

Pantalla QML

&#x20;  ↓

PedidoController

&#x20;  ↓

Validación C++

&#x20;  ↓

SupabaseService

&#x20;  ↓

Supabase / PostgreSQL

&#x20;  ↓

Actualización del sistema

&#x20;  ↓

Usuarios autorizados



\---



\# 5. Arquitectura de roles



CGI utilizará control de acceso basado en roles.



Roles iniciales:



\## Venta / Reparto



Acceso operativo limitado.



\## Software / Pedidos



Acceso al registro y seguimiento de pedidos y ventas.



\## Gerente



Acceso administrativo y de supervisión.



La seguridad se aplicará tanto en la interfaz como en el backend.



Ocultar opciones de la interfaz no será considerado suficiente para

proteger información restringida.



\---



\# 6. Arquitectura de datos



Supabase/PostgreSQL funcionará como fuente central de información.



Los dispositivos no mantendrán versiones independientes de los datos

principales del negocio.



Esto permitirá que varios usuarios trabajen sobre la misma información.



\---



\# 7. Datos configurables



Los datos variables de la actividad comercial no estarán escritos

directamente en el código.



Entre ellos:



\- Productos.

\- Precios.

\- Ingredientes.

\- Recetas.

\- Cantidades.

\- Unidades de medida.

\- Costos.

\- Gastos.

\- Personal.

\- Valores de mano de obra.



Estos datos serán administrados desde el sistema según los permisos

del usuario.



\---



\# 8. Tiempo real



Los cambios que requieran sincronización podrán propagarse a los

dispositivos autorizados.



Ejemplo:



Encargado registra pedido

&#x20;       ↓

Servidor recibe pedido

&#x20;       ↓

Base de datos lo almacena

&#x20;       ↓

Sistema notifica actualización

&#x20;       ↓

Venta/Reparto recibe pedido

&#x20;       ↓

Gerente puede supervisarlo



\---



\# 9. Seguridad



La arquitectura deberá contemplar:



\- Autenticación.

\- Autorización.

\- Roles.

\- Permisos.

\- Validación de datos.

\- Protección de credenciales.

\- Comunicación HTTPS.

\- Políticas de acceso a datos.

\- Auditoría.



Las credenciales o claves privadas no deberán almacenarse directamente

en el repositorio Git.



\---



\# 10. Organización del código



La estructura prevista será:



CGI/

|

|-- src/

|   |-- core/

|   |-- models/

|   |-- controllers/

|   `-- services/

|

|-- qml/

|   |-- pages/

|   |-- components/

|   `-- themes/

|

|-- assets/

|   |-- icons/

|   `-- images/

|

|-- tests/

|-- docs/

|

|-- main.cpp

|-- Main.qml

|-- CMakeLists.txt

`-- .gitignore



\---



\# 11. Principio de extensibilidad



Los módulos deberán tener responsabilidades separadas.



Cuando se incorpore un nuevo tema de Contabilidad II, se analizará si

requiere:



\- Una nueva entidad.

\- Un nuevo cálculo.

\- Una nueva pantalla.

\- Una modificación de base de datos.

\- Un nuevo reporte.



El objetivo será incorporar el nuevo requisito sin modificar

innecesariamente módulos que ya funcionan.



\---



\# 12. Estrategia de pruebas



CGI será probado progresivamente.



Se realizarán pruebas sobre:



\- Cálculos contables.

\- Validaciones.

\- Inicio de sesión.

\- Roles y permisos.

\- Pedidos.

\- Inventario.

\- Comunicación con el backend.

\- Sincronización.

\- Interfaz.

\- Ejecución en Android.



Cada módulo importante deberá probarse antes de integrarse con el siguiente.



\---



\# 13. Plataformas



Plataforma principal:



Android



Plataforma secundaria de desarrollo y pruebas:



Windows



La aplicación utilizará Qt para mantener una base de código común cuando

sea posible.



\---



\# 14. Control de versiones



El proyecto utilizará Git y GitHub.



Los cambios importantes se registrarán mediante commits descriptivos.



Los archivos generados durante la compilación y archivos que contengan

información sensible no deberán almacenarse en el repositorio.



\---



\# 15. Evolución



Esta arquitectura corresponde a la versión inicial de CGI.



Podrá evolucionar conforme:



\- Se definan los datos finales de la venta.

\- Se incorporen nuevos temas de Contabilidad II.

\- Se realicen pruebas.

\- Se detecten nuevos requisitos.

\- Se reciban modificaciones solicitadas por la docente.

