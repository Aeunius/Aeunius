<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/banner-dark.svg">
  <img alt="Alejandro Gonzales Sarmiento — Fullstack Laravel + Vue — Socio fundador y CTO en Dibal" src="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/banner-light.svg">
</picture>

Construyo sistemas de gestión administrativa y financiera: control patrimonial,
facturación electrónica y reportería contable. Trece años entre escritorio, web
y móvil. Hoy reparto el tiempo entre los sistemas institucionales de la
**Universidad Nacional Agraria La Molina** y **Dibal**, la startup que cofundé.

---

## Dibal · Socio fundador y CTO

Dirijo la arquitectura y un equipo de **5 personas**. Construimos productos de
gestión para pymes sobre Laravel.

**Financiado dos veces por ProInnóvate** — StartUp Perú **9G** y **11G**.

| Producto | Qué hace | Stack |
|---|---|---|
| **Gestión de restaurantes** | El sistema que sostiene a la empresa | Laravel 12 · Tailwind 4 · Vitest · MySQL |
| **Gestión de cocheras** | Producto nuevo, en desarrollo | Laravel 12 · Tailwind 4 · Vite 7 · MySQL |
| **Servicio de WhatsApp** | Envío automatizado de PDF por la Cloud API oficial | Laravel 12 · WhatsApp Cloud API |
| **Servicio de facturación** | Facturación electrónica, en construcción | Laravel 12 · MariaDB |

### La decisión de arquitectura

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/architecture-dark.svg">
  <img alt="La facturación se extrae del monolito de restaurantes a un servicio compartido que consumen todos los productos" src="https://raw.githubusercontent.com/Aeunius/Aeunius/main/assets/architecture-light.svg">
</picture>

El sistema de restaurantes nació como un monolito, con la facturación
electrónica escrita dentro del propio código. Funcionaba, pero cada producto
nuevo obligaba a reimplementar lo mismo.

Al arrancar el sistema de cocheras la pregunta se volvió inevitable:
¿duplicamos la facturación, o la sacamos fuera? Optamos por extraerla como
**microservicio reutilizable**, igual que ya habíamos hecho con el envío por
WhatsApp.

Menos superficie duplicada, y un solo lugar donde corregir cuando cambian las
reglas de SUNAT.

---

## UNALM · Desarrollador Senior

En la Oficina de Tecnologías de Información y Comunicaciones (OTIC). Mi trabajo
aquí no es solo desarrollo: soy **coordinador SIGA–MEF** y **coordinador
SIAF–MEF**, y responsable de los sistemas institucionales —SINADMOL y
facturación electrónica—, lo que significa conocer las reglas del sistema
financiero público peruano tan bien como el código que las implementa.

Durante un tiempo estuve además a cargo del **soporte informático de la
Dirección General de Administración**, un área que no existía formalmente en el
organigrama, con un pequeño equipo a mi cargo.

| Sistema | Alcance | Stack |
|---|---|---|
| **SIMI** | Gestión de **~140 000 activos físicos**, integrado con SIGA (MEF) y SINADMOL (SBN) | Laravel 9 · SQL Server · Bootstrap 5 |
| **SINADMOL / SIGA v2** | Transferencias patrimoniales, cuadros de tiempos y saldos, reportes de gastos por grupo operacional con exportación a Excel y PDF | Laravel 11 · Vue 3 · ApexCharts · SQL Server |
| **Intranet** | Reportería mensual de ingresos y gastos con detalle navegable y exportaciones | Laravel 9 · SQL Server · Vite |
| **Sistema heredado** | Mantenimiento y actualizaciones, sigue en producción | Visual FoxPro 9 |

### Laravel contra SQL Server

No es el camino cómodo. Casi todo el ecosistema de Laravel asume MySQL o
PostgreSQL, y la documentación se acaba rápido cuando el motor es SQL Server
—pero es lo que hay en el sector público peruano.

Lo resolví de punta a punta: imagen base con el driver **ODBC 18** y
`pdo_sqlsrv`, consultas y migraciones que respetan las particularidades de
T-SQL, y un entorno Docker reproducible para levantar cualquier proyecto con un
solo `make up`.

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

---

## Antes

**Transportes Palomino** — Desarrollador y Jefe de Sistemas.
**Freelance** — de forma continua, en paralelo, desde el principio.

Trece años dan para ver morir varios stacks. Pasé por **Visual Basic 6**,
**C#**, **Visual FoxPro 9**, **WordPress** y **Joomla**, y los dejé cuando dejé
las empresas que los necesitaban — salvo el FoxPro de la universidad, que sigue
en producción y sigue siendo mi responsabilidad.

Me enseñó algo que no se aprende en stacks nuevos: el código que de verdad
importa es el que lleva años corriendo y no se puede apagar.

---

## Stack

**Backend**

![PHP](https://img.shields.io/badge/PHP_8.2-777BB4?style=flat-square&logo=php&logoColor=white)
![Laravel](https://img.shields.io/badge/Laravel_9--12-FF2D20?style=flat-square&logo=laravel&logoColor=white)
![SQL Server](https://img.shields.io/badge/SQL_Server-CC2927?style=flat-square&logo=microsoftsqlserver&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

**Frontend**

![Vue](https://img.shields.io/badge/Vue_3-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind_4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap_5-7952B3?style=flat-square&logo=bootstrap&logoColor=white)
![Vitest](https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white)

**Infraestructura**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Traefik](https://img.shields.io/badge/Traefik-24A1C1?style=flat-square&logo=traefikproxy&logoColor=white)
![AWS](https://img.shields.io/badge/AWS_RDS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)

<details>
<summary><b>Integraciones y lo que ya no uso</b></summary>

<br>

**Integraciones** — WhatsApp Cloud API · Facturación electrónica (SUNAT) · SIGA
y SIAF (MEF) · SINADMOL (SBN)

**Reportería** — Maatwebsite/Excel · DomPDF · Snappy

**Antes** — Visual Basic 6 · C# · Visual FoxPro 9 · WordPress · Joomla

</details>

---

## Formación

Técnico en Computación e Informática — **Instituto José Pardo**.

---

## Contacto

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://pe.linkedin.com/in/alejandro-gonzales-sarmiento)
