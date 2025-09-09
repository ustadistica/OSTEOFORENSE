
# Proyecto: template_pcd_usta
---
![Logo Universidad Santo Tomás](https://usantotomas.edu.co/hs-fs/hubfs/social-suggested-images/usantotomas.edu.cohs-fshubfsLogo%20Santoto%20-%20SP%20Bogota%20Horizontal%20blanco-2.png)

## Consultorio de Estadística y Ciencia de Datos
**Universidad Santo Tomás**

### 1. Descripción General
Este repositorio contiene todos los artefactos y el código para el proyecto "template_pcd_usta". 
La estructura sigue la metodología estandarizada del Consultorio, diseñada para garantizar la reproducibilidad, 
colaboración y calidad en cada fase del ciclo de vida de la ciencia de datos.

### 2. Stack Tecnológico
![Python 3.12](https://img.shields.io/badge/python-3.12-blue.svg)
- **Lenguaje Principal**: Python
- **Versión**: 3.12
- **Gestor de Dependencias**: Poetry

### 3. Cómo Empezar
Para configurar el entorno de desarrollo local, sigue estos pasos:

1.  **Clona el repositorio**:
    ```bash
    git clone https://github.com/ustadistica/project_template.git
    cd template_pcd_usta
    ```

2.  **Inicializa Poetry y instala las dependencias**:
    Asegúrate de tener Poetry instalado. Luego, ejecuta:
    ```bash
    # Este comando crea el pyproject.toml interactivamente
    poetry init 

    # Instala las dependencias definidas en pyproject.toml
    poetry install
    ```

3.  **Activa el entorno virtual**:
    ```bash
    poetry shell
    ```
Ahora estás dentro del entorno virtual del proyecto y puedes empezar a trabajar.

### 4. Estructura del Repositorio
- **/datos**: Contiene todos los datos, desde los crudos hasta los procesados, y los modelos guardados.
- **/docs**: Documentación clave del proyecto (informes, diagramas, carta de proyecto).
- **/notebooks**: Notebooks de Jupyter o R para análisis exploratorio y prototipado.
- **/src**: Código fuente de producción (scripts de Python o R).
- **.gitgnore**: Archivos y carpetas que no se suben al repositorio.
- **pyproject.toml**: Archivo de configuración del proyecto gestionado por Poetry.
- **README.md**: Este mismo archivo.
