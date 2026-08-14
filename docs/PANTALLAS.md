\# CGI — Costos y Gestión Integral

\## Diseño de Pantallas y Permisos



\*\*Versión:\*\* 1.0

\*\*Plataforma principal:\*\* Android

\*\*Interfaz:\*\* Qt Quick / QML



\---



\# 1. Flujo general



INICIO

&#x20; ↓

LOGIN

&#x20; ↓

AUTENTICACIÓN

&#x20; ↓

IDENTIFICAR ROL

&#x20; ↓

CARGAR INTERFAZ AUTORIZADA



Cada usuario verá únicamente las funciones correspondientes

a sus permisos.



\---



\# 2. Login



Elementos:



\- Logo CGI

\- Nombre del sistema

\- Correo o usuario

\- Contraseña

\- Botón "Iniciar sesión"

\- Indicador de carga

\- Mensajes de error



El sistema identificará automáticamente el rol después

de iniciar sesión.



\---



\# 3. Rol Software / Pedidos



\## Pantalla principal



Diseñada para registrar pedidos rápidamente durante la venta.



Mostrará:



\- Pedidos activos

\- Pedidos pendientes

\- Pedidos completados

\- Acceso a nuevo pedido

\- Estado de conexión

\- Usuario activo



\## Nuevo pedido



Flujo:



Seleccionar producto

&#x20;     ↓

Cantidad

&#x20;     ↓

Agregar al pedido

&#x20;     ↓

Revisar pedido

&#x20;     ↓

Mostrar total

&#x20;     ↓

Confirmar



El pedido deberá enviarse inmediatamente al sistema central.



\## Seguimiento



Permitirá visualizar:



\- Número de pedido

\- Productos

\- Cantidades

\- Total

\- Hora

\- Estado

\- Responsable



\---



\# 4. Rol Venta / Reparto



Tendrá una interfaz más sencilla.



\## Pantalla principal



Mostrará principalmente:



\- Pedidos pendientes

\- Pedidos asignados

\- Estado del pedido

\- Información necesaria para atenderlo



No mostrará:



\- Costos internos

\- Ganancias

\- Configuración

\- Usuarios

\- Reportes administrativos

\- Información contable restringida



\## Flujo



NUEVO PEDIDO

&#x20;    ↓

PENDIENTE

&#x20;    ↓

EN PREPARACIÓN

&#x20;    ↓

LISTO

&#x20;    ↓

EN ENTREGA

&#x20;    ↓

ENTREGADO



Solo podrán realizarse cambios de estado autorizados.



\---



\# 5. Rol Gerente



Tendrá acceso a la administración y supervisión general.



\## Dashboard



Mostrará indicadores como:



\- Ventas acumuladas

\- Pedidos realizados

\- Productos vendidos

\- Pedidos pendientes

\- Costos

\- Gastos

\- Pérdidas

\- Costo de producción

\- Resultado de la actividad



Los indicadores se actualizarán con los datos disponibles.



\---



\# 6. Productos



Permitirá:



\- Ver productos

\- Crear producto

\- Editar producto

\- Cambiar precio

\- Activar producto

\- Desactivar producto

\- Configurar receta



\---



\# 7. Ingredientes e inventario



Permitirá:



\- Consultar ingredientes

\- Registrar ingredientes

\- Registrar compras

\- Consultar existencias

\- Registrar ajustes

\- Registrar mermas

\- Consultar movimientos



\---



\# 8. Costos y registros contables



Formulario de registro:



Concepto

Monto

Tipo de registro

Comportamiento

Identificación

Elemento del costo

Fecha

Observación



Clasificaciones disponibles inicialmente:



Tipo:

\- Costo

\- Gasto

\- Pérdida



Comportamiento:

\- Fijo

\- Variable

\- Semivariable



Identificación:

\- Directo

\- Indirecto



Elemento:

\- MPD

\- MOD

\- CIF

\- No aplica



El sistema podrá ocultar campos que no correspondan según

el tipo de registro seleccionado.



\---



\# 9. Mano de obra



Permitirá registrar y consultar:



\- Trabajador

\- Tipo de mano de obra

\- Valor o salario

\- Horas trabajadas

\- Horas hombre

\- Horas fábrica

\- Horas máquina cuando corresponda



También mostrará los cálculos disponibles relacionados con

mano de obra.



\---



\# 10. Resultados contables



Pantalla destinada al análisis.



Mostrará inicialmente:



\- MPD

\- MOD

\- CIF

\- Costo Primo

\- Costo de Conversión

\- Costo Total de Producción

\- Costo Unitario

\- Ingresos

\- Gastos

\- Pérdidas

\- Resultado de la actividad



\---



\# 11. Reportes



Permitirá consultar información agrupada como:



\- Ventas

\- Pedidos

\- Productos vendidos

\- Costos

\- Gastos

\- Pérdidas

\- Inventario

\- Mano de obra



Los nuevos reportes serán incorporados conforme evolucione CGI.



\---



\# 12. Administración de usuarios



Disponible para el gerente.



Permitirá:



\- Consultar usuarios

\- Crear o habilitar usuarios según el mecanismo definido

\- Asignar roles

\- Activar/desactivar acceso

\- Consultar estado



\---



\# 13. Auditoría



Permitirá consultar operaciones importantes.



Información:



\- Usuario

\- Acción

\- Fecha

\- Hora

\- Registro afectado



\---



\# 14. Configuración



Permitirá administrar parámetros autorizados del negocio.



Los datos finales de la venta podrán modificarse desde CGI

sin modificar el código fuente.



\---



\# 15. Navegación por rol



SOFTWARE / PEDIDOS



Inicio

├── Nuevo pedido

├── Pedidos

└── Perfil





VENTA / REPARTO



Inicio

├── Pedidos

├── Pedidos asignados

└── Perfil





GERENTE



Dashboard

├── Pedidos

├── Productos

├── Inventario

├── Compras

├── Costos

├── Mano de obra

├── Resultados

├── Reportes

├── Usuarios

├── Auditoría

└── Configuración



\---



\# 16. Diseño visual



La interfaz deberá ser:



\- Moderna

\- Limpia

\- Rápida

\- Fácil de comprender

\- Adaptada a teléfonos

\- Consistente entre pantallas



Se utilizarán componentes reutilizables para evitar repetir

el mismo diseño en múltiples pantallas.



Los estados importantes deberán distinguirse visualmente.



\---



\# 17. Principio de seguridad visual



La interfaz se adaptará al rol.



Ejemplo:



Un usuario Venta/Reparto no deberá simplemente recibir un

mensaje de "Acceso denegado" al intentar abrir Costos.



La opción Costos ni siquiera deberá formar parte de su

navegación normal.



Esto será complementado con seguridad real en el backend.

