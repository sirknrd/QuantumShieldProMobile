# Mobile Trading Terminal (APK) — Kivy

Esta carpeta contiene una versión **nativa móvil** del terminal (sin Streamlit), pensada para compilarse como **APK** usando **Kivy + python-for-android**.

## Qué incluye (MVP funcional)
- Pantalla tipo “terminal” con:
  - Ticker + timeframe
  - Recomendación (Compra/Venta/Neutral) con color
  - KPIs (Último, % cambio, RSI, ADX, ATR%)
  - Panel “Técnicos multi‑timeframe” (1D/4H/1H/15m) con consenso
- Datos de mercado desde **Yahoo Finance (endpoint JSON)**, sin `yfinance`.
- Indicadores calculados con **NumPy** (sin `pandas`), para que el APK sea viable.

## Requisitos de build (Windows)
Compilar APK desde Windows se hace normalmente con:
- **WSL2 (Ubuntu)** recomendado, o
- Linux nativo.

## Build rápido (WSL2 / Ubuntu)
1) Instala dependencias de sistema:

```bash
sudo apt update
sudo apt install -y python3 python3-pip git zip unzip openjdk-17-jdk \
  build-essential autoconf automake libtool pkg-config \
  zlib1g-dev libncurses5-dev libncursesw5-dev libtinfo5 cmake \
  libffi-dev libssl-dev
```

2) Crea venv e instala buildozer:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install buildozer cython==0.29.36
```

3) Entra a esta carpeta y compila:

```bash
cd mobile_terminal
buildozer android debug
```

El APK quedará en `mobile_terminal/bin/`.

## Ejecutar en PC (modo dev)
En Windows puedes probar la UI con:

```powershell
python -m pip install -r mobile_terminal\requirements-dev.txt
python mobile_terminal\main.py
```

