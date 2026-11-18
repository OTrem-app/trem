# Catálogo de Peças e Kits por Aplicação (BYOD)

Este catálogo lista os módulos compatíveis com a plataforma **TREM** e exemplos de composições por aplicação e nível de automação. Você pode adquirir as peças avulsas no **AliExpress**, Mercado Livre, Shopee ou lojas de eletrônica locais.

---

## 1. Catálogo de Componentes Compatíveis

### Controlador e Base (Obrigatórios em todo nó)

| Componente | Especificação recomendada | Termo de busca (AliExpress) |
|---|---|---|
| **Placa ESP32-WROOM-32 (38 pinos)** | Versão estreita de **38 pinos**, USB-C ou Micro-USB (`CP2102` ou `CH340`) | `ESP32 38 pin development board Type-C` |
| **Shield de Expansão ESP32 38P** | Placa base com barramentos `V` (`3V3`/`5V`), `G` (`GND`), `S` (`GPIO`) e entrada P4 (`6,5–16 V`) | `ESP32 38 pin expansion board shield` |

### Sensores

| Categoria | Sensor | O que mede | Tensão / Interface | Termo de busca (AliExpress) |
|---|---|---|---|---|
| **Clima (Ar)** | **DHT22 (AM2302)** | Temperatura (`-40 a +80 °C`) e umidade do ar (`0–100% UR`) | `3,3 V – 5 V` · Digital 1-Wire (módulo 3 pinos com *pull-up*) | `DHT22 AM2302 temperature humidity sensor module` |
| **Temperatura (Sonda)** | **DS18B20** | Temperatura em líquidos, solo ou câmara fria (`-55 a +125 °C`, inox à prova d'água) | `3,3 V – 5 V` · Digital 1-Wire (requer resistor `4,7 kΩ` entre `VCC` e `DATA`) | `DS18B20 waterproof temperature sensor cable` |
| **Luz** | **BH1750 (GY-302)** | Luminosidade ambiente em `lux` | `3,3 V` · Digital `I2C` (`GPIO 21 SDA` / `GPIO 22 SCL`) | `BH1750 GY-302 light intensity sensor module` |
| **Solo (Básico)** | **LM393 + Sonda** | Umidade do solo (`0–100%`) via saída analógica `AO` | **`3,3 V` estrito** (protege o ADC do ESP32) · Analógico `ADC1` (`GPIO 32–39`) | `soil moisture sensor module LM393 hygrometer` |
| **Solo (Capacitivo)** | **Capacitive Soil Moisture v1.2 / v2.0** | Umidade do solo sem corrosão das hastes | **`3,3 V`** · Analógico `ADC1` (`GPIO 32–39`) | `capacitive soil moisture sensor v1.2 corrosion resistant` |
| **Solo (Profissional)** | **Sonda RS485 7-em-1** | Umidade, Temperatura, EC, pH, Nitrogênio (N), Fósforo (P) e Potássio (K) | `12 V DC` (sonda) + conversor `MAX485 TTL-RS485` em `3,3 V` (`UART2`) | `RS485 soil NPK PH EC temperature humidity 7 in 1 sensor` |
| **Água / Hidroponia** | **Módulo de pH (BNC)** | Acidez/alcalinidade da solução (`pH 0–14`) | `3,3 V / 5 V` (divisor/limitador `≤ 3,3 V` no pino `ADC1`) | `PH sensor module BNC probe Arduino ESP32` |
| **Água / Fluxo** | **YF-S201 (Hall)** | Vazão de água em tubulação (`1–30 L/min`) | `5 V` (sinal com divisor para `3,3 V`) · Pulso digital | `YF-S201 water flow sensor 1/2 inch` |
| **Presença** | **PIR HC-SR501** | Movimento humano/animal por infravermelho passivo | `5 V` (saída lógica `3,3 V` nativa) · Digital | `HC-SR501 PIR motion sensor module` |
| **Gases / Segurança** | **MQ-2** / **MQ-135** | Gás GLP/fumaça (`MQ-2`) ou amônia/qualidade do ar (`MQ-135`) | Aquecedor `5 V` · Leitura em `ADC1` (com divisor para `≤ 3,3 V`) | `MQ-2 gas smoke sensor module` / `MQ-135 air quality sensor` |
| **Qualidade do Ar** | **MH-Z19B (NDIR)** | Concentração de `CO₂` (`0–5000 ppm`) | `5 V` · `UART` (`3,3 V` TTL) ou `PWM` | `MH-Z19B infrared CO2 sensor module` |

### Atuadores e Módulos de Potência

| Componente | Função | Alimentação / Controle | Termo de busca (AliExpress) |
|---|---|---|---|
| **Módulo Relé 1, 2 ou 4 Canais (`SRD-05VDC-SL-C`)** | Liga/desliga bombas, exaustores, lâmpadas, válvulas e umidificadores | Bobina `5 V` (`VCC`/`GND`) · Sinal `IN` `3,3 V` · **Com optoacoplador** | `5V 1 channel relay module optocoupler low level trigger` |
| **Mini Bomba d'Água Submersível + Mangueira** | Irrigação automática de vasos, hortas e estufas | `5 V USB` ou `12 V DC` (acionada pelos contatos `COM`/`NO` do relé) + tubo de silicone `6x8 mm` | `mini submersible water pump 5V 12V silicone tube irrigation` |
| **Válvula Solenoide Normalmente Fechada (NF)** | Abertura de linha de água pressurizada por zona | `12 V DC` (via relé + fonte `12 V`) | `12V DC electric solenoid valve 1/2 inch normally closed water` |
| **Umidificador Ultrassônico 5V** | Controle de umidade do ar em estufas e ambientes | `5 V USB` (acionado via relé) | `5V USB ultrasonic mist maker humidifier module` |
| **Sirene / Buzzer Ativo** | Alarme sonoro local de segurança ou alerta crítico | `3,3 V – 5 V` (buzzer) ou `12 V` (sirene via relé) | `active buzzer module 3.3V 5V` / `12V wired alarm siren` |

### Cabos, Fontes e Acessórios Essenciais

- **Jumpers Dupont Fêmea-Fêmea (20 cm):** para ligar os sensores e relés diretamente às barras de pinos do Shield 38P (`40pcs dupont wire female to female 20cm`).
- **Fonte de Alimentação:** carregador `5 V / 2 A` + cabo USB de dados (para o ESP32) ou fonte chaveada `9 V / 12 V DC` com plugue P4 (`5,5 × 2,1 mm`).
- **Caixa de Proteção (Case):** caixa plástica ventilada (ambientes internos) ou caixa estanque `IP65` com prensa-cabos (hortas, estufas e áreas úmidas).

---

## 2. Kits de Referência por Aplicação e Nível

Cada kit é pensado pelo **que você consegue automatizar na prática**, não apenas pela lista de peças.

### 🏠 1. Residencial (Casa Inteligente)
- **Básico:** `ESP32 38P + Shield` + `DHT22` + `PIR HC-SR501` + `Relé 2 Canais` → acende luz por presença ou horário e liga ventilador/aquecedor conforme a temperatura do quarto.
- **Intermediário:** Básico + `BH1750` (luminosidade) + `Relé 4 Canais` → só acende a luz se estiver escuro + controla até 4 circuitos independentes pelo celular.
- **Avançado:** Intermediário + `2x PIR` + `MQ-2` (gás/fumaça) + `Sirene` → adiciona camada de segurança contra vazamento de gás e presença não autorizada.

### 🌿 2. Horta, Estufa e Cultivo Indoor
- **Básico (Clima + Rega Automática):** `ESP32 38P + Shield` + `DHT22` + `Sensor de Solo LM393 (ou Capacitivo)` + `Relé 2 Canais` + `Mini Bomba d'Água + Mangueira` → monitora temperatura/umidade do ar e **irriga sozinho quando o solo seca**, desligando a bomba assim que atinge a umidade ideal.
- **Intermediário:** Básico + `DS18B20` (temperatura da água/substrato) + `BH1750` (luz) + `Relé 4 Canais` + `Umidificador 5V` → controla rega, umidificador e exaustão de forma coordenada.
- **Avançado:** Intermediário + `Sonda RS485 7-em-1` (ou `pH` + `EC`) + `CO₂ MH-Z19B` + `Sensor de Fluxo YF-S201` → controle completo de nutrição, VPD e fertirrigação.

### 🏪 3. Comercial e Câmaras Frias
- **Básico:** `ESP32 38P + Shield` + `DHT22` + `PIR HC-SR501` + `Relé 2 Canais` + `Sirene` → iluminação econômica por expediente, proteção térmica de estoque e alerta de movimento fora de horário.
- **Intermediário:** Básico + `Sonda DS18B20 à prova d'água` + `MQ-2` → monitora interior de freezers/câmaras frias com alerta imediato no celular se a temperatura subir.

### 🐟 4. Granja, Avicultura e Piscicultura
- **Básico:** `ESP32 38P + Shield` + `DHT22` + `DS18B20` + `Relé 2 Canais` → monitora temperatura do galpão ou tanque de peixes e aciona exaustor, aquecedor ou aerador automaticamente.
- **Intermediário:** Básico + `MQ-135` (amônia/gases) + `Sirene` → protege os animais acionando ventilação forçada e alerta sonoro caso o nível de amônia suba.

---

## ⚠️ Regras de Ouro na Compra e Montagem

1. **Pinos do ESP32 trabalham em `3,3 V`:** nunca ligue um sinal de `5 V` diretamente em um pino `GPIO` ou `ADC` do ESP32. Alimente o sensor de solo `LM393` sempre em **`3V3`**.
2. **ADC1 vs. ADC2:** com o Wi-Fi ligado, use apenas pinos **ADC1 (`GPIO 32, 33, 34, 35, 36 ou 39`)** para sensores analógicos.
3. **Pinos somente entrada:** `GPIO 34, 35, 36 e 39` são ótimos para sensores analógicos, mas **não acionam relés** (para relés, prefira `GPIO 25, 26, 27, 32 ou 33`).
4. **Cargas de potência:** nunca alimente bombas d'água, válvulas ou motores direto pelo pino `3V3` do ESP32; passe sempre a alimentação da carga pelos contatos `COM` e `NO` do **Módulo Relé**.
