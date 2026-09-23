# Alejandro Gonzales Sarmiento

**Fullstack Laravel + Vue** · CTO en Dibal

Construyo sistemas de gestión con mucha regla de negocio y reportes que tienen
que cuadrar al céntimo. Trabajo en paralelo en dos frentes muy distintos: los
sistemas administrativos de la **Universidad Nacional Agraria La Molina** y la
plataforma de productos de **Dibal**, donde dirijo el desarrollo.

---

## Dibal · CTO

Dirijo la arquitectura y el desarrollo de una plataforma de productos de gestión
para pymes, construida sobre Laravel 12.

### Productos

**Gestión de restaurantes** — sistema principal de la empresa.
`Laravel 12` · `PHP 8.2` · `Tailwind 4` · `Vite` · `Vitest` · `MySQL`

**Gestión de cocheras y aparcamientos** — producto nuevo, en desarrollo.
`Laravel 12` · `PHP 8.2` · `Tailwind 4` · `Vite 7` · `MySQL`

### Microservicios compartidos

**Envío por WhatsApp** — entrega automatizada de documentos PDF a clientes
mediante la Cloud API oficial de WhatsApp.
`Laravel 12` · `WhatsApp Cloud API` · `MySQL`

**Facturación electrónica** — en construcción.
`Laravel 12` · `Tailwind 4` · `Vite 7` · `MariaDB`

### La decisión de arquitectura

El sistema de restaurantes nació como un monolito, con la facturación
electrónica escrita dentro del propio código. Funcionaba, pero cada producto
nuevo obligaba a reimplementar lo mismo.

Al arrancar el sistema de cocheras la pregunta se volvió inevitable: ¿duplicamos
la facturación, o la sacamos fuera? Optamos por extraerla como **microservicio
reutilizable**, igual que ya habíamos hecho con el envío por WhatsApp.

El objetivo es que cada producto nuevo —cocheras hoy, lo que venga después—
consuma facturación y mensajería como servicios, en vez de heredar una copia más
que mantener. Menos superficie duplicada y un solo lugar donde corregir cuando
cambian las reglas de SUNAT.

---

## UNALM · Desarrollo de sistemas administrativos

**SIMI · Gestión de bienes patrimoniales**
Registro, control y reportería de **~140 000 activos físicos** asignados a
responsables, locales, áreas y oficinas, con integración a los sistemas
**SIGA (MEF)** y **SINADMOL (SBN)**.
`Laravel 9` · `SQL Server` · `Bootstrap 5` · `Vite`

**SINADMOL / SIGA v2 · Integración y gestión interna**
Sistema multi-módulo: transferencias patrimoniales con montos independientes por
pata, cuadros de tiempos y saldos, y reportes de gastos desagregados por grupo
operacional con exportación a Excel y PDF.
`Laravel 11` · `PHP 8.2` · `Vue 3` · `Tailwind` · `ApexCharts` · `SQL Server`

**Intranet institucional**
Reportería mensual de ingresos y gastos con detalle navegable y exportaciones.
`Laravel 9` · `SQL Server` · `Vite`

### Laravel contra SQL Server

No es el camino cómodo. Casi todo el ecosistema de Laravel asume MySQL o
PostgreSQL, y la documentación se acaba rápido cuando el motor es SQL Server
—pero es lo que hay en el sector público peruano.

Lo resolví de punta a punta: imagen base con el driver **ODBC 18** y
`pdo_sqlsrv`, consultas y migraciones que respetan las particularidades de
T-SQL, y un entorno Docker reproducible para levantar cualquier proyecto con un
solo `make up`.

---

## Stack

| | |
|---|---|
| **Backend** | Laravel 9 → 12 · PHP 8.0–8.2 · SQL Server (`pdo_sqlsrv` + ODBC 18) · MySQL · MariaDB · Redis |
| **Frontend** | Vue 3 · Vite · Tailwind CSS 3–4 · Bootstrap 5 · ApexCharts · Vitest |
| **Integraciones** | WhatsApp Cloud API · Facturación electrónica · SIGA (MEF) · SINADMOL (SBN) |
| **Reportería** | Maatwebsite/Excel · DomPDF · Snappy |
| **Entorno** | Docker · Docker Compose · Traefik · AWS RDS · Makefile · WSL2 · Linux |

---

## Dos mundos a la vez

Mantener sistemas heredados y construir sobre lo actual usan músculos distintos.
En la universidad heredo código con años encima y un motor que el framework no
quiere; en Dibal decido la arquitectura desde cero. Me interesa no perder ninguno
de los dos.

---

## Contacto

[LinkedIn](https://pe.linkedin.com/in/alejandro-gonzales-sarmiento)
