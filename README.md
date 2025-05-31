# Tesis: Time-Space Complexity on Edge vs Cloud para Video-Text Prediction

Este repositorio contiene todo el código, datos y documentación complementaria de la tesis titulada:

> **Time-Space Complexity on Edge vs Cloud Computing for Real-Time Video Text Prediction**  
> Autor: Sebastian Dulong Salazar  
> Repositorio: https://github.com/dulongski/tesis

---

## Descripción

En esta tesis se estudia y compara el rendimiento (precisión, latencia y uso de recursos) de dos esquemas de procesamiento de video a texto en tiempo real:

1. **Edge (Raspberry Pi 4 + Vosk + Regresión de Poisson)**  
   - Un sistema embarcado que emplea Vosk para transcribir audio localmente y un regresor de Poisson sencillo para predecir la aparición futura de palabras clave.  
   - Ventajas: latencia muy baja (ms por segundo de video), independencia de la red y costo cero en infraestructura.  
   - Desventajas: precisión limitada comparada con modelos grandes, alta carga en CPU de la Raspberry Pi.

2. **Cloud (Google Colab con GPU T4 + Whisper + DistilBERT)**  
   - Un pipeline en la nube que utiliza Whisper (OpenAI) para la transcripción y DistilBERT fine-tuneado como regresor multisalida de conteos.  
   - Ventajas: mayor precisión en transcripción y predicción, escalabilidad de modelos complejos.  
   - Desventajas: requiere GPU, latencias totales alrededor de decenas de ms por segundo de video, dependencia de conexión y posible costo en infraestructuras de pago.

El caso de estudio se basa en discursos de Donald Trump: dos videos para entrenamiento (Discurso Inaugural 2017 y Discurso sobre Bitcoin) y un video de prueba (Discurso del 30 de mayo de 2020 en Pittsburgh).

---

## Estructura del repositorio

```

tesis/
├── .gitignore
├── README.md
├── requirements.txt
├── modelos\_edge/
├── vosk-model-small-en-us-0.15/
├── model\_edge.ipynb
├── cloud\_model.ipynb
├── stats\_edge\_results.csv
├── trump1.mp4 / trump1.wav / trump1.txt
├── trump2.mp4 / trump2.wav / trump2.txt
├── trump3.mp4 / trump3.wav / trump3.txt
└── Imagenes/
├── comparacion\_mae.png
├── comparacion\_rmse.png
├── comparacion\_latencia.png
├── comparacion\_latencia\_edge\_cloud.png
├── esquema\_modelo.png
└── trumpspeech.png

````

---

## Instalación de dependencias

```bash
git clone https://github.com/dulongski/tesis.git
cd tesis
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
````

> ⚠️ Whisper requiere GPU para funcionar eficientemente. Ejecutarlo en CPU puede tardar mucho.

---

## Uso de los notebooks

### `model_edge.ipynb`

* Entrena un modelo de regresión de Poisson con trump1 y trump3.
* Usa Vosk para transcribir trump2.
* Simula predicción palabra a palabra.
* Guarda métricas en `stats_edge_results.csv`.

### `cloud_model.ipynb`

* Usa Whisper para transcribir trump1 y trump3.
* Fine-tunea DistilBERT para regresión multisalida.
* Evalúa sobre trump2.
* Guarda métricas en `stats_cloud_results.csv`.

---


## Cómo citar este repositorio

```bibtex
@misc{tesis_dulongski_2025,
  author       = {Sebastian Dulong Salazar},
  title        = {{Time-Space Complexity on Edge vs Cloud Computing for Real-Time Video Text Prediction}},
  year         = {2025},
  howpublished = {\url{https://github.com/dulongski/tesis}}
}
```

---

## Licencia

MIT © Sebastian Dulong Salazar

---

## Contacto

📬 [sebastian.dulong@itam.mx](mailto:sebastian.dulong@correo.edu)
📎 [https://github.com/dulongski/tesis](https://github.com/dulongski/tesis)
