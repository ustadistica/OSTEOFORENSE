
# Carpeta: Datos y Conexiones
---
Esta carpeta almacena todos los activos de datos del proyecto, organizados por su estado en el ciclo de vida.

## Subcarpetas y Artefactos Correspondientes

### `0_raw/`
- **Propósito**: Almacenar los datos originales en su formato inicial, sin ninguna modificación.
- **Artefactos**:
    - `Datos brutos`: Archivos CSV, Excel, JSON, bases de datos, etc., tal como fueron entregados por el cliente o descargados.
- **Regla de Oro**: Esta carpeta debe ser tratada como de **solo lectura**. Nunca modifiques los archivos aquí. Si necesitas hacer cambios, crea una copia en `1_processed`.

### `1_processed/`
- **Propósito**: Contener los datos que han sido limpiados, transformados, y preparados para el modelado.
- **Artefactos**:
    - `Script de integración de fuentes (ETL)` (El resultado de este script vive aquí).
    - `Script de limpieza` (El resultado de este script vive aquí).
    - `Datos limpios`: Versiones de los datos sin valores nulos, con tipos corregidos, etc.
    - `Datos transformados`: Datos listos para ser consumidos por los modelos (ej: escalados, codificados).

### `2_models/`
- **Propósito**: Guardar los objetos de los modelos entrenados y serializados.
- **Artefactos**:
    - `Modelos serializados`: Archivos `.pkl`, `.h5`, `.rds`, `.joblib`, etc. Esto permite cargar los modelos para evaluación o despliegue sin necesidad de reentrenar.

---
### ⚠️ **Nota de Seguridad Importante**
**NUNCA** subas datos sensibles, confidenciales o personales a repositorios de Git, especialmente si son públicos. Utiliza el archivo `.gitignore` para excluir estos archivos del control de versiones.
