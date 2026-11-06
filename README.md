# CyberTec Homelab

**Nuestro laboratorio de ciberseguridad hecho en casa: un servidor armado con piezas recicladas para practicar hacking ético sin tocar sistemas reales.**

Proyecto de **CyberTec**, la agrupación estudiantil de ciberseguridad del Tec CEM.

---

## ¿Qué es esto?

Un servidor personal, no tan grande ni tan pesado de armar, pero muy útil. Lo construimos con componentes de computadoras viejas que encontramos y compramos, y ahí viven máquinas virtuales vulnerables a propósito para que el grupo practique.

Todo lo que hacemos pasa dentro de una **red aislada**. Nada de lo que atacamos sale al mundo ni toca la red normal.

## Objetivos

- Tener un lugar seguro donde practicar pentesting y hacking ético.
- Aprender armando: hardware, virtualización, redes y seguridad.
- Dejar todo documentado para que cualquiera del grupo (o de otro grupo) pueda replicarlo.

## Cómo está pensado

```
Internet
   │
Router (red de casa o del Tec)
   │      sin acceso directo al lab
   │
Servidor Proxmox  ◄──── VPN (WireGuard / Tailscale) ◄──── miembros de CyberTec
   │
Red aislada del lab
   ├── Máquina atacante (Kali o Parrot)
   ├── Máquinas vulnerables (DVWA, Juice Shop, Metasploitable)
   └── Firewall virtual (pfSense / OPNsense, opcional)
```

## Hardware

| Componente | Mínimo | Ideal |
|---|---|---|
| RAM | 16 GB | 32 GB |
| CPU | De hace ~8 años, con virtualización (Intel VT-x o AMD-V) activada en la BIOS | Más núcleos = más VMs a la vez |
| Disco | SSD de 240 GB | SSD de 500 GB |
| Red | 1 puerto Ethernet | 2 puertos |

La lista completa con precios y estado de cada pieza está en `docs/01-hardware.md`.

## Software y máquinas

- **Base:** Proxmox VE
- **Atacante:** Kali Linux o Parrot
- **Web:** DVWA, OWASP Juice Shop
- **Redes y servicios:** Metasploitable 2 y 3, máquinas de VulnHub
- **Más adelante:** un laboratorio de Active Directory

## Estructura del repo

```
cybertec-homelab/
├── README.md
├── docs/           # guía paso a paso, en orden
│   ├── 01-hardware.md
│   ├── 02-instalacion-proxmox.md
│   ├── 03-red-aislada.md
│   └── 04-maquinas-vulnerables.md
├── scripts/        # scripts de instalación y configuración
├── configs/        # archivos de configuración (sin secretos)
├── ejercicios/     # guías de práctica por máquina
├── .gitignore
└── LICENSE
```

## Roadmap

- [ ] Definir objetivo, presupuesto y responsables
- [ ] Conseguir y armar el hardware
- [ ] Instalar Proxmox VE
- [ ] Crear la red aislada y el acceso por VPN
- [ ] Montar la máquina atacante y las máquinas vulnerables
- [ ] Guardar snapshots de cada VM
- [ ] Documentar todo en `docs/`
- [ ] Escribir las guías de ejercicios
- [ ] Sesión de prueba con el grupo

El detalle de fechas y responsables está en la pestaña **Projects** de la organización.

## Reglas del lab

1. **Solo atacamos lo que es nuestro.** Los ejercicios se hacen únicamente contra las máquinas del lab.
2. **Las máquinas vulnerables nunca se exponen** a internet ni a la red normal.
3. **El acceso es por VPN** y solo para miembros del grupo.
4. Todo lo que se aprende aquí es para uso **educativo y ético**.

## Seguridad del repo

Nunca subimos contraseñas, llaves SSH, tokens, llaves de VPN ni las IPs reales de nuestra red interna. El `.gitignore` ayuda, pero antes de cada commit revisa qué estás subiendo con `git status` y `git diff`.

Si por error subes un secreto, **cámbialo de inmediato**. Borrarlo del repo no basta, porque queda en el historial.

## ¿Quieres colaborar?

1. Elige una tarea del tablero de **Projects** o abre un **Issue** con tu idea.
2. Crea tu propia rama (no se edita directo en `main`).
3. Haz tus cambios y abre un **Pull Request** para que alguien del grupo lo revise.

## Licencia

Este proyecto usa la licencia MIT .

---

Hecho con ☕ y piezas recicladas por **CyberTec**.
