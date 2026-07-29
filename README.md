# Django + DataTables + Binance API

Aprende a utilizar la librería DataTables.js para crear tablas dinámicas y mostrar datos leídos desde una aplicación backend (API) creada con Python y Django. Conoce cómo utilizar el framework web Django para proveer datos que se mostrarán en una DataTable (usando DataTables.js de jQuery), e integrando los precios en tiempo real desde la API de Binance.

<hr/>

## Pasos para iniciar la aplicación

Sigue estos pasos para levantar el entorno localmente y hacer funcionar el proyecto.

### 1. Clonar el repositorio
Si aún no lo has hecho, clona el repositorio en tu máquina local:
```bash
git clone <url-del-repositorio>
cd <nombre-de-la-carpeta>
```

### 2. Crear y activar un entorno virtual
Se recomienda el uso de entornos virtuales para evitar conflictos con otras dependencias en tu sistema.
```bash
# Crear entorno virtual
python -m venv env

# Activar el entorno virtual (Windows)
env\Scripts\activate

# Activar el entorno virtual (Linux/macOS)
source env/bin/activate
```

### 3. Instalar las dependencias
Instala todas las librerías necesarias ejecutando el siguiente comando:
```bash
pip install -r requirements.txt
```
*(Nota: El archivo `requirements.txt` ya incluye dependencias importantes como `Django`, `python-binance` y `requests`).*

### 4. Configurar las claves de la API de Binance (Opcional pero Recomendado)
El proyecto utiliza la API de Binance para obtener los precios de las criptomonedas.
Puedes encontrar la configuración de las credenciales en el archivo `app/binance_api.py`.
```python
API_KEY = 'TU_API_KEY'
API_SECRET = 'TU_API_SECRET'
```
*Si tienes problemas de conexión (por ejemplo, errores de restricción geográfica "Service unavailable from a restricted location"), asegúrate de que tus claves API estén habilitadas y que tu IP permita consultas a la API global de Binance.*

### 5. Configurar la Base de Datos
Antes de levantar la aplicación, necesitas preparar la base de datos (SQLite por defecto).
```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Ejecutar el servidor de desarrollo
Finalmente, levanta el servidor de Django:
```bash
python manage.py runserver
```

Una vez que el servidor esté corriendo, puedes acceder a la aplicación desde tu navegador en la dirección:
[http://127.0.0.1:8000/](http://127.0.0.1:8000/)

## Endpoints de la API de Binance disponibles en el proyecto:
- `http://127.0.0.1:8000/app/get_binance_prices/`: Obtiene los precios de un conjunto de criptomonedas.
- `http://127.0.0.1:8000/app/get_binance_crypto_info/<symbol>/`: Obtiene información específica para el símbolo dado (ej: `BTCUSDT`).
