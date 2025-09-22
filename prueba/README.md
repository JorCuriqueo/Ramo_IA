# Sistema de Consultas Inteligentes para Clínica VitalCare

Este proyecto implementa una solución integral basada en agentes LLM y pipelines RAG para responder consultas frecuentes de pacientes en la clínica médica ficticia "Clínica VitalCare", optimizando tiempos y mejorando la experiencia del usuario.

## Descripción
-- **Organización:** Clínica VitalCare (ficticia, inspirada en clínicas reales)
- **Rubro:** Salud, atención médica ambulatoria
- **Problema:** Muchas consultas repetitivas sobre síntomas, medicamentos, horarios y procedimientos generan sobrecarga en el personal.
- **Solución:** Chatbot con recuperación aumentada (RAG) y LLM, que responde consultas usando documentos internos.

## Características
- Recuperación híbrida de información (embeddings + keywords)
- Métricas de calidad: fidelidad, relevancia y precisión de contexto
- Dashboard de métricas y exportación de resultados
- Edición y gestión de documentos internos
- Chatbot interactivo

## Explicación de Métricas
La aplicación evalúa la calidad de las respuestas usando las siguientes métricas:

- **Fidelidad:** Indica si la respuesta está basada únicamente en la información de los documentos internos. Un valor alto significa que la respuesta es precisa y no inventa información.
- **Relevancia:** Mide qué tan útil y pertinente es la respuesta respecto a la consulta realizada por el usuario.
- **Precisión de contexto:** Representa la proporción de documentos recuperados que realmente ayudan a responder la consulta, mostrando la capacidad del sistema para seleccionar información relevante.

Estas métricas permiten monitorear y mejorar el desempeño del sistema, asegurando que las respuestas sean confiables y útiles para los usuarios.

## Interfaz: Tabs y Funcionalidad
La aplicación cuenta con varias pestañas (tabs) en la interfaz web, cada una con una función específica:

1. **Consulta**
    - Permite al usuario realizar preguntas sobre salud, horarios, procedimientos y otros temas relacionados con la clínica.
    - Muestra los documentos utilizados para responder, la respuesta generada y métricas de calidad.
    - **Importante:** Antes de enviar una pregunta, es necesario generar los embeddings de los documentos internos usando el botón correspondiente.
       - **¿Por qué es necesario este paso?** Los embeddings permiten que el sistema represente el significado de los documentos en un formato que el modelo puede comparar con la consulta del usuario. Así, el sistema puede identificar qué documentos son más relevantes para responder la pregunta, mejorando la precisión y calidad de la respuesta generada por el asistente.

2. **Documentos**
   - Permite visualizar, editar, eliminar y agregar documentos internos (protocolos, guías, preguntas frecuentes, etc.).
   - Se pueden importar archivos de texto y ver estadísticas de los documentos.

3. **Métricas**
   - Presenta un dashboard con métricas de rendimiento y calidad de las consultas realizadas.
   - Incluye gráficos de tiempos de respuesta, distribución de fidelidad, relevancia y precisión de contexto.

4. **Evaluación**
   - Ejecuta una evaluación sistemática del sistema usando un conjunto de preguntas frecuentes simuladas.
   - Muestra los resultados y métricas promedio de la evaluación.

5. **Analytics**
   - Permite exportar los datos de interacción en formato JSON (para LangSmith) o CSV.
   - Muestra insights sobre los documentos, como distribución de longitud y palabras más frecuentes.

6. **Chatbot**
   - Ofrece un asistente virtual para consultas libres, con ajuste de temperatura y registro de mensajes.
   - Incluye una barra para ajustar la temperatura de la respuesta, permitiendo que el asistente sea más amigable o más serio según la preferencia del usuario.

## Requisitos
- Python 3.10+
- Instalar dependencias:
   ```bash
   pip install streamlit python-dotenv openai pandas numpy scikit-learn plotly langchain langchain-openai
   ```
- Archivo `.env` con la variable `GITHUB_TOKEN` (API Key de OpenAI/Azure)

   Ejemplo de archivo `.env`:
   ```
   GITHUB_TOKEN=tu_api_key_aqui
   GITHUB_BASE_URL=https://models.inference.ai.azure.com
   OPENAI_API_KEY=tu_api_key_aqui
   OPENAI_API_BASE=https://models.inference.ai.azure.com
   ```

## Ejecución
1. Clona el repositorio desde GitHub usando el siguiente comando:
   ```bash
   git clone https://github.com/usuario/tu-repositorio.git
   ```
   Luego entra a la carpeta del proyecto.
2. Cambia a la carpeta `prueba`:
   ```bash
   cd prueba
   ```
3. (Opcional pero recomendado) Crea un entorno virtual:
   ```bash
   python -m venv .venv
   ```
4. Activa el entorno virtual:
   - En **Windows**:
     ```bash
     .venv\Scripts\activate
     ```
   - En **Linux/Mac**:
     ```bash
     source .venv/bin/activate
     ```
3. Instala las dependencias.
4. Crea el archivo `.env` con tu API Key:
   ```
   GITHUB_TOKEN=tu_api_key_aqui
   ```
5. Ejecuta la aplicación:
   ```bash
   streamlit run prueba.py
   ```
6. Accede a la interfaz web para realizar consultas, editar documentos y visualizar métricas.

## Estructura del Proyecto
- `prueba.py`: Código principal de la aplicación Streamlit
- `.env`: Variables de entorno (no compartir públicamente)
- `README.md`: Documentación e instrucciones del proyecto

## Documentos Simulados
El sistema incluye ejemplos de protocolos médicos, preguntas frecuentes, horarios y políticas de privacidad de Clínica VitalCare. Puedes agregar, editar o importar nuevos documentos desde la interfaz.

## Uso Ético y Declaración de IA
-- El sistema utiliza OpenAI y LangChain para procesamiento de lenguaje y recuperación.
-- Se utilizó GitHub Copilot y ChatGPT como apoyo para la generación de código, redacción y solución de dudas técnicas.
-- Todas las ideas y justificaciones técnicas deben ser propias del equipo.
-- Cita el uso de IA según normativa APA.

## Referencias
- [Documentación LangChain](https://python.langchain.com/docs/)
- [Documentación OpenAI API](https://platform.openai.com/docs/)

## Contacto y Soporte
Para dudas técnicas, contacta al equipo desarrollador o revisa la documentación interna.

---

> Proyecto desarrollado para la Evaluación Parcial N°1 - Subdirección de Diseño Instruccional, 2025.
