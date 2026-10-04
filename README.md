# RecyclAIDeep — Aplicación de Reciclaje Inteligente

> Aplicación móvil que utiliza inteligencia artificial para detectar y clasificar residuos reciclables mediante visión por computadora.
> Proyecto desarrollado como parte de la **tesis profesional** en Ingeniería Civil Informático, Universidad del Bío-Bío.

[![React Native](https://img.shields.io/badge/React_Native-61DAFB?style=flat-square&logo=react&logoColor=black)](https://reactnative.dev/)
[![Expo](https://img.shields.io/badge/Expo-000000?style=flat-square&logo=expo&logoColor=white)](https://expo.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![YOLOv5](https://img.shields.io/badge/YOLOv5-1a73e8?style=flat-square)](https://github.com/ultralytics/yolov5)

<!--
## Capturas
Coloca las imágenes en `docs/screenshots/` y descomenta:

![Detección en tiempo real](docs/screenshots/deteccion.png)
![Mapa de puntos limpios](docs/screenshots/mapa.png)
![Resultado y recompensa](docs/screenshots/resultado.png)
-->

---

## Características

- **Detección en tiempo real:** usa la cámara para identificar residuos reciclables.
- **Clasificación inteligente:** detecta botellas, latas, cajas, papel, vidrio y más (6 clases: cartón, metal, papel, pilas, plástico, vidrio).
- **Modo Online/Offline:** funciona contra la API backend o con el modelo local en el dispositivo.
- **Mapa de puntos limpios:** encuentra centros de reciclaje cercanos.
- **Sistema de recompensas:** gamificación para incentivar el reciclaje.
- **Interfaz moderna:** UI/UX con React Native y Expo Router.

## Stack tecnológico

### Frontend
- **React Native** con Expo Router
- **TypeScript** para tipado seguro
- **TensorFlow.js / TFLite** para predicción offline en el dispositivo
- **React Native Maps** para geolocalización
- **Expo Camera** para captura de imágenes

### Backend (modo online)
- **FastAPI** (Python) como API REST
- **YOLOv5** para detección de objetos (entrenamiento en [Repositorio_Tesis](https://github.com/FranciscoAguilarCuadra/Repositorio_Tesis))
- **PyTorch** y **OpenCV** para procesamiento de ML e imágenes

> **Nota:** los pesos de los modelos (`best.pt`, `best_float16.tflite`) no están incluidos por tamaño; la guía de configuración está en [SETUP_MODELS.md](SETUP_MODELS.md). El código del servidor FastAPI se configura en el directorio `api/backend/model/` descrito allí.

## Correr la app en local

### Requisitos
- Node.js ≥ 18
- Expo Go en el celular (o emulador Android/iOS)

### Frontend

```bash
git clone https://github.com/FranciscoAguilarCuadra/APP_Tesis_rec.git
cd APP_Tesis_rec
npm install
npm run update-ip   # apunta la app a la IP de tu máquina
npm run dev         # escanear QR con Expo Go
```

### Backend y modelos
Sigue [SETUP_MODELS.md](SETUP_MODELS.md) para configurar el modelo YOLOv5 (backend) y los modelos TFLite/TFJS (offline).

```bash
uvicorn main:app --host 0.0.0.0 --port 5000
```

## Estructura del proyecto

```
APP_Tesis_rec/
├── app/            # Pantallas (Expo Router, navegación por pestañas)
├── assets/         # Imágenes y modelos ML (no incluidos, ver SETUP_MODELS.md)
├── components/     # Componentes reutilizables
├── constants/      # Configuración (API_URL, etc.)
├── data/           # Datos de apoyo
├── hooks/          # Hooks personalizados
├── services/       # Lógica de API y ML
├── scripts/        # Scripts de mantenimiento
└── utils/          # Utilidades
```

## Despliegue

- **Frontend:** builds con [EAS](https://docs.expo.dev/build/introduction/) (`eas build`) para Android/iOS.
- **Backend:** Docker o servidor cloud (AWS/GCP). Ver comandos en [SETUP_MODELS.md](SETUP_MODELS.md).

## Modelos y experimentación

El entrenamiento y la comparación de los tres modelos (YOLOv5, Faster R-CNN, DETR) está documentado en **[Repositorio_Tesis](https://github.com/FranciscoAguilarCuadra/Repositorio_Tesis)**.

## Autor

**Francisco Aguilar Cuadra** — Ingeniero Civil Informático, Universidad del Bío-Bío (2025)
[GitHub](https://github.com/FranciscoAguilarCuadra) · [LinkedIn](https://linkedin.com/in/francisco-aguilar-cuadra)
