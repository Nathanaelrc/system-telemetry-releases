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
sudo apt install ./system-telemetry-dashboard_0.1.0_all.deb

# Fedora (no uses este comando en Debian / do not run this on Debian)
sudo dnf install ./system-telemetry-dashboard-0.1.0-1.noarch.rpm

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
- Detección informativa de TLP, auto-cpufreq, tuned y System76 Power.
- Wayland/X11 con decoraciones nativas; sin helper privilegiado.

Hardware telemetry, history, CSV export, light/dark themes, Spanish/English,
TUXEDO/Power Profiles integration and native Wayland/X11 decorations.

Las lecturas GPU dependen del hardware y del controlador. Los sensores ausentes
se muestran como N/D; no se inventan temperaturas ni Watts. La carga Intel basada
en clientes DRM accesibles no equivale a carga global. No se activan servicios
ni se modifican curvas de ventiladores; un cambio de perfil puede ser rechazado
por la política D-Bus existente.

GPU readings depend on hardware and driver support. Missing values remain N/A.
Intel accessible-client DRM load is not global utilization. No services are
enabled and no fan curves are changed; existing D-Bus policy may reject changes.

## Alcance / Scope

Este repositorio solo publica documentación y paquetes, no el repositorio fuente.
Los paquetes instalables sí incluyen los módulos Python necesarios para ejecutar
la aplicación. No se concede una licencia de código abierto.

This repository publishes documentation and packages, not the source repository.
Installable packages do contain the required Python modules. No open-source
license is granted.

La versión inicial se ha comprobado en TUXEDO OS/KDE Wayland. La instalación en
todas las versiones de Debian, Ubuntu y Fedora indicadas aún no se ha verificado.

The initial release was checked on TUXEDO OS/KDE Wayland; installation across
every listed Debian, Ubuntu and Fedora version has not yet been verified.
