# 🚀 AIDD-Vibe-coding

[![Tecnología](https://img.shields.io/badge/AI-Gemini-blue.svg)](https://gemini.google.com)
[![Tecnología](https://img.shields.io/badge/AI-Claude-purple.svg)](https://www.anthropic.com/claude)
[![Estado](https://img.shields.io/badge/Estado-Prototipo-orange)]()

## 📝 Resumen del Proyecto
Este repositorio contiene un conjunto de prompts y configuraciones para definir y operar agentes de IA (como Gemini y Claude) especializados en tareas de desarrollo de software. El objetivo es automatizar y estandarizar procesos como la generación de commits semánticos, la creación de documentación y el análisis de código.

---

## ✨ Características Principales
*   Generación automática de commits semánticos.
*   Análisis de código y generación de documentos de contexto del proyecto.
*   Creación automatizada de archivos `README.md` detallados.
*   Estructura centralizada para la gestión y reutilización de prompts de IA.

---

## 🛠️ Stack Tecnológico
*   **Modelos de IA Core:** Gemini, Claude
*   **Lenguajes de Configuración:** Markdown, TOML
*   **Entorno:** Consola / Terminal (CLI)

---

## ⚙️ Configuración y Ejecución Local

### Prerrequisitos
*   Git
*   CLI del Asistente de Google (Gemini)
*   CLI de Anthropic (Claude)

### Instalación
1.  Clonar el repositorio:
    ```bash
    git clone https://github.com/vibe-community-vip/AIDD-Vibe-coding.git
    cd AIDD-Vibe-coding
    ```
2.  Este proyecto no requiere instalación de dependencias a través de gestores de paquetes como `npm` or `pip`.

### Variables de Entorno
Para interactuar con los modelos de IA, debes configurar las claves de API correspondientes en tu entorno local, siguiendo la documentación oficial de cada herramienta CLI.

### Ejecución de Agentes
Los agentes se ejecutan invocando los prompts a través de su respectivo CLI. Por ejemplo:
```bash
# Ejemplo para ejecutar el generador de commits con Gemini
gemini -p prompts/commit.md
```

-----

## 🗺️ Arquitectura y Estructura del Código

El proyecto sigue un patrón de **Configuración Basada en Prompts**. La estructura está diseñada para separar las configuraciones específicas de cada IA de los prompts de tareas generales.

| Directorio | Función Principal |
| :--- | :--- |
| `/.gemini/` | Contiene configuraciones y comandos específicos para el CLI de Gemini. |
| `/.claude/` | Contiene configuraciones y comandos específicos para el CLI de Claude. |
| `/prompts/` | Almacena los prompts agnósticos que definen las tareas de los agentes. |

-----

## ✅ Pruebas
No aplica para este tipo de proyecto.

## 🤝 Contribución

Las contribuciones son bienvenidas. Por favor, sigue los siguientes pasos:

1.  Haz un `fork` del repositorio.
2.  Crea una nueva rama (`git checkout -b feature/AmazingFeature`).
3.  Asegúrate de que tus cambios no rompan los prompts existentes.
4.  Abre un *Pull Request* claro y detallado.
