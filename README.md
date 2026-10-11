# 🤖 Bot de Telegram para automatizar novedades con Python

![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)
![Requests](https://img.shields.io/badge/Requests-HTTP-2C5BB4)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-web%20scraping-4B8BBE)
![Telegram](https://img.shields.io/badge/Telegram-Bot%20API-26A5E4?logo=telegram&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white)
![License](https://img.shields.io/badge/licencia-MIT-blue)

Práctica de **automatización de tareas con Python**: se extraen datos de una página web (*web scraping*) y se envían de forma automática a un chat de **Telegram** mediante un bot.

> 📓 **El paso a paso está en [`notebooks/automatizacion_telegram.ipynb`](./notebooks/automatizacion_telegram.ipynb)**

---

## ¿Qué hace?

| Paso | Qué se resuelve |
|------|-----------------|
| 🌐 Descarga | Obtiene el HTML de una página con `requests` |
| 🔎 Extracción | Interpreta el HTML con `BeautifulSoup` y selecciona los elementos de interés |
| 🧹 Limpieza | Elimina repetidos usando `set` |
| 📨 Notificación | Envía los resultados a Telegram con la API de bots (`sendMessage`) |
| ⏱️ Automatización | Repite el proceso cada cierto tiempo con un bucle y `sleep` (por ejemplo, cada 24 hs) |

## Ejemplos incluidos en el notebook

1. **Novedades de recitales** en Buenos Aires: extrae los shows de una página de conciertos y los manda al chat.
2. **Búsqueda de alquileres**: extrae los departamentos de un listado inmobiliario.
3. **Ofertas del día**: extrae precios de un listado de productos.

## Estructura del repositorio

```
bot-telegram-novedades/
├── README.md
├── LICENSE
├── requirements.txt
├── .env.example                      # plantilla de credenciales (el .env real NO se sube)
├── .gitignore
└── notebooks/
    └── automatizacion_telegram.ipynb # el paso a paso
```

## Cómo ejecutarlo

**Requisitos:** Python 3.9+, Git y una cuenta de Telegram.

### 1. Clonar e instalar

```
git clone https://github.com/Jeanette22/bot-telegram-novedades.git
cd bot-telegram-novedades

python -m venv .venv
.venv\Scripts\Activate.ps1      # Windows (PowerShell)
source .venv/bin/activate       # macOS / Linux

pip install -r requirements.txt
```

### 2. Crear tu bot de Telegram

1. En Telegram, buscá a **@BotFather** y creá un bot con el comando `/newbot`. Te entrega un **token**.
2. Escribile un mensaje a tu bot y obtené tu `chat_id` consultando `getUpdates` (el notebook lo muestra).
3. Copiá `.env.example` como `.env` y completá tus datos.

> ⚠️ **Nunca escribas el token en el código ni lo subas a GitHub.** Quien lo tenga puede controlar tu bot. El archivo `.env` está en `.gitignore` justamente para evitarlo. En el notebook, `bot_token` y `chat_id` aparecen con marcadores (`xxxx`) que tenés que reemplazar con tus datos al ejecutarlo en tu equipo.

### 3. Abrir el notebook

Abrí `notebooks/automatizacion_telegram.ipynb` en VS Code (con la extensión *Jupyter*) y elegí como *kernel* el entorno `.venv`.

## Qué aprendí / conceptos aplicados

- Cómo funciona una página web: HTML, etiquetas y clases CSS.
- Descargar y navegar HTML con `requests` y `BeautifulSoup`.
- Consumir una API REST (Telegram Bot API) con peticiones `GET` y `POST`.
- Crear funciones reutilizables (`send_msg`) y bucles de ejecución periódica.
- Manejo de credenciales: por qué los tokens no van en el código.

## Notas y limitaciones

- Es una **práctica de aprendizaje**, realizada en un taller del Instituto Humai y desarrollada originalmente en Deepnote (Python 3.7).
- Los ejemplos apuntan a páginas concretas de 2022. Los sitios cambian su HTML con el tiempo, así que los selectores pueden necesitar ajustes.
- Antes de extraer datos de un sitio, revisá sus **términos de uso** y su archivo `robots.txt`.
- Para dejar el bot corriendo de forma permanente se necesita un servidor o servicio en la nube (por ejemplo Heroku o Replit); en local solo funciona mientras la computadora esté encendida.

## Cómo contribuir

¡Las sugerencias son bienvenidas! Este proyecto es parte de mi proceso de aprendizaje.

1. Hacé un **fork** del repositorio.
2. Creá una rama: `git checkout -b feat/mi-mejora`
3. Hacé tus cambios y sus commits: `git commit -m "feat: descripción del cambio"`
4. Subí la rama: `git push origin feat/mi-mejora`
5. Abrí un **Pull Request** explicando qué cambia y por qué.

**Ideas para colaborar:** pasar el código a un script `.py` con credenciales en `.env`, sumar manejo de errores, o programar la ejecución con `schedule` o GitHub Actions.

## Autora

**Jeanette Mansilla** · [Portfolio](https://jeanettemansilla.netlify.app/) · [LinkedIn](https://www.linkedin.com/in/jeanettemansilla/) · [Tableau Public](https://public.tableau.com/app/profile/jeanettecrd/vizzes)

Distribuido bajo licencia MIT. Ver [`LICENSE`](./LICENSE).
