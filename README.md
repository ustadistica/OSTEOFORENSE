
# Proyecto: Reconocimiento de personas desaparecidas en Colombia mediante análisis facial
 
---
![Logo Universidad Santo Tomás](https://usantotomas.edu.co/hs-fs/hubfs/social-suggested-images/usantotomas.edu.cohs-fshubfsLogo%20Santoto%20-%20SP%20Bogota%20Horizontal%20blanco-2.png)

## Consultorio de Estadística y Ciencia de Datos
**Universidad Santo Tomás**

Responsables

- Alejandra Benedetti
- Angela Orguela
- Natalia Zarate
- Alejandro Chavarro

----------------------------------------------

### Introducción

El Proyecto Osteo-Forense busca resolver el problema de la desaparición de personas en Colombia, donde a menudo no se tienen registros tradicionales para la identificación. Combinando la antropología forense y la visión por computador, el proyecto usa fotografías para estandarizar imágenes, extraer rasgos faciales como puntos de referencia y medidas craneofaciales, y crear representaciones numéricas (embeddings) de los rostros. Estas representaciones permiten realizar comparaciones automáticas para fortalecer los procesos de identificación de las víctimas.

----------------------------------------------

### 1. Descripción General

Este repositorio documenta la primera fase del Proyecto Osteo-Forense, cuyo objetivo es apoyar el reconocimiento de personas desaparecidas por el conflicto armado en Colombia mediante análisis facial. Ante las limitaciones de métodos tradicionales como huellas, odontogramas o ADN, se exploran alternativas de antropología forense y visión por computador, en particular la normalización de fotografías y su preparación para el posterior análisis de landmarks, medidas craneofaciales y embeddings faciales.

La fase inicial implementó un pipeline en Python para:

- Cargar fotografías desde la plataforma SICLICO-HOPE.
- Normalizarlas (128×128 px, formato RGB, tensores 3×128×128).
- Integrarlas con los metadatos de cada caso (archivo Excel BASE OSTEO 50.xlsx).
- Generar un dataset estructurado y validado (dataset_osteo.pkl).

El resultado es un conjunto de datos homogéneo y auditado, listo para entrenar modelos de aprendizaje profundo y extraer información morfométrica en etapas posteriores.

----------------------------------------------

### 2. ¿Qué debemos saber sobre el proyecto?

#### 2.1. ¿Todas las fotos son iguales?  
No. Las imágenes de **SICLICO-HOPE** presentaban diferencias en formato, tamaño, iluminación, ángulo y calidad, lo que dificultaba su análisis automático.  
- **Solución:** se normalizaron todas a **128×128 píxeles en RGB** y se almacenaron como tensores.  
- **Resultado:** se obtuvo un conjunto homogéneo y directamente comparable.  

#### 2.2. ¿Podemos extraer curvas/landmarks de las fotos?  
Sí. Existen modelos como **Dlib, Mediapipe u OpenFace**, que detectan entre **68 y 468 landmarks faciales** (ojos, nariz, boca, mandíbula, contorno craneal).  
- En esta fase **no se extrajeron landmarks**, pero las imágenes quedaron listas para que dichos algoritmos funcionen en etapas posteriores.  

#### 2.3. ¿Qué información podemos obtener de las fotos?  
- **Cualitativa:** rasgos visibles como cicatrices, arrugas o vello facial.  
- **Cuantitativa:**  
  - Landmarks (coordenadas anatómicas).  
  - Medidas craneofaciales (distancias y proporciones).  
  - Embeddings faciales (vectores numéricos del rostro).  
  - Estadísticas de variabilidad intra e interindividual.  

Además, las fotos se vincularon con **metadatos** de un archivo Excel (`BASE OSTEO 50.xlsx`), creando una tabla unificada con:  
- **ID único** de la persona.  
- Variables asociadas.  
- Imagen procesada.  

#### 2.4. ¿Cómo se traduce esa información en embeddings, tablas y reportes?  
- Aunque aún **no se generaron embeddings**, el dataset quedó preparado para aplicar modelos de *deep learning*.  
- Se creó un **DataFrame** donde cada ID está asociado con su imagen procesada y metadatos.  
- Este dataset fue exportado en formato **Pickle** (`dataset_osteo.pkl`).  
- Se realizaron **verificaciones visuales y de correspondencia entre IDs** para garantizar la consistencia de la base.  


----------------------------------------------

### 3. Stack Tecnológico  

![Python 3.11](https://img.shields.io/badge/python-3.11-blue.svg)  
![Google Colab](https://img.shields.io/badge/Google%20Colab-notebooks-orange.svg)  
![Jupyter](https://img.shields.io/badge/Jupyter-compatible-lightgrey.svg)  
![Poetry](https://img.shields.io/badge/Poetry-deps%20%26%20envs-blueviolet.svg)  

**Lenguajes, versión y gestión de dependencias/entorno**  

- **Lenguaje principal**: Python 3.11  
- **Entorno de desarrollo**: Google Colab  
- **Compatibilidad local**: Jupyter Notebooks  
- **Gestión de dependencias y entornos**: Poetry  

----------------------------------------------

### 4. Cómo Empezar
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

----------------------------------------------

### 5. Estructura del Repositorio
- **/datos**: Contiene todos los datos, desde los crudos hasta los procesados, y los modelos guardados.
- **/docs**: Documentación clave del proyecto (informes, diagramas, carta de proyecto).
- **/notebooks**: Notebooks de Jupyter o R para análisis exploratorio y prototipado.
- **/src**: Código fuente de producción (scripts de Python o R).
- **.gitgnore**: Archivos y carpetas que no se suben al repositorio.
- **pyproject.toml**: Archivo de configuración del proyecto gestionado por Poetry.
- **README.md**: Este mismo archivo.

----------------------------------------------

### 6. Datos y Fuentes  

#### Fuente principal de fotografías para análisis  

- **Plataforma HOPE (Hagamos Obligatorio Poder Encontrarlos)**  
  HOPE forma parte del *Registro Nacional de Desaparecidos* (RND) de Colombia y se integra con el sistema **SIRDEC** (Sistema de Información Red de Desaparecidos y Cadáveres), administrado por el Instituto Nacional de Medicina Legal y Ciencias Forenses.  
[Acceso a HOPE](https://siclico.medicinalegal.gov.co/hope/)  

- **SIRDEC (Sistema de Información Red de Desaparecidos y Cadáveres)**  
  Actúa como el sistema de consulta principal del RND, recolectando información desde el 1 de enero de 2007 sobre personas desaparecidas y cadáveres ingresados a Medicina Legal. Incluye registros de desaparecidos, cadáveres y casos no reclamados.  
[Acceso a SIRDEC](https://siclico.medicinalegal.gov.co/consultasPublicas/Desaparecidos.xhtml)  

#### Papel de los familiares y aportes contextuales  

- Las **fotografías** incluidas en HOPE son aportadas por familiares de las personas desaparecidas, aportando un elemento visual determinante para el análisis forense mediante visión computacional.  
- HOPE también permite hacer seguimiento de casos judicializados, facilitando el nexo entre la información visual (imágenes) y el contexto legal del caso.  

#### En resumen, los datos incluyen:  

| Fuente / Sistema | Tipo de contenido                                   | Uso en el Proyecto Óseo                                              |
|------------------|-----------------------------------------------------|----------------------------------------------------------------------|
| **HOPE (RND)**   | Fotografías aportadas por familias                  | Insumo visual para procesamiento, normalización y análisis facial.   |
| **SIRDEC (RND)** | Registros de desaparecidos y cadáveres, metadatos   | Vincular imágenes con datos de casos y dar trazabilidad forense.     |

----------------------------------------------

### 7. Metodología (resumen)  

El Proyecto Osteo-Forense se estructura en fases progresivas, que combinan procesamiento digital de imágenes con técnicas de antropología forense y aprendizaje automático.  

#### Fase 1 — Procesamiento inicial (ya realizada)  
- **Carga y estandarización de fotografías**: se normalizaron todas las imágenes de HOPE a 128×128 píxeles en formato RGB.  
- **Integración con metadatos**: se enlazaron las imágenes con el archivo `BASE OSTEO 50.xlsx`, consolidando un dataset único y validado.  
- **Verificación de consistencia**: conteo de IDs, visualización de ejemplos y exportación en formato `dataset_osteo.pkl`.  

#### Fase 2 — Extracción de información facial (en planeación)  
- **Landmarks faciales**: detección automática de entre 68 y 468 puntos de referencia anatómicos (ej. glabela, nasion, gnathion, zygion).  
- **Medidas morfométricas**: cálculo de distancias y proporciones craneofaciales.  
- **Embeddings faciales**: representación numérica del rostro para análisis estadístico y comparativo.  

#### Fase 3 — Análisis morfométrico y estadístico (propuesto, en evaluación)  
- **Geometric Morphometrics**  
  - Uso de landmarks para análisis con **PCA** (componentes principales) y distancias de **Mahalanobis**.  
  - Permite mantener la interpretación antropológica clásica, comprensible para peritos forenses.  

- **Fusión discriminativa**  
  - Estrategia de **stacking + calibración** para combinar diferentes fuentes de evidencia (morfometría, embeddings de deep learning, calidad de la foto).  
  - Busca mejorar el rendimiento práctico y reducir falsos positivos.  

#### Enfoque a futuro  
- **Validación forense**: los resultados deberán ser evaluados con criterios de reproducibilidad, trazabilidad y aceptabilidad judicial.  
- **Posible integración** con otros marcos metodológicos (ej. fusión bayesiana, teoría de valores extremos para escenarios open-set).  

----------------------------------------------

### 8. Flujo de trabajo sugerido  

El flujo de trabajo del **Proyecto Óseo** se organiza en fases que van desde la obtención de fotografías hasta los análisis estadísticos avanzados.  
Cada registro está vinculado a un **ID único** basado en las iniciales de la persona, lo que asegura trazabilidad entre imágenes, metadatos y resultados.  

1. **Ingesta y limpieza de datos**  
   - Descarga de fotografías desde la plataforma HOPE.  
   - Asignación de **ID único** (iniciales de la persona).  
   - Normalización de imágenes (128×128 px, RGB).
   - Crear una base de datos con la información de la página (HOPE).
   - Crear una carpeta con las fotografías selecionadas de la página (HOPE).
   - Organización de metadatos en un archivo unificado (`BASE OSTEO 50.xlsx`). 

2. **Integración**  
   - Creación de un dataset estructurado que combine:  
     - ID único (ej. MABC).  
     - Metadatos tabulares (edad, sexo, etc.).  
     - Imagen procesada en tensor.  
   - Exportación en formato reproducible (`dataset_osteo.pkl`).  

3. **Extracción de características faciales** *(fase planeada)*  
   - Detección de landmarks faciales (68–468 puntos).  
   - Cálculo de medidas craneofaciales (distancias y proporciones).  
   - Generación de embeddings faciales para comparación numérica.  

4. **Análisis y modelado** *(fase propuesta)*  
   - Aplicar **Geometric Morphometrics** (landmarks + PCA + Mahalanobis).  
   - Implementar **fusión discriminativa** (stacking + calibración) para integrar morfometría y embeddings.  
   - Evaluación de variabilidad intra/interindividual.  

5. **Resultados y validación**  
   - Tablas de medidas, representaciones gráficas y comparaciones entre individuos.  
   - Validación de consistencia técnica y trazabilidad de IDs.  
   - Preparación de resultados para posible aceptación judicial y pericial.  

6. **Entrega**  
   - Reportes reproducibles en notebooks (`.ipynb`).  
   - Documentación en README para guiar uso y replicación del pipeline. 

----------------------------------------------

### 9. Resumen General

- Las imágenes eran heterogéneas, pero se **normalizaron a un formato y tamaño uniforme**.  
- Se dejó preparado el terreno para la **extracción de landmarks y medidas morfométricas** en fases posteriores.  
- Se logró **integrar imágenes y metadatos** en un dataset tabular con trazabilidad garantizada.  
- Se verificó la **consistencia y validez de la base** mediante controles visuales y de correspondencia.  
- **Resultado:** un conjunto de datos robusto y auditado, listo para alimentar algoritmos de alineación, embeddings y validaciones estadísticas en las siguientes fases del proyecto. 

----------------------------------------------

### 10. Licencia  

Este proyecto se distribuye bajo la **Licencia MIT**, lo que permite su uso, copia, modificación y distribución con fines académicos y de investigación, siempre que se mantenga el reconocimiento de la autoría original.  

**Nota importante:** Las fotografías y datos provenientes de la plataforma [HOPE](https://siclico.medicinalegal.gov.co/hope/) y del **Instituto Nacional de Medicina Legal y Ciencias Forenses** tienen un carácter sensible. Su uso está sujeto a las políticas de privacidad, derechos humanos y restricciones legales de la entidad proveedora de los datos.  


