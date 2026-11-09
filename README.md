# CoreChat

![Java](https://img.shields.io/badge/Java-17%2B-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Paper%20%7C%20Purpur%20%7C%20Spigot-brightgreen?style=for-the-badge)
![Version](https://img.shields.io/badge/Minecraft-1.20%2B-blue?style=for-the-badge)
![Discord](https://img.shields.io/badge/Discord-CoreLab-5865F2?style=for-the-badge&logo=discord&logoColor=white)

CoreChat es un plugin modular y optimizado de gestión de chat para servidores de Minecraft basados en Paper, Purpur y Spigot. Cuenta con soporte nativo para colores HEX/RGB, etiquetas interactivas y filtros de moderación en tiempo real sin impacto en el tick rate del servidor.

---

## Características Principales

* **Formato Visual Avanzado:** Soporte completo para colores hexadecimales (`&#RRGGBB`), degradados y formato moderno MiniMessage.
* **Tags Interactivos:**
  * `[item]` / `[i]` — Muestra el objeto de la mano con encantamientos y lore mediante hover.
  * `[pos]` — Comparte las coordenadas actuales del jugador.
  * `[ping]` — Muestra la latencia en milisegundos.
* **Moderación y Anti-Spam:**
  * Cooldowns configurables entre mensajes.
  * Detección y bloqueo de mayúsculas excesivas.
  * Filtro de caracteres y palabras repetitivas.
* **Integraciones Nativas:**
  * **PlaceholderAPI (PAPI):** Compatibilidad con cualquier placeholder en el formato del chat.
  * **Vault / LuckPerms:** Sincronización automática de prefijos, sufijos y grupos de permisos.
* **Procesamiento Asíncrono:** Manejo de eventos en segundo plano para evitar caídas de rendimiento (lag spikes).

---

## Requisitos del Servidor

* **Java:** 17 o superior (Recomendado Java 21).
* **Software:** Paper, Purpur o Spigot (versión 1.20 o superior).
* **Dependencias:**
  * [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) (Recomendado)
  * [Vault](https://www.spigotmc.org/resources/vault.34315/) + Plugin de permisos (ej. [LuckPerms](https://luckperms.net/))

---

## Instalación

1. Descarga la versión más reciente desde [GitHub Releases](https://github.com/DiegoteUnCut/CoreChat/releases).
2. Coloca el archivo `CoreChat.jar` en la carpeta `plugins/` del servidor.
3. Asegúrate de tener instalados Vault y PlaceholderAPI.
4. Inicia o reinicia el servidor para generar los archivos base.
5. Ajusta los parámetros en `plugins/CoreChat/config.yml`.
6. Aplica los cambios usando `/corechat reload`.

---

## Comandos y Permisos

| Comando | Permiso | Descripción |
| :--- | :--- | :--- |
| `/corechat reload` | `corechat.admin.reload` | Recarga la configuración sin reiniciar el servidor. |
| `/corechat clear` | `corechat.admin.clear` | Limpia el historial del chat global. |
| — | `corechat.tag.item` | Permite usar la etiqueta `[item]` en el chat. |
| — | `corechat.tag.pos` | Permite usar la etiqueta `[pos]` en el chat. |
| — | `corechat.tag.ping` | Permite usar la etiqueta `[ping]` en el chat. |
| — | `corechat.bypass.cooldown` | Omite el tiempo de espera entre mensajes. |
| — | `corechat.bypass.filter` | Omite los filtros de spam y mayúsculas. |

---

## Configuración Base (`config.yml`)

```yaml
chat:
  format: "<gray>[<#00AAFF>{vault_prefix}<gray>] <white>{player_name}: <#E0E0E0>{message}"
  cooldown: 2.0

tags:
  item:
    enabled: true
    permission: "corechat.tag.item"
    format: "<yellow>[{item_name} <gray>x{item_amount}<yellow>]"
  pos:
    enabled: true
    permission: "corechat.tag.pos"
    format: "<aqua>[X: {x}, Y: {y}, Z: {z}]"
  ping:
    enabled: true
    permission: "corechat.tag.ping"
    format: "<green>[{ping}ms]"
