**Nombre del proyecto:** ¿Qué comemos hoy?
Este proyecto desarrolla un Proof of Concept (POC) para una herramienta que genera recetas personalizadas e imágenes ilustrativas a partir de ingredientes disponibles en casa. Usando APIs gratuitas y técnicas de Fast Prompting, el objetivo es demostrar cómo la inteligencia artificial puede facilitar la cocina diaria.

## Presentación del problema a abordar
Cada día, millones de personas se enfrentan a la pregunta: "¿Qué comemos hoy?". Al revisar la heladera, encuentran ingredientes que parecen no combinar, lo que lleva a desperdiciar comida, tiempo y dinero. Además, la falta de ideas fomenta la repetición de comidas o compras innecesarias. Este problema es relevante porque afecta la economía doméstica y la sostenibilidad, y una solución tecnológica podría transformar esta experiencia cotidiana en algo creativo, eficiente y accesible.

## Desarrollo de la propuesta de solución
La solución propuesta utiliza dos modelos de IA:
1. **Generación de recetas (texto)**: A través de la API de TheMealDB, se buscan recetas basadas en un ingrediente principal ingresado por el usuario (ej. "pollo"). La respuesta se traduce al español para mayor accesibilidad.
2. **Generación de imágenes**: Usando Stable Diffusion de Hugging Face, se crea una imagen realista del plato propuesto (ej. "pollo con espinaca y queso gratinado").

Los prompts se diseñaron con técnicas de Fast Prompting para minimizar consultas a las APIs (una por receta, una por imagen), optimizando recursos y cumpliendo con los límites gratuitos.

## Justificación de la viabilidad del proyecto
- **Técnica**: El proyecto usa APIs gratuitas (TheMealDB y Hugging Face), accesibles sin costo y con documentación clara. No requiere infraestructura propia.
- **Tiempo**: El POC se desarrolló en pocos días usando Google Colab, lo que demuestra que una implementación básica es rápida.
- **Recursos**: Solo se necesita un navegador, una cuenta en Hugging Face para el token, y GitHub para el repositorio. Los límites de las APIs gratuitas (100-200 solicitudes/día en Hugging Face) son suficientes para pruebas.

**Limitaciones**: TheMealDB no genera recetas nuevas ni siempre coincide con todos los ingredientes ingresados, pero esto se compensa con la imagen personalizada de Stable Diffusion.

## Objetivos
1. Demostrar que la IA puede sugerir recetas útiles a partir de ingredientes disponibles.
2. Generar imágenes ilustrativas que complementen las recetas.
3. Optimizar el uso de APIs gratuitas, limitando las consultas a dos por ejecución.
4. Crear un POC funcional y replicable en Google Colab.

- **Procedimiento**:
  1. **Ingreso de ingredientes**: El usuario proporciona una lista (ej. "pollo, espinaca, queso").
  2. **Búsqueda de receta**: Se consulta TheMealDB con el ingrediente principal y se traduce la respuesta al español.
  3. **Generación de imagen**: Se envía un prompt a Stable Diffusion con la combinación de ingredientes.
  4. **Pruebas**: Se probaron combinaciones como "carne, papa, cebolla" para validar la flexibilidad.
- **Justificación**: Este enfoque modular simplifica el desarrollo y reduce consultas innecesarias, alineándose con la consigna de optimización.

## Herramientas y tecnologías
- **Google Colab**: Plataforma gratuita para ejecutar el código en la nube.
- **TheMealDB API**: Fuente gratuita de recetas estructuradas (texto).
- **Hugging Face Stable Diffusion**: API gratuita para generación de imágenes (requiere token).
- **Fast Prompting**: Prompts directos y específicos (ej. "Imagen realista de pollo con espinaca y queso gratinado") para evitar iteraciones.
- **Python**: Lenguaje usado con bibliotecas como `requests` y `IPython.display`.

**Justificación**: Estas herramientas son gratuitas, fáciles de usar y adecuadas para un POC académico.

## Implementación
El código está disponible en este repositorio como `Recetas_IA_POC.ipynb`. Ejemplo de uso:
```python
ingredientes = ["pollo", "espinaca", "queso"]
print("Generando receta...")
receta = buscar_receta(ingredientes)
print(receta)
print("\nGenerando imagen...")
generar_imagen("pollo con espinaca y queso gratinado")
