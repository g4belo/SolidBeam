# SolidBeam — Research Log & Diário de Bordo

Este arquivo serve para registrar as tomadas de decisão de engenharia, problemas de física/RF encontrados e as respectivas soluções adotadas durante o desenvolvimento do TCC.

---

## [Semana 1] — Definição de Escopo e Arquitetura Matemática

### 1. Objetivos da Semana
* Estruturar o repositório com o padrão modular.
* Iniciar a modelagem matemática do Phased Array Planar $2 \times 2$.

### 2. Decisões de Engenharia Tomadas
* **Frequência de Operação:** Fixada em $2,4\text{ GHz}$ ($\lambda = 12,5\text{ cm}$) para balancear a viabilidade de fabricação da PCB com o tamanho prático do alvo.
* **Geometria:** Espaçamento rígido de $\lambda/2 = 6,25\text{ cm}$ para evitar lóbulos de grade (*grating lobes*) e garantir o foco do feixe.
* **Hardware:** Substituição de motores mecânicos por chips defasadores digitais controlados via SPI no ESP32-S3.

### 3. Problemas Encontrados & Próximos Desafios
* **Desafio Próximo:** Modelar a equação do *Array Factor* (Fator de Arranjo) bidimensional em Python para calcular o ganho da antena nas coordenadas horizontais e verticais simultaneamente.
