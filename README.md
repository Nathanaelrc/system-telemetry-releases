# System Telemetry — Releases

Paquetes de instalación públicos para **System Telemetry**, un dashboard nativo
GTK 4 para monitorizar hardware y gestionar perfiles de energía en Linux.

Public installation packages for **System Telemetry**, a native GTK 4 Linux
hardware and power-profile dashboard.

## Descargar / Download

Abre [Releases](https://github.com/Nathanaelrc/system-telemetry-releases/releases)
y descarga el formato de tu distribución:

- Ubuntu 22.04+, Debian 12+, TUXEDO OS: `system-telemetry-dashboard_*_all.deb`
- Fedora 39+: `system-telemetry-dashboard-*.noarch.rpm`
- `SHA256SUMS`: comprobación de integridad / integrity verification.

Los paquetes son independientes de la arquitectura; necesitan Python 3.10+,
GTK 4.6+, PyGObject y Cairo del sistema. `apt`/`dnf` resuelven las dependencias.
No incluyen un runtime autónomo ni las fuentes Fira.

Packages are architecture-independent and require the host's Python 3.10+,
GTK 4.6+, PyGObject and Cairo. `apt`/`dnf` resolve dependencies.

## Instalar / Install

En la carpeta de descarga / in your download directory:

```bash
sha256sum -c SHA256SUMS

# Debian / Ubuntu / TUXEDO OS
sudo apt install ./system-telemetry-dashboard_0.2.0_all.deb

# Fedora (no uses este comando en Debian / do not run this on Debian)
sudo dnf install ./system-telemetry-dashboard-0.2.0-1.noarch.rpm

system-telemetry
```

También aparece en el menú de aplicaciones. Fira Sans y Fira Mono son opcionales:
si no están instaladas, se usan fuentes del sistema.

The application also appears in the desktop menu. Fira Sans/Mono are optional;
system fonts are used when unavailable.

## Características / Features

- CPU/GPU, RAM/swap, disco/red, sensores, historial y exportación CSV.
- Temas claro/oscuro y traducción español/inglés.
- Control de TUXEDO `tccd` o Power Profiles, incluida la interfaz de `tuned-ppd`.
- Control del único gestor activo: TUXEDO, Power Profiles, tuned, auto-cpufreq o TLP.
  tuned-ppd usa la interfaz Power Profiles; System76 Power solo se detecta.
- Tarjetas con gráficos alineados e hilos CPU compactos: una fila hasta 12, dos para más.
- Ventiladores AMD PWM y NVIDIA NV-CONTROL X11 cuando el driver los permite.
  Pruebas manuales de 30 s, 50–100 %, retorno automático y límite de 80 °C.
- Wayland/X11 con decoraciones nativas; helper restringido con autorización polkit.

Hardware telemetry, history, CSV export, light/dark themes, Spanish/English,
TUXEDO/Power Profiles integration and native Wayland/X11 decorations.
Version 0.2.0 adds active-manager controls for tuned, auto-cpufreq and TLP,
a restricted polkit helper, aligned charts and compact CPU bars.
GPU manual fan tests are bounded to 30 seconds at 50–100%, restore automatic
control on completion/errors and enforce an 80°C guard. AMD requires exposed
PWM sensors; NVIDIA requires accessible X11 NV-CONTROL and driver permission.

Las lecturas GPU dependen del hardware y del controlador. Los sensores ausentes
se muestran como N/D; no se inventan temperaturas ni Watts. La carga Intel basada
en clientes DRM accesibles no equivale a carga global. No se activan servicios
ni se modifican curvas de ventiladores; un cambio de perfil puede ser rechazado
por la política D-Bus o polkit existente. Los perfiles TUXEDO son temporales.
No se modifican Coolbits ni Xorg. No se inicia una prueba sobre otro control
manual. El retorno automático no se puede garantizar ante SIGKILL o fallo del
driver; estos controles no reemplazan la gestión térmica del fabricante.

GPU readings depend on hardware and driver support. Missing values remain N/A.
Intel accessible-client DRM load is not global utilization. No services are
enabled and no fan curves are changed; existing D-Bus/polkit policy may reject
changes. Cooling tests do not replace vendor thermal management. Automatic
restoration cannot be guaranteed after SIGKILL or driver failure.

## Alcance / Scope

Este repositorio solo publica documentación y paquetes, no el repositorio fuente.
Los paquetes instalables sí incluyen los módulos Python necesarios para ejecutar
la aplicación. No se concede una licencia de código abierto.

This repository publishes documentation and packages, not the source repository.
Installable packages do contain the required Python modules. No open-source
license is granted.

La versión 0.2.0 se ha comprobado en TUXEDO OS/KDE Wayland con 58 pruebas.
El usuario confirmó que la versión 0.1.0 funciona en Fedora; la instalación
0.2.0 y los controles de cada gestor/GPU en Fedora aún requieren verificación.
Las pruebas de escritura de controles usan sensores y herramientas simulados.

Version 0.2.0 was checked on TUXEDO OS/KDE Wayland with 58 passing tests.
The user reported 0.1.0 working on Fedora; 0.2.0 installation and real manager/GPU
controls on Fedora remain unverified. Control-writing tests use simulated
sensors and tools. Packages are not GPG-signed; use SHA256SUMS for integrity.
