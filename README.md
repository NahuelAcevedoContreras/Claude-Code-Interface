# Claude Code Interface

<p align="center">
  <img src="resources/icon.png" width="96" alt="Claude Code Interface" />
</p>

<p align="center">
  <strong>Interfaz gráfica de escritorio flotante y minimalista para Claude Code CLI.</strong><br>
  Optimizada para un flujo de trabajo ágil, visual y sin fricciones en Windows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%20x64%20(Portable)-0078D6?style=flat-square&logo=windows" alt="Platform" />
  <img src="https://img.shields.io/badge/Status-Beta-informational?style=flat-square" alt="Status" />
  <img src="https://img.shields.io/badge/Claude%20Code-Compatible-D97757?style=flat-square" alt="Claude Code" />
  <img src="https://img.shields.io/badge/AI%20Providers-Official%20%7C%20Proxies%20%7C%20OpenRouter%20%7C%20DeepSeek-2ea44f?style=flat-square" alt="Providers" />
  <img src="https://img.shields.io/badge/Distribution-Portable%20Executable-blue?style=flat-square" alt="Distribution" />
  <img src="https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square" alt="License" />
</p>

---

> **Nota sobre el estado del proyecto (Fase Beta):**  
> Claude Code Interface se encuentra actualmente en fase beta pública. La aplicación es completamente funcional y portable, pero continúa en desarrollo activo para optimizar rendimiento y estabilidad.

---

## Descripción General

Claude Code Interface proporciona una capa gráfica flotante (*Always-on-top*) para la herramienta oficial de línea de comandos de Anthropic, **Claude Code**. Su objetivo es simplificar la interacción diaria con el asistente de código, permitiendo revisar respuestas en Markdown con resaltado de sintaxis, gestionar permisos de herramientas, adjuntar archivos y capturas de pantalla, y administrar múltiples sesiones concurrentes sin necesidad de mantener terminales abiertas manualmente.

---

## Nuevas Características y Mejoras en este Port

Este desarrollo corresponde a un port adaptado y optimizado específicamente para sistemas Windows, incorporando las siguientes capacidades:

### Modo LockScreen (Fijación de Ventana y Copiado)
- Opción accesible desde el menú de configuración que bloquea la posición de la ventana en pantalla.
- Al activarse, evita movimientos accidentales por arrastre y habilita la selección natural de texto con el cursor, permitiendo copiar bloques de código o texto mediante `Ctrl + C` o el menú contextual del botón derecho (*Copiar*).
- Al desactivarse, restablece el comportamiento habitual de arrastre por pantalla.

### Ejecutable Portable Independiente
- Compilado como un único binario ejecutable (`.exe`) que no requiere instalación en el sistema, elevación de privilegios de administrador ni configuración manual de dependencias de compilación.

### Captura Inteligente Multi-Monitor
- Detección precisa de las coordenadas de la ventana para determinar en qué monitor se encuentra la aplicación, garantizando que la captura de pantalla adjuntada corresponda siempre al monitor de trabajo correcto en entornos con dos o más pantallas.

### Control de Instancia Única (Single Instance Lock)
- Mecanismo que previene la ejecución simultánea de múltiples instancias del programa. Cualquier intento de apertura posterior enfoca y restaura la ventana existente.

### Administración Avanzada de Sesiones
- Menú contextual en el panel de historial que permite fijar sesiones prioritarias (*Pin*), renombrar identificadores de chat y ejecutar la eliminación completa de los archivos de registro (`.jsonl`) en todas las rutas de proyecto de Claude Code. Si se elimina una sesión activa en una pestaña abierta, dicha pestaña se cierra de forma automática.

### Compatibilidad Ampliada de Red e Inferencia
- Soporte nativo para operar mediante proxies locales, túneles HTTP y proveedores externos de modelos de lenguaje.

---

## Requisitos del Sistema

Para el correcto funcionamiento de la interfaz, el entorno de Windows debe contar con:

1. **Node.js**: Versión 18.x o superior instalada en el sistema.
2. **Claude Code CLI**: La herramienta oficial instalada globalmente:
   ```bash
   npm install -g @anthropic-ai/claude-code
   ```
3. **Inicialización**: Haber ejecutado al menos una vez el comando `claude` en terminal para validar credenciales o configuración inicial (`claude --version`).

---

## Compatibilidad: API Oficial, Proxies y Proveedores Externos

La aplicación se comunica directamente con el proceso de Claude Code en el equipo, heredando todas las capacidades de integración del CLI:

- **Anthropic Oficial**: Autenticación directa mediante `claude auth login` o asignación de `ANTHROPIC_API_KEY`.
- **Proxies Locales y Corporativos**: Total compatibilidad con proxies como `antigravity-claude-proxy`, proxies locales en `http://localhost`, túneles corporativos o LiteLLM.
- **Proveedores de Inferencia Alternativos**: Capacidad de conectar con modelos externos (DeepSeek, OpenRouter, OpenAI, Ollama u otros compatibles) mediante la configuración de variables de entorno como `ANTHROPIC_BASE_URL` o modificaciones en `~/.claude/settings.json`.

---

## Descarga y Uso

No se requiere clonar el código fuente ni compilar artefactos locales:

1. Acceda a la sección de **Releases** de este repositorio.
2. Descargue el ejecutable **`Claude Code Interface-Portable.exe`**.
3. Ejecute el archivo para iniciar la aplicación inmediatamente.

---

## Resumen de Funcionalidades

- **Ventana Flotante Always-on-top**: Interfaz compacta con transparencia y efecto de desenfoque de fondo.
- **Modo Ancho Completo (Full Width)**: Expansión de la interfaz para lectura detallada de diferencias de código y respuestas extensas.
- **Soporte Multi-Pestaña**: Gestión de sesiones de trabajo independientes en pestañas simultáneas.
- **Selector de Directorios**: Configuración de directorio base y anexión de múltiples carpetas adicionales de consulta (*Add directory*).
- **Entrada por Voz**: Dictado directo asistido por transcripción local.
- **Temas Claro y Oscuro**: Paleta visual conmutables para coincidencia con la iluminación del espacio de trabajo.

---

## Controles y Atajos de Teclado

| Acción | Atajo / Control |
|---|---|
| Mostrar / Ocultar (Minimizar) | `Ctrl + Shift + K` o `Alt + Espacio` |
| Mover ventana | Arrastrar con clic izquierdo sobre el área de cabecera (con LockScreen inactivo) |
| Bloquear posición y permitir copiado | Activar **LockScreen** en el menú de ajustes (`...`) |
| Alternar panel expandido / compacto | Clic sobre la pestaña activa |
| Cerrar pestaña activa | Botón de cierre (`X`) en la pestaña |
| Ajustes rápidos | Menú contextual (`...`) |
| Historial de sesiones | Botón de historial (`Reloj`) |

---

## Créditos y Reconocimientos

Este proyecto está basado en la idea y desarrollo original de **[siteboon/claudecodeui](https://github.com/siteboon/claudecodeui)**.

Agradecemos a **siteboon** por la creación de la arquitectura base concebida originalmente para macOS. Este repositorio alberga el **port independiente para Windows**, optimizado para ejecución portable y complementado con soporte multi-pantalla, modo LockScreen, bloqueo de instancias duplicadas y gestión de historial.

---

## Licencia

Distribuido bajo los términos de la licencia [MIT](LICENSE).
