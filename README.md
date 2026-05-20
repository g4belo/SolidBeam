# SolidBeam: Active Phased Array Dynamic Radar

> **Status do Projeto:** Marco 1 — Em fase de simulação computacional.

---

## 📝 Descrição do Projeto

O **SolidBeam** é um sistema ciberfísico de radar de estado sólido (*solid-state*) baseado em um arranjo de antenas planas em fase (**Active Phased Array**). O objetivo principal do projeto é o rastreamento espacial e a predição de trajetórias de alvos dinâmicos em tempo real, eliminando completamente qualquer atuação mecânica ou parte móvel. 

O direcionamento do feixe eletromagnético (tanto em azimute quanto em elevação) é feito exclusivamente por software através da manipulação e calibração de fase em picossegundos.

---

## 🛠️ Arquitetura e Engenharia do Sistema

O projeto é dividido em três pilares fundamentais de desenvolvimento:

### 1. Hardware e Radiofrequência (RF)
* **Frequência Central:** $2,4\text{ GHz}$ (Comprimento de onda $\lambda = 12,5\text{ cm}$).
* **Geometria do Arranjo:** Matriz planar $2 \times 2$ de antenas patch espaçadas por $\lambda/2$ ($6,25\text{ cm}$).
* **Atuação Eletromagnética:** Divisor de potência Wilkinson integrado a 4 chips defasadores digitais controlados via barramento SPI de alta velocidade.

### 2. Firmware e Processamento Embarcado (ESP32-S3)
* **Modulação FMCW:** Geração artificial da rampa de frequência (*chirp*) controlando o sintetizador de RF.
* **Processamento Digital de Sinais (DSP):** Janelamento de sinal, FFT para extração de distância/velocidade e algoritmo CA-CFAR para rejeição de ruído de fundo (*clutter*).
* **Estimação de Estados:** Implementação de um **Filtro de Kalman Estendido (EKF)** para linearização e predição da trajetória balística em coordenadas cartesianas.

### 3. Interface de Telemetria e Visualização 3D
* **Ambiente Virtual:** Interface em Python para receber a nuvem de pontos (*point cloud*) via sockets UDP/Wi-Fi.
* **Validação Gráfica:** Renderização em tempo real do cone de varredura do radar, sobrepondo a trajetória real do alvo com a linha de predição gerada pelo EKF.

---

## 📈 Estrutura de Diretórios (Workspaces)

* `/simulation` — Scripts em Python para modelagem eletromagnética do Phased Array 2D e do EKF.
* `/firmware` — Código em C/C++ para o ESP32-S3 usando a estrutura do ESP-IDF / FreeRTOS.
* `/hardware` — Arquivos de CAD e roteamento de RF das PCBs (KiCAD).
* `/telemetry` — Interface gráfica 3D para plotagem das trajetórias em tempo real.

---

## 🚀 Ferramentas Utilizadas no Desenvolvimento

* **Simulação/Interface:** Python 3 (NumPy, SciPy, PyQtGraph/Open3D)
* **Firmware:** C/C++ (ESP-IDF)
* **CAD/PCB:** KiCAD 8.0
* **Gestão de Tarefas:** Notion (Quadro Kanban)

---

## 📖 Diário de Bordo e Mudanças de Escopo

As tomadas de decisão técnicas, correções de impedância, calibrações de firmware e logs de desenvolvimento estão documentados detalhadamente no arquivo [RESEARCH_LOG.md](RESEARCH_LOG.md).
