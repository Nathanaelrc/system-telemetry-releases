# System Telemetry

## Español (Chile)

Lo hice como un proyecto personal para revisar el hardware y los perfiles de
energía de mis equipos Linux. Si te sirve, puedes descargarlo y usarlo también.
Es una aplicación GTK 4 sencilla, con temas claro y oscuro, sin efectos llamativos.
No es una herramienta oficial de NVIDIA, System76 ni TUXEDO.

### Descargar e instalar

En [Releases](https://github.com/Nathanaelrc/system-telemetry-releases/releases/latest)
están los paquetes y `SHA256SUMS`.

- **DEB:** Ubuntu 22.04+, Debian 12+ y derivados con Python 3.10+ y GTK 4.6+.
- **RPM:** Fedora 39+.
- Usa el paquete de tu distribución; no instales el RPM en Debian.

Desde la carpeta donde descargaste los archivos:

```bash
sha256sum -c SHA256SUMS

# Ubuntu / Debian / TUXEDO OS
sudo apt install ./system-telemetry-dashboard_0.3.0_all.deb

# Fedora
sudo dnf install ./system-telemetry-dashboard-0.3.0-1.noarch.rpm

system-telemetry
```

También aparece en el menú de aplicaciones. `apt` y `dnf` resuelven las
dependencias. Usa Python, GTK, PyGObject y Cairo del sistema; Fira Sans y Fira
Mono vienen incluidas, con su licencia SIL OFL. No descarga fuentes al abrir.

### Qué incluye

- Uso de CPU/GPU, RAM y swap, disco, red, sensores, historial y exportación CSV.
- Interfaz en español chileno e inglés, con idioma y tema guardados.
- Tarjetas ordenadas, chevrons discretos e hilos CPU en una o dos filas.
- Perfiles del único gestor activo: TUXEDO, Power Profiles, tuned, auto-cpufreq,
  TLP y System76 Power. tuned-ppd y los puentes de System76 usan D-Bus.
- En una sesión COSMIC, **Sistema** sigue su paleta GTK y acento. Necesita el
  tema GTK exportado por COSMIC y su portal. **Claro/Oscuro** conservan VS Code.
  Fuera de COSMIC se mantiene el comportamiento anterior.
- Ventiladores AMD PWM y NVIDIA NVML en Wayland/X11, cuando el driver lo permite.
  NVIDIA también tiene una alternativa NV-CONTROL para X11.
- Pruebas de ventilación de **30 segundos**, entre **50 y 100 %** y dentro de
  los límites del driver, con retorno automático y un límite de **80 °C**.
  Los controles que requieren permisos usan un helper restringido con polkit;
  la aplicación completa no se ejecuta como root.

### Lo que conviene saber

Los sensores dependen del equipo y del driver. Si una lectura no está disponible,
se muestra N/D, sin inventar temperaturas ni Watts. La lectura Intel basada en
clientes DRM accesibles no representa toda la carga GPU.

No instala gestores, no cambia Coolbits/Xorg y no modifica curvas persistentes
de ventiladores. Los perfiles TUXEDO son temporales. El control NVIDIA en Windows
no garantiza que el driver Linux lo permita. Las pruebas de ventilación no
reemplazan la gestión térmica del fabricante; el retorno automático no se puede
garantizar ante SIGKILL, fallas del driver o un corte de energía.

La versión 0.3.0 se comprobó en TUXEDO OS/KDE Wayland: **95 pruebas**, renderizado
GTK y arranque de ambos paquetes con datos reales. Fedora fue confirmado por
el usuario en versiones anteriores. Pop!_OS, COSMIC, Cinnamon y Xfce todavía
necesitan pruebas en sus entornos reales; los adaptadores y la integración COSMIC
se probaron con simulaciones. No se probaron escrituras físicas AMD/NVIDIA aquí.

Este repositorio publica documentación y paquetes. El código fuente se mantiene
en un repositorio privado; los paquetes incluyen los módulos Python necesarios.
Puedes usar la aplicación, pero eso no concede una licencia de código abierto.
Las fuentes Fira conservan su licencia propia. Los paquetes no tienen firma GPG:
SHA-256 sirve para comprobar integridad, no como firma independiente.

## English

I made this as a personal project to check hardware and power profiles on my
Linux computers. If it is useful to you, you are welcome to download and use it.
It is a simple GTK 4 app with light and dark themes, without flashy effects.
It is not an official NVIDIA, System76 or TUXEDO tool.

### Download and install

Get your distribution's package and `SHA256SUMS` from
[Releases](https://github.com/Nathanaelrc/system-telemetry-releases/releases/latest).
Use the commands above: DEB for Ubuntu 22.04+, Debian 12+ and compatible
derivatives; RPM for Fedora 39+. Do not use the RPM on Debian.

The app also appears in the desktop menu. It needs host Python 3.10+, GTK 4.6+,
PyGObject and Cairo; `apt`/`dnf` resolve dependencies. Fira Sans/Mono and their
SIL OFL license are included. Fonts are not downloaded at startup.

### What is included

- CPU/GPU, RAM/swap, disk/network, sensors, history and CSV export.
- Chilean Spanish and English, with saved language and theme preferences.
- Tidier cards, subtle chevrons and CPU bars in one or two rows.
- Controls for the single active manager: TUXEDO, Power Profiles, tuned,
  auto-cpufreq, TLP and System76 Power. PPD bridges are grouped by bus owner.
- In a COSMIC session, **System** follows its exported GTK palette and portal
  accent. **Light/Dark** keep the VS Code palettes. Other desktops are unchanged.
- Conditional AMD PWM and NVIDIA NVML fan controls on Wayland/X11, with an
  X11 NV-CONTROL fallback. Tests last **30 seconds**, use **50–100%** within
  driver limits, restore automatic mode and stop at **80°C**.
- A restricted polkit helper for privileged controls; the GUI does not run as root.

### Things to keep in mind

Hardware support varies. Missing readings stay N/A. Intel accessible-client DRM
load is not global GPU load. The app does not install energy managers, change
Coolbits/Xorg or set persistent fan curves. TUXEDO profiles are temporary.
Windows fan support does not guarantee Linux driver support. Cooling tests do
not replace vendor thermal management, and automatic restoration cannot be
guaranteed after SIGKILL, driver failure or power loss.

Version 0.3.0 was checked on TUXEDO OS/KDE Wayland with **95 passing tests**,
GTK rendering and live launches of both packages. Earlier versions were
user-confirmed on Fedora. Pop!_OS, COSMIC, Cinnamon and Xfce still need testing
on real systems; adapters and COSMIC integration were tested with simulations.
Physical AMD/NVIDIA fan writes were not tested on this development machine.

This repository contains documentation and packages, not the private source
repository. Packages include the Python modules needed to run the app.
You are welcome to use it; no open-source license is granted. Fira fonts retain
their own license. Packages are not GPG-signed; SHA-256 checks integrity and is
not an independent signature.
