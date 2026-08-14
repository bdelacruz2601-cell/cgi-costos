\# CGI — Costos y Gestión Integral

\## Modelo Entidad-Relación



\*\*Versión:\*\* 1.0

\*\*Base de datos:\*\* PostgreSQL / Supabase



\---



\# 1. Diagrama general



```mermaid

erDiagram



&#x20;   ROLES ||--o{ PERFILES : asigna



&#x20;   PERFILES ||--o{ PEDIDOS : registra

&#x20;   PERFILES ||--o{ COMPRAS : registra

&#x20;   PERFILES ||--o{ REGISTROS\_CONTABLES : registra

&#x20;   PERFILES ||--o{ MANO\_OBRA : registra

&#x20;   PERFILES ||--o{ AUDITORIA : genera



&#x20;   PRODUCTOS ||--o{ RECETAS : contiene

&#x20;   INGREDIENTES ||--o{ RECETAS : utiliza

&#x20;   UNIDADES\_MEDIDA ||--o{ INGREDIENTES : mide



&#x20;   PEDIDOS ||--|{ DETALLE\_PEDIDOS : contiene

&#x20;   PRODUCTOS ||--o{ DETALLE\_PEDIDOS : vendido\_en



&#x20;   COMPRAS ||--|{ DETALLE\_COMPRAS : contiene

&#x20;   INGREDIENTES ||--o{ DETALLE\_COMPRAS : comprado\_en



&#x20;   INGREDIENTES ||--o{ MOVIMIENTOS\_INVENTARIO : genera



&#x20;   ROLES {

&#x20;       uuid id PK

&#x20;       string nombre

&#x20;       string descripcion

&#x20;       int nivel\_acceso

&#x20;       boolean activo

&#x20;   }



&#x20;   PERFILES {

&#x20;       uuid id PK

&#x20;       uuid usuario\_auth\_id

&#x20;       uuid rol\_id FK

&#x20;       string nombre

&#x20;       boolean activo

&#x20;   }



&#x20;   PRODUCTOS {

&#x20;       uuid id PK

&#x20;       string nombre

&#x20;       string descripcion

&#x20;       decimal precio\_venta

&#x20;       boolean activo

&#x20;   }



&#x20;   UNIDADES\_MEDIDA {

&#x20;       uuid id PK

&#x20;       string nombre

&#x20;       string simbolo

&#x20;       boolean activo

&#x20;   }



&#x20;   INGREDIENTES {

&#x20;       uuid id PK

&#x20;       uuid unidad\_medida\_id FK

&#x20;       string nombre

&#x20;       boolean activo

&#x20;   }



&#x20;   RECETAS {

&#x20;       uuid id PK

&#x20;       uuid producto\_id FK

&#x20;       uuid ingrediente\_id FK

&#x20;       decimal cantidad

&#x20;       boolean activo

&#x20;   }



&#x20;   PEDIDOS {

&#x20;       uuid id PK

&#x20;       int numero\_pedido

&#x20;       uuid usuario\_registro\_id FK

&#x20;       uuid usuario\_asignado\_id

&#x20;       string estado

&#x20;       decimal subtotal

&#x20;       decimal total

&#x20;       datetime fecha\_hora

&#x20;   }



&#x20;   DETALLE\_PEDIDOS {

&#x20;       uuid id PK

&#x20;       uuid pedido\_id FK

&#x20;       uuid producto\_id FK

&#x20;       decimal cantidad

&#x20;       decimal precio\_unitario

&#x20;       decimal subtotal

&#x20;   }



&#x20;   COMPRAS {

&#x20;       uuid id PK

&#x20;       uuid usuario\_id FK

&#x20;       datetime fecha

&#x20;       string proveedor

&#x20;       decimal total

&#x20;   }



&#x20;   DETALLE\_COMPRAS {

&#x20;       uuid id PK

&#x20;       uuid compra\_id FK

&#x20;       uuid ingrediente\_id FK

&#x20;       decimal cantidad

&#x20;       decimal costo\_unitario

&#x20;       decimal subtotal

&#x20;   }



&#x20;   MOVIMIENTOS\_INVENTARIO {

&#x20;       uuid id PK

&#x20;       uuid ingrediente\_id FK

&#x20;       uuid usuario\_id FK

&#x20;       string tipo\_movimiento

&#x20;       decimal cantidad

&#x20;       decimal costo\_referencia

&#x20;       datetime fecha

&#x20;   }



&#x20;   REGISTROS\_CONTABLES {

&#x20;       uuid id PK

&#x20;       uuid usuario\_id FK

&#x20;       string concepto

&#x20;       decimal monto

&#x20;       string tipo\_registro

&#x20;       string comportamiento

&#x20;       string identificacion

&#x20;       string elemento\_costo

&#x20;       datetime fecha

&#x20;   }



&#x20;   MANO\_OBRA {

&#x20;       uuid id PK

&#x20;       uuid usuario\_id FK

&#x20;       string nombre\_trabajador

&#x20;       string tipo

&#x20;       decimal salario\_o\_valor

&#x20;       decimal horas\_trabajadas

&#x20;       decimal horas\_hombre

&#x20;       decimal horas\_fabrica

&#x20;       decimal horas\_maquina

&#x20;       datetime fecha

&#x20;   }



&#x20;   AUDITORIA {

&#x20;       uuid id PK

&#x20;       uuid usuario\_id FK

&#x20;       string accion

&#x20;       string tabla\_afectada

&#x20;       uuid registro\_id

&#x20;       datetime fecha\_hora

&#x20;   }

