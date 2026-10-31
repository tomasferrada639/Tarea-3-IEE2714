# Tarea 3 - IEE2714: Fundamentos de Procesamiento de Imágenes

**Estudiante:** Tomás Ferrada Contreras  
**Profesor:** Carlos Milovic  
**Fecha:** 30 de octubre de 2026  

## Descripción General
Este directorio contiene los archivos correspondientes a la entrega de la Tarea 3 del curso Fundamentos de Procesamiento de Imágenes. La tarea aborda dos problemas fundamentales del procesamiento en el dominio de la frecuencia:

1. **Filtrado Notch de ruido periódico:** eliminación de patrones periódicos en una imagen RAW (`.CR2`) mediante filtros notch ideales y gaussianos, con estudio del efecto del padding y un bonus de optimización automática del ancho del filtro.
2. **Deconvolución regularizada:** restauración de imágenes degradadas por convolución con una PSF conocida, implementando el filtro de Wiener, la regularización de Tikhonov resuelta por descenso de gradiente y el método de Landweber, incluyendo análisis de sensibilidad ante PSF incorrectas.

## Estructura de la Entrega

*   **`Tarea3_IEE2714.pdf` (Informe):** Contiene toda la justificación teórica, el análisis matemático, la interpretación de los resultados experimentales y las respuestas a las preguntas guiadas del enunciado.
*   **`Tarea3_IEE2714.ipynb` (Jupyter Notebook):** Contiene todo el código fuente en Python, incluyendo la definición de las funciones solicitadas y los bloques de experimentación. Al ejecutarlo de principio a fin se reproducen todas las figuras y tablas del informe.
*   **`repositorio_tarea3.zip` (Repositorio):** Archivo comprimido con el repositorio completo, incluyendo las imágenes de entrada (`data/`), las figuras generadas (`figs/`) y los resultados intermedios (`resultados/`).

## Instrucciones de Ejecución

El código ha sido estructurado en un único Jupyter Notebook para facilitar su revisión y evaluación. Está diseñado para ejecutarse de principio a fin sin requerir configuraciones adicionales.

Para ejecutar el código:
1. Descomprima `repositorio_tarea3.zip` y abra `Tarea3_IEE2714.ipynb` en su entorno de preferencia (Jupyter Notebook, JupyterLab, VS Code, Google Colab, etc.).
2. Asegúrese de contar con las siguientes librerías de Python:
   ```
   pip install numpy scipy matplotlib pillow rawpy jupyter
   ```
   Si `rawpy` no está disponible, el notebook utiliza automáticamente `libraw` mediante `ctypes` como alternativa (`sudo apt install libraw-dev` en Ubuntu/Debian).
3. En el menú superior de su entorno, seleccione la opción **"Run All"** (Ejecutar todo) o reinicie el kernel y ejecute todas las celdas secuencialmente.

El *notebook* se encargará de leer la imagen RAW, ejecutar los filtros, procesar las imágenes y generar todas las figuras referenciadas en el informe. Tiempo aproximado: 8-10 minutos (la imagen RAW es de 2856 × 4290 píxeles). La primera ejecución guarda la imagen en gris en `resultados/P1_gris.npy`; las siguientes la reutilizan.




