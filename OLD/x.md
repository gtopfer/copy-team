# X Copy

_Gerado em: 2026-04-13_
_Fonte: arquivos em ./Input/_

---
<!--
## Post 1 — Lock-down day (Milestone)

**[EN]**
Lock-down day.

Our mechanical design was reviewed by engineers from 3 companies across 3 countries — on the same call. Their verdict: "Pretty good ground to just make the Mech. Des.."

---

**[PT-BR]**
Lock-down day.

Nosso design mecânico foi revisado por engenheiros de 3 empresas em 3 países — na mesma call. Veredicto: "Pretty good ground to just make the Mech. Des.."

---
-->

<!--
## Post 2 — Battery wire golden rule (Decisão / Thread)

**[EN]**
1/4 — Rule of RF design: battery wires should be close to the antenna. Lithium cells are metal. Metal reflects RF. Having the wires near the antenna creates a predictable coupling you can compensate for.

2/4 — Problem: the High Boy has antennas on both sides. Sub-GHz at the top. LoRa at the bottom. You can't optimize battery wire placement for both at the same time.

3/4 — We kept the connector near the LoRa side. Reasoning: LoRa is the range-sensitive radio most users will rely on. Sub-GHz uses active tuning and can compensate more. Moving the connector would have caused mechanical clearance issues.

4/4 — The tradeoff: Sub-GHz on the first prototype "will not be perfect." Needs tuning. That's fine — that's what the prototype is for. Hardware doesn't get good performance by accident. It gets there by measuring.
---

**[PT-BR]**
1/4 — Regra de design RF: os fios da bateria devem ficar perto da antena. Células de lítio são metal. Metal reflete RF. Ter os fios perto da antena cria um acoplamento previsível que você pode compensar.

2/4 — Problema: o High Boy tem antenas nos dois lados. Sub-GHz em cima. LoRa embaixo. Não dá pra otimizar o posicionamento dos fios pra ambas ao mesmo tempo.

3/4 — Mantivemos o conector próximo ao lado LoRa. Raciocínio: LoRa é o rádio sensível a alcance que a maioria dos usuários vai usar. Sub-GHz usa active tuning e pode compensar mais. Mover o conector criaria problemas de clearance mecânico.

4/4 — O trade-off: Sub-GHz no primeiro protótipo "não vai estar perfeito." Precisa de tuning. Tudo bem — é para isso que serve o protótipo. Hardware não consegue boa performance por acidente. Chega lá medindo.
---
-->

## Post 3 — 21.9mm vs 25mm (Explainer)

**[EN]**
The Flipper Zero is 25mm thick.

The High Boy is 21.9mm.

Inside: Wi-Fi 6, BLE 5.3, LoRa, Sub-GHz, NFC, RFID, IR, dual-MCU, color display, mic, SD card, USB-C, GPIO.

3.1mm thinner. Twice the radio stack.
---

**[PT-BR]**
O Flipper Zero tem 25mm de espessura.

O High Boy tem 21,9mm.

Dentro: Wi-Fi 6, BLE 5.3, LoRa, Sub-GHz, NFC, RFID, IR, dual-MCU, display colorido, microfone, SD card, USB-C, GPIO.

3,1mm mais fino. O dobro de rádios.
---

## Post 4 — 1.8mm NFC spacing (Problema → Solução)

**[EN]**
Three weeks ago our NFC antenna was 0.4mm from the battery. Antenna team: blocker.

Today: 1.8mm — same as the Flipper Zero. With a ferrite sheet between battery and board, confirmed as "fairly reasonable."

1.4mm. Dead radio to working radio.
---

**[PT-BR]**
Três semanas atrás, nossa antena NFC estava a 0,4mm da bateria. Time de antenas: bloqueador.

Hoje: 1,8mm — o mesmo do Flipper Zero. Com ferrite sheet entre bateria e placa, confirmado como "razoável."

1,4mm. Rádio morto para rádio funcionando.
---

## Post 5 — First prototype won't be perfect (Thread)

**[EN]**
1/3 — Our antenna engineer said it directly: "The first prototype will not be perfect. It needs tuning."

That's the most honest sentence anyone has said to us during this build.

2/3 — Sub-GHz active tuning can't be fully simulated. You need the physical hardware. You measure real resonance, swap components in the matching network, measure again. No deploy and patch.

3/3 — We're not promising a perfect first prototype. We're promising a real one — something you can hold, measure, and break. That's the point. Anyone who promises otherwise on first hardware is lying.
---

**[PT-BR]**
1/3 — Nosso engenheiro de antenas disse diretamente: "O primeiro protótipo não vai estar perfeito. Precisa de tuning."

É a frase mais honesta que alguém nos disse durante esse build.

2/3 — O active tuning do Sub-GHz não pode ser totalmente simulado. Você precisa do hardware físico. Mede a ressonância real, troca componentes na rede de matching, mede de novo. Não tem deploy e patch.

3/3 — Não estamos prometendo um primeiro protótipo perfeito. Estamos prometendo um real — algo que você pode segurar, medir e quebrar. É esse o ponto. Quem promete perfeição no primeiro hardware está mentindo.
---

## Post 6 — Timeline até o protótipo (Transparência / Thread)

**[EN]**
1/5 — Building in public means showing the full path, not just the destination. Here's exactly what needs to happen before we hold the first High Boy prototype.

2/5 — Apr 11: DXF locked, sent to PCB layout team. The mechanical design doesn't change after this.

3/5 — Apr 14: Antenna simulation engineer back from vacation, starts Sub-GHz, LoRa, and NFC simulations. Parallel track to PCB layout.

4/5 — End of April: PCB layout done (2–3 weeks), antenna designs finalized, both merged into final board file. Production begins.

5/5 — May 1–15: prototype PCBs in production. May 15–20: first unit in hand. Not for shipping — for measuring, breaking, and iterating.
---

**[PT-BR]**
1/5 — Construir em público significa mostrar o caminho inteiro, não só o destino. Aqui está exatamente o que precisa acontecer antes de termos o primeiro protótipo do High Boy nas mãos.

2/5 — 11 abr: DXF travado, enviado para o time de layout de PCB. O design mecânico não muda depois disso.

3/5 — 14 abr: engenheiro de simulações de antena volta de férias, começa simulações Sub-GHz, LoRa e NFC. Track paralelo ao layout do PCB.

4/5 — Final de abril: layout do PCB pronto (2-3 semanas), designs de antena finalizados, ambos fundidos no arquivo final de placa. Produção começa.

5/5 — 1-15 maio: PCBs do protótipo em produção. 15-20 maio: primeira unidade em mão. Não para envio — para medir, quebrar e iterar.
---

## Post 7 — PCB thickness 1.2mm → 1.6mm (Decisão técnica)

**[EN]**
1/3 — We changed both PCBs from 1.2mm to 1.6mm this week. Reason: at 1.2mm, the manufacturing team flagged real risk of stress fractures at mounting points under normal handling. Not edge cases. Normal use.

2/3 — The main board is 6 layers, 1.6mm. The NFC/RFID board is a sub-board that sits behind the battery. Both now at 1.6mm. Total device: still 21.9mm — under the 25mm hard ceiling we set.

3/3 — Small number. Real consequence. The manufacturing team is specifically there to catch things that look fine in CAD but fail in production. This is one of those.
---

**[PT-BR]**
1/3 — Mudamos os dois PCBs de 1,2mm para 1,6mm essa semana. Motivo: a 1,2mm, o time de manufatura sinalizou risco real de fratura por tensão nos pontos de montagem sob uso normal. Não casos extremos. Uso normal.

2/3 — A placa principal tem 6 camadas, 1,6mm. A placa NFC/RFID é uma sub-placa atrás da bateria. Ambas em 1,6mm. Dispositivo total: ainda 21,9mm — abaixo do teto rígido de 25mm que definimos.

3/3 — Número pequeno. Consequência real. O time de manufatura existe para pegar coisas que parecem boas no CAD mas falham na produção. Este foi um desses casos.

Número pequeno. Consequência real.
---

## Post 8 — SMA connector debate (Decisão / Thread)

**[EN]**
1/4 — The most-requested feature from our early community: a SMA antenna connector on the High Boy. External antenna, more range. We wanted it too.

2/4 — Two problems. First: a visible SMA on the outside looks like a walkie-talkie, not a hacking tool. Industrial design matters. Second: FCC. An external antenna connector changes the certification path significantly.

3/4 — Solution: internal LoRa antenna as default. SMA module available for the GPIO header. GPIO is pin-compatible with Flipper Zero modules — if you need range, you add a module.

4/4 — Tradeoff we accepted: base device range is limited by internal antenna. We're not pretending otherwise. For most use cases it's fine. For range-critical scenarios, the module path is the answer.
---

**[PT-BR]**
1/4 — A feature mais pedida pela nossa comunidade: um conector SMA de antena no High Boy. Antena externa, mais alcance. Nós também queríamos.

2/4 — Dois problemas. Primeiro: um SMA visível do lado de fora parece um walkie-talkie, não uma ferramenta de hacking. Design industrial importa. Segundo: FCC. Um conector de antena externa muda o caminho de certificação significativamente.

3/4 — Solução: antena LoRa interna como padrão. Módulo SMA disponível para o header GPIO. GPIO é compatível com módulos do Flipper Zero — se você precisa de alcance, adiciona um módulo.

4/4 — Trade-off que aceitamos: alcance do dispositivo base é limitado pela antena interna. Não estamos fingindo o contrário. Para a maioria dos casos de uso é suficiente. Para cenários críticos de alcance, o caminho do módulo é a resposta.
---

