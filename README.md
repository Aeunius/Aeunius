<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/banner-dark.svg">
  <img alt="Alejandro Gonzales Sarmiento — Fullstack Laravel + Vue — Socio fundador y CTO en Dibal" src="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/banner-light.svg">
</picture>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/stack-dark.v2.svg">
  <img alt="Terminal: el stack en formato YAML" src="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/stack-light.v2.svg">
</picture>

---

## Código abierto

Paquetes de Laravel para problemas que resuelvo una y otra vez en sistemas
peruanos. En español, sin depender de servicios externos, con CI contra
Laravel 12 y 13. Tres tienen un gemelo en npm para el frontend, en TypeScript,
que se prueba con los mismos datos y da el mismo resultado que el backend.

| Paquete | Qué resuelve | Versión |
|---|---|---|
| [**laravel-feriados-peru**](https://github.com/Aeunius/laravel-feriados-peru) | Feriados nacionales y plazos en días hábiles según la Ley 27444, con días no laborables y feriados regionales | [![Packagist](https://img.shields.io/packagist/v/aeunius/laravel-feriados-peru.svg?style=flat-square)](https://packagist.org/packages/aeunius/laravel-feriados-peru) |
| [**laravel-peru-rules**](https://github.com/Aeunius/laravel-peru-rules) | Validación de RUC, DNI, carné de extranjería, celular, placa y CCI, con sus dígitos de control. Gemelo para el frontend, con reglas para Vue: [peru-rules-js](https://github.com/Aeunius/peru-rules-js) | [![Packagist](https://img.shields.io/packagist/v/aeunius/laravel-peru-rules.svg?style=flat-square)](https://packagist.org/packages/aeunius/laravel-peru-rules) [![npm](https://img.shields.io/npm/v/@aeunius/peru-rules.svg?style=flat-square)](https://www.npmjs.com/package/@aeunius/peru-rules) |
| [**laravel-catalogos-sunat**](https://github.com/Aeunius/laravel-catalogos-sunat) | Los catálogos de la facturación electrónica de la SUNAT (Anexo N.° 8) y sus códigos de retorno, consultables y con regla de validación. Gemelo para el frontend: [catalogos-sunat-js](https://github.com/Aeunius/catalogos-sunat-js) | [![Packagist](https://img.shields.io/packagist/v/aeunius/laravel-catalogos-sunat.svg?style=flat-square)](https://packagist.org/packages/aeunius/laravel-catalogos-sunat) [![npm](https://img.shields.io/npm/v/@aeunius/catalogos-sunat.svg?style=flat-square)](https://www.npmjs.com/package/@aeunius/catalogos-sunat) |
| [**laravel-numero-a-letras**](https://github.com/Aeunius/laravel-numero-a-letras) | Montos en letras con el formato de los comprobantes de la SUNAT (`MIL DOSCIENTOS CINCUENTA CON 50/100 SOLES`), en soles, dólares o euros. Núcleo en PHP puro, también sin Laravel. Gemelo para el frontend: [monto-en-letras-js](https://github.com/Aeunius/monto-en-letras-js) | [![Packagist](https://img.shields.io/packagist/v/aeunius/laravel-numero-a-letras.svg?style=flat-square)](https://packagist.org/packages/aeunius/laravel-numero-a-letras) [![npm](https://img.shields.io/npm/v/@aeunius/monto-en-letras.svg?style=flat-square)](https://www.npmjs.com/package/@aeunius/monto-en-letras) |

<details>
<summary><b>Por qué cada uno es más difícil de lo que parece</b></summary>

Calcular un plazo en días hábiles parece trivial hasta que aparecen los
feriados agregados por ley a mitad de año, los días no laborables que solo
aplican al Estado y los feriados regionales. El paquete de feriados cuenta los
plazos como manda la ley, y cada entidad lo ajusta a su realidad desde la
configuración.

Los catálogos de la SUNAT suelen copiarse de los PDF de las resoluciones, y ahí
se rompen: descripciones corridas entre filas, números de página pegados al
texto, códigos que dejaron de existir. El paquete de catálogos los toma de las
reglas de validación que publica la propia SUNAT, los regenera con un solo
comando y versiona sus fuentes, así que cada actualización se ve código por
código. Su gemelo en npm toma esos mismos datos de un tag fijo y trae cada
catálogo como un módulo aparte, para que los 49 mil códigos de producto no
entren en una app que solo necesita monedas.

Pasar un monto a letras parece un ejercicio de primer ciclo hasta que aparecen
«veintiún mil» frente a «veintiuno», «un millón de soles» frente a «un millón
cien soles», el redondeo de los céntimos y el límite de 100 caracteres de la
leyenda del comprobante. El paquete de montos en letras se prueba con cientos
de casos escritos a mano y se contrastó con ICU en doscientos mil números. Su
gemelo en npm pasa esos mismos casos y da el mismo texto en el navegador.

</details>

---

## En producción

Repositorios privados, institucionales y de empresa. Lo que hay dentro:

| Sistema | Qué resuelve | Stack |
|---|---|---|
| **SIMI** · UNALM | **~140 000 activos físicos** con responsables, locales y oficinas, integrado con SIGA (MEF) y SINADMOL (SBN) | Laravel 9 · SQL Server · Bootstrap 5 |
| **SINADMOL / SIGA v2** · UNALM | Transferencias patrimoniales, cuadros de tiempos y saldos, y reportes de gastos por grupo operacional a Excel y PDF | Laravel 11 · Vue 3 · ApexCharts · SQL Server |
| **Gestión de restaurantes** · Dibal | El sistema que sostiene a la empresa | Laravel 12 · Tailwind 4 · Vitest · MySQL |
| **Gestión de cocheras** · Dibal | Producto nuevo, en desarrollo | Laravel 12 · Tailwind 4 · Vite 7 · MySQL |
| **Servicio de WhatsApp** · Dibal | Envío de PDF por la Cloud API oficial, compartido entre productos | Laravel 12 · WhatsApp Cloud API |
| **Servicio de facturación** · Dibal | Facturación electrónica sacada del monolito, en construcción | Laravel 12 · MariaDB |
| **Intranet** · UNALM | Reportería mensual de ingresos y gastos con detalle y exportaciones | Laravel 9 · SQL Server · Vite |
| **Sistema heredado** · UNALM | Mantenimiento y actualizaciones, sigue en producción | Visual FoxPro 9 |

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/architecture-dark.svg">
  <img alt="La facturación se extrae del monolito de restaurantes a un servicio compartido que consumen todos los productos" src="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/architecture-light.svg">
</picture>

Al arrancar cocheras había que decidir: ¿duplicar la facturación que vivía dentro
del monolito, o extraerla? La sacamos como **microservicio reutilizable**, igual
que el envío por WhatsApp. Un solo lugar donde corregir cuando cambian las reglas
de SUNAT.

<details>
<summary><b>Laravel contra SQL Server</b></summary>

<br>

El ecosistema de Laravel asume MySQL o PostgreSQL, y la documentación se acaba
rápido cuando el motor es SQL Server. Lo resolví de punta a punta: imagen base
con **ODBC 18** y `pdo_sqlsrv`, migraciones que respetan T-SQL, y un entorno
Docker que levanta cualquier proyecto con un `make up`.

</details>

---

## Trayectoria

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/timeline-dark.v3.svg">
  <img alt="Línea de tiempo de 2013 a hoy: roles y stacks a lo largo de trece años" src="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/timeline-light.v3.svg">
</picture>

---

## Contacto

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://pe.linkedin.com/in/alejandro-gonzales-sarmiento)
