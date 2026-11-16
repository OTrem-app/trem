# Passo a Passo de Montagem — Kit Básico

Siga esta ordem exatamente como está descrita. **Faça todas as conexões com a placa desligada** (sem cabo USB e sem fonte na tomada).

---

## Mapa Canônico de Conexões (Resumo)

| Componente | Pino no Módulo | Pino na Placa de Expansão (ESP32 38P) | Observação |
|---|---|---|---|
| **DHT22** | `VCC` (`+`) | **`5V`** (ou `3V3`) | `5V` recomendado para maior estabilidade |
| **DHT22** | `DATA` (`OUT`) | **`GPIO4`** | Dados digitais 1-Wire |
| **DHT22** | `GND` (`-`) | **`GND`** | Terra comum |
| **LM393 (Solo)** | `VCC` | **`3V3`** | ⚠️ **NUNCA ligar em 5V** |
| **LM393 (Solo)** | `GND` | **`GND`** | Terra comum |
| **LM393 (Solo)** | `AO` | **`GPIO35`** | Saída analógica (`ADC1_CH7`) |
| **LM393 (Solo)** | `DO` | *Não conectar* | Deixar solto |
| **Relé 5V (1 canal)** | `VCC` / `DC+` | **`5V`** | Alimentação da bobina |
| **Relé 5V (1 canal)** | `GND` / `DC-` | **`GND`** | Terra comum |
| **Relé 5V (1 canal)** | `IN` / `IN1` | **`GPIO19`** | Nunca usar `GPIO34–39` (são só entrada) |

> **Por que esses pinos?** Eles correspondem à configuração padrão do firmware TREM (`GPIO4` para DHT22, `GPIO35` para solo analógico e `GPIO19` para relé). Mantê-los evita ter que remapear pinos no aplicativo depois.

---

## Passo 1 — Conferir a bancada e encaixar o ESP32 no Shield

1. Separe todas as peças sobre uma mesa limpa, seca e não condutiva (madeira ou tapete antiestático — nunca metal).
2. Alinhe a placa **ESP32 (38 pinos)** sobre a **Placa de Expansão 38P** observando a direção do conector USB (ele deve ficar voltado para a borda externa, conforme a serigrafia do shield).
3. Pressione de forma uniforme até todos os pinos entrarem completamente nos soquetes, sem nenhum pino sobrando para fora ou entortado.

---

## Passo 2 — Ligar o Sensor DHT22 (Temperatura e Umidade do Ar)

Use 3 jumpers fêmea-fêmea:
1. `VCC` (`+`) do DHT22 → pino **`5V`** do shield.
2. `GND` (`-`) do DHT22 → pino **`GND`** do shield.
3. `DATA` (`OUT`) do DHT22 → pino **`GPIO4`** (ou `D4` / `IO4` / `4` na serigrafia do shield).

*(Se o seu DHT22 for o modelo cru de 4 pinos sem plaquinha, coloque um resistor de `4,7 kΩ` a `10 kΩ` entre `VCC` e `DATA`. O pino 3 `NC` fica vazio.)*

---

## Passo 3 — Ligar o Sensor de Umidade do Solo (LM393)

1. Conecte a sonda de 2 hastes aos dois pinos do conector na ponta da plaquinha do LM393 (não tem polaridade).
2. Do outro lado (4 pinos), conecte 3 jumpers fêmea-fêmea:
   - `VCC` do LM393 → **`3V3`** do shield ⚠️ **Conferir duas vezes: 3V3, nunca 5V!**
   - `GND` do LM393 → **`GND`** do shield.
   - `AO` do LM393 → **`GPIO35`** (ou `D35` / `IO35` / `35`).
3. Deixe o pino **`DO` completamente livre** (sem fio ligado).

> **Por que 3V3?** O pino de leitura analógica (`ADC`) do ESP32 suporta no máximo `3,3 V`. Alimentando o módulo LM393 com `3V3`, o sinal `AO` nunca ultrapassa esse limite.

---

## Passo 4 — Ligar o Módulo Relé 5V (`SRD-05VDC-SL-C`)

Use 3 jumpers fêmea-fêmea no lado de controle do relé:
1. `VCC` (`DC+`) do relé → **`5V`** do shield.
2. `GND` (`DC-`) do relé → **`GND`** do shield.
3. `IN` (ou `IN1`) do relé → **`GPIO19`** (ou `D19` / `IO19` / `19`).

*(Para testar primeiro na bancada, **não** ligue nenhuma carga na rede elétrica `110V/220V` ainda — o LED do módulo relé e o estalo mecânico já mostram se ele está acionando.)*

---

## Passo 5 — Checklist Antes de Ligar na Energia

Confira cada item antes de plugar o cabo USB ou a fonte:
- [ ] **Nenhum fio encostando** em pino vizinho ou solto sobre a mesa.
- [ ] **LM393** está no **`3V3`** (e não no `5V`), e o pino `DO` está livre.
- [ ] **Relé** está no **`5V`**, com `IN` em **`GPIO19`**.
- [ ] **DHT22** está com `VCC` e `GND` corretos (polaridade invertida aquece e queima o sensor na hora).
- [ ] Todos os `GND` compartilham a trilha de terra do shield.

---

## Passo 6 — Energizar e Testar

1. Conecte o cabo USB no computador (ou fonte `5 V` estável).
2. O LED de energia do ESP32 deve acender firme, sem piscar fraco nem aquecer nenhum componente.
3. Se algum componente esquentar ou o LED apagar, **desconecte imediatamente** e revise a fiação do Passo 5.
4. Tudo estável? Siga para a gravação do firmware e pareamento no app pela plataforma TREM (<https://trem.app.br>).
