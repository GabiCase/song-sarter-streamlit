# 🎵 Song Starter 🎵

Song Starter es una aplicación que genera nuevas canciones inspiradas en canciones existentes. Utiliza APIs de **Spotify**, **OpenAI**, y **Pinecone** para analizar canciones y generar acordes, letras y características armónicas similares.

## Características principales

1. **Recomendación de canciones similares**: A partir de una canción dada, la app sugiere canciones con acordes y características armónicas parecidas.
2. **Generación de letras y acordes**: Utilizando OpenAI, se generan nuevas letras y progresiones de acordes basadas en las canciones de referencia.
3. **Análisis de características de audio**: Incluye análisis de tempo, loudness, speechiness, y otros detalles extraídos de Spotify.
4. **Almacenamiento y búsqueda en Pinecone**: La app utiliza Pinecone para guardar las canciones y sus características en un formato vectorial, lo que permite búsquedas rápidas por similitud.

## Flujo de trabajo

1. **Entrada del usuario**: El usuario introduce una canción y un artista.
2. **Búsqueda de canciones similares**: Se obtiene un `track_id` de la API de Spotify y se buscan canciones similares.
3. **Generación de acordes y letras**:
   - Se genera una nueva progresión de acordes.
   - Se generan letras basadas en el tema de la canción original.
4. **Análisis vectorial en Pinecone**: Se comparan los resultados con una base de datos de canciones previamente analizadas para ofrecer recomendaciones más precisas.

## Instalación

1. Clona el repositorio:

    ```bash
    git clone https://github.com/tu_usuario/song-starter.git
    ```

2. Instala las dependencias:

    ```bash
    pip install -r requirements.txt
    ```

3. Configura las variables de entorno:

    Crea un archivo `.env` con las claves necesarias:

    ```bash
    SPOTIFY_CLIENT_ID=tu_spotify_client_id
    SPOTIFY_CLIENT_SECRET=tu_spotify_client_secret
    OPENAI_API_KEY=tu_openai_api_key
    PINECONE_API_KEY=tu_pinecone_api_key
    ```

4. Ejecuta la aplicación:

    ```bash
    streamlit run app.py
    ```

## Requisitos

- **Python 3.8** o superior.
- Claves de API de **Spotify**, **OpenAI** y **Pinecone**.

## Descripción del código

- **app.py**: Archivo principal que controla el flujo de la aplicación.
  - Recoge la entrada del usuario.
  - Llama a funciones que buscan canciones similares, generan acordes, letras, y analizan las características de las canciones.
  
- **utils/**: Contiene varios módulos auxiliares para gestionar las diferentes funcionalidades:
  - `chat_gpt_manager.py`: Funciones para interactuar con OpenAI (generación de letras y acordes).
  - `spotify_manager.py`: Funciones para interactuar con la API de Spotify (obtener `track_id`, análisis de audio, recomendaciones).
  - `functions.py`: Funciones adicionales para manipulación de datos (normalización de acordes, transposición, etc.).
  - `pinecone_manager.py`: Inicialización y configuración de Pinecone.
  - `streamlit_manager.py`: Gestión de entradas del usuario en Streamlit.
  - `lyrics_manager.py`: Inserción de letras en la base de datos.
  
## Ejemplo de uso

1. **Introduce una canción y artista**: Elige una canción que te guste para recibir recomendaciones.
2. **Obtén canciones similares**: La aplicación buscará canciones con acordes y características similares.
3. **Genera nueva música**: Se generarán acordes y letras nuevas inspiradas en las canciones de referencia.
4. **Consulta de características**: Obtén información detallada como tempo, acordes, instrumentos y temas líricos.
