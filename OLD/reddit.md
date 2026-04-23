# Reddit Copy

_Gerado em: 2026-04-13_
_Fonte: arquivos em ./Input/_

---

## [EN] Lock-down day: our mechanical design was reviewed and approved by engineers from 3 companies across 3 countries — on the same call

We're building the High Boy, a multi-radio hacking device with Wi-Fi 6, BLE 5.3, LoRa, Sub-GHz, NFC, RFID, and IR — all in a 21.9mm chassis. We've been doing hardware development with teams in Finland and China, which means coordination is mostly async.

Last week we had a single call where our antenna specialists in Finland, our PCB layout team, and our mechanical manufacturing partner in China all reviewed the 3D model together. At the end, the antenna engineer said: "This is exactly as we discussed. Pretty good ground to just make the designs." That was it. Lock-down confirmed.

Lock-down means: component positions are frozen, the DXF file ships to the PCB team, layout begins. After this point, any mechanical change ripples into timeline and cost. It's roughly the hardware equivalent of merging to main with no rollback — except iterations take weeks, not minutes.

To get there we'd been negotiating constraints in advance: PCB thickness was bumped from 1.2mm to 1.6mm for mechanical strength, NFC gap to the battery was validated at 1.8mm (same as the Flipper Zero — a known-good reference), and antenna clearance zones were documented before anyone got on the call. By the time we had the three teams together, there were no surprises — just confirmations.

What I didn't expect: the hardest part wasn't the technical decisions. It was making sure each team had the exact same 3D reference file before the call so we weren't looking at different versions of the model. We've been burned by that before.

If you're doing hardware with distributed teams: what's your process for keeping everyone on the same mechanical reference? We're still figuring out a cleaner versioning workflow for 3D models.

Subreddits sugeridos: r/electronics, r/embedded, r/FlipperZero, r/hardwaredev, r/AskElectronics
---

## [PT-BR] Lock-down day: nosso design mecânico foi aprovado por engenheiros de 3 empresas em 3 países — na mesma call

Estamos construindo o High Boy, um dispositivo multi-rádio com Wi-Fi 6, BLE 5.3, LoRa, Sub-GHz, NFC, RFID e IR — tudo em um chassi de 21,9mm. O desenvolvimento de hardware acontece com times na Finlândia e na China, o que significa que a coordenação é quase sempre assíncrona.

Na semana passada, conseguimos reunir na mesma call nosso time de antenas na Finlândia, o time de layout de PCB e a manufatura mecânica na China para revisar o modelo 3D. No final, o engenheiro de antenas disse: "This is exactly as we discussed. Pretty good ground to just make the designs." Foi isso. Lock-down confirmado.

Lock-down significa: posição dos componentes congelada, arquivo DXF enviado para o time de PCB, layout começa. Qualquer mudança mecânica depois disso impacta prazo e custo. É o equivalente em hardware de dar merge no main sem rollback — com a diferença que cada iteração leva semanas, não minutos.

Para chegar até aqui, negociamos as restrições com antecedência: espessura dos PCBs subiu de 1,2mm para 1,6mm por resistência mecânica, o espaço entre a antena NFC e a bateria foi validado em 1,8mm (o mesmo do Flipper Zero — uma referência já testada), e as zonas de clearance de antena foram documentadas antes de qualquer call. Quando os três times se encontraram, não havia surpresas — só confirmações.

O que me surpreendeu: a parte mais difícil não foi a decisão técnica. Foi garantir que cada time estivesse olhando para o mesmo arquivo 3D antes da reunião. Já fomos prejudicados por isso antes — alguém com uma versão antiga do modelo sem saber.

Se você faz hardware com times distribuídos: como você controla a versão dos arquivos 3D? Ainda estamos construindo um workflow mais limpo para isso.

Subreddits sugeridos: r/electronics, r/embedded, r/FlipperZero, r/hardwaredev, r/AskElectronics
---

<!--
## [EN] The golden rule of battery placement: wires near the antenna. But what do you do when you have antennas on both sides?

Building a multi-radio device teaches you RF rules you never think about in software. Here's one we had to navigate this week.

The High Boy has antennas on two sides: Sub-GHz at the top, LoRa at the bottom. Standard RF engineering rule says battery wires should run close to the antenna — because lithium batteries are metal, and metal interferes with RF. Having the wires near (rather than opposite) the antenna gives you a predictable, controllable coupling you can compensate for. Having them far away creates an unpredictable reflection.

Our antenna team's guidance was clear on the principle. The problem: we had to choose which antenna to optimize for, because you can't win on both sides.

We kept the battery connector near the LoRa side. Reasons: LoRa is the antenna we expect most users to rely on for range-sensitive applications. The existing 3D model already placed the connector there and moving it to the Sub-GHz side would have pushed the connector into a zone with less mechanical clearance. And Sub-GHz with active tuning can compensate more than LoRa can.

The tradeoff: Sub-GHz performance on the first prototype will be "not perfect" by the antenna engineer's own admission. It needs tuning. That's fine — that's what prototypes are for.

What I found interesting: this kind of decision doesn't exist in software. There's no "battery wires near the antenna" in a web app. Hardware forces you to reason about physics directly, and the cost of a wrong guess isn't a failing test — it's three more weeks of PCB layout.

Has anyone here dealt with multi-antenna RF placement? Curious how you handle prioritization when you can't isolate the interference sources cleanly.

Subreddits sugeridos: r/rfelectronics, r/electronics, r/AskElectronics, r/embedded, r/FlipperZero
---

## [PT-BR] A regra de ouro do posicionamento da bateria: fios perto da antena. Mas e quando você tem antenas nos dois lados?

Construir um dispositivo multi-rádio te ensina regras de RF que você nunca encontra em software. Aqui está uma que tivemos que enfrentar essa semana.

O High Boy tem antenas nos dois lados: Sub-GHz em cima, LoRa embaixo. A regra básica de RF diz que os fios da bateria devem passar perto da antena — porque baterias de lítio são metal, e metal interfere com RF. Ter os fios perto (em vez de do lado oposto) da antena cria um acoplamento previsível e controlável. Do lado oposto, você tem uma reflexão imprevisível que é muito mais difícil de compensar.

A orientação do nosso time de antenas foi clara no princípio. O problema: tínhamos que escolher qual antena otimizar, porque não dá pra ganhar nos dois lados.

Mantivemos o conector da bateria próximo ao lado do LoRa. Razões: LoRa é a antena que mais usuários vão usar em aplicações sensíveis a alcance. O modelo 3D existente já posicionava o conector ali, e mover para o lado Sub-GHz criaria restrições mecânicas problemáticas. E o Sub-GHz com active tuning tem mais capacidade de compensação do que o LoRa.

O trade-off: a performance Sub-GHz no primeiro protótipo "não vai estar perfeita", nas palavras do próprio engenheiro de antenas. Precisa de tuning. Tudo bem — é exatamente isso que protótipos são para resolver.

O que achei mais interessante: esse tipo de decisão não existe em software. Não tem "fio de bateria perto da antena" em uma aplicação web. Hardware te obriga a raciocinar sobre física diretamente, e o custo de uma decisão errada não é um teste falhando — são três semanas a mais de layout de PCB.

Alguém aqui já trabalhou com posicionamento de múltiplas antenas? Curioso saber como vocês lidam com a priorização quando não dá pra isolar as fontes de interferência.

Subreddits sugeridos: r/rfelectronics, r/electronics, r/AskElectronics, r/embedded, r/FlipperZero
---
-->

## [EN] 21.9mm vs 25mm: how we fit more radios into a thinner device than the Flipper Zero

The Flipper Zero is 25mm thick. The High Boy is 21.9mm. That's 3.1mm thinner.

Inside the High Boy: Wi-Fi 6, BLE 5.3, LoRa, Sub-GHz, NFC, RFID, IR, dual-MCU, color display, microphone, SD card slot, USB-C, and a GPIO header compatible with Flipper Zero modules.

That 21.9mm number isn't the result of a single clever decision — it came from a series of small compromises that compounded. PCBs at 1.6mm instead of thicker options. Battery connector positioned to maximize clearance for antenna zones. Component placement iterated over multiple 3D reviews with three teams across two continents. The NFC/RFID sub-board positioned behind the battery with 1.8mm of separation (and a ferrite sheet to keep crosstalk down).

We also gave ourselves a hard ceiling: the device cannot exceed 25mm. The reasoning was simple — if we're going to be 3mm thinner than the Flipper Zero while carrying more radios, that margin should never be given back casually. The antenna team has up to 3mm of emergency budget if simulations prove it's needed, but the mechanical design won't touch it.

What's currently 21.9mm might flex slightly depending on antenna simulation results. Sakari (our antenna simulation engineer) gets back from vacation Monday and starts the Sub-GHz, LoRa, and NFC simulations. If something needs to change, we'll know in 2–3 weeks.

The honest version: you can design for thin and you can design for feature-rich, but designing for both at the same time is a constant negotiation. There's no magic here, just a lot of small decisions that each shave or add fractions of a millimeter.

Subreddits sugeridos: r/FlipperZero, r/electronics, r/hardwaredev, r/cybersecurity, r/hacking
---

## [PT-BR] 21,9mm vs 25mm: como colocamos mais rádios em um dispositivo mais fino que o Flipper Zero

O Flipper Zero tem 25mm de espessura. O High Boy tem 21,9mm. São 3,1mm a menos.

Dentro do High Boy: Wi-Fi 6, BLE 5.3, LoRa, Sub-GHz, NFC, RFID, IR, dual-MCU, display colorido, microfone, slot SD card, USB-C e um GPIO compatível com módulos do ecossistema Flipper Zero.

Esses 21,9mm não vieram de uma única decisão genial — vieram de uma série de pequenos compromissos que foram se acumulando. PCBs em 1,6mm em vez de opções mais espessas. Conector da bateria posicionado para maximizar o clearance das zonas de antena. Posicionamento de componentes iterado em múltiplas revisões 3D com três times em dois continentes. A sub-placa NFC/RFID posicionada atrás da bateria com 1,8mm de separação (e um ferrite sheet para manter o crosstalk sob controle).

Também definimos um teto rígido: o dispositivo não pode ultrapassar 25mm. O raciocínio foi simples — se vamos ser 3mm mais finos que o Flipper Zero com mais rádios, essa margem não pode ser descartada de forma casual. O time de antenas tem até 3mm de margem de emergência caso as simulações provem necessidade, mas o design mecânico não vai tocar nisso.

Os 21,9mm atuais podem ajustar ligeiramente dependendo dos resultados das simulações de antena. Nosso engenheiro de simulações entra de férias nessa semana e começa as simulações de Sub-GHz, LoRa e NFC assim que voltar. Se algo precisar mudar, saberemos em 2-3 semanas.

A versão honesta: você pode projetar para ser fino e pode projetar para ter muitas funcionalidades, mas fazer os dois ao mesmo tempo é uma negociação constante. Não tem mágica aqui, só muitas pequenas decisões que cada uma economiza ou adiciona frações de milímetro.

Subreddits sugeridos: r/FlipperZero, r/electronics, r/hardwaredev, r/cybersecurity, r/hacking
---

<!--
## [EN] From 0.4mm to 1.8mm: how we fixed the NFC antenna placement that would have killed the radio

A few weeks ago, the NFC antenna in our design was 0.4mm from the battery. Our antenna team flagged it immediately: at that distance, with a lithium cell acting as a metal plane, NFC performance would have been severely degraded or non-functional. It wasn't a warning — it was a blocker.

We moved the entire NFC/RFID sub-board layout. The new gap: 1.8mm. The reference we used: the Flipper Zero, which also runs a NFC antenna next to a battery and has known-good performance at that spacing. The antenna team confirmed 1.8mm is "fairly reasonable" and that with a ferrite sheet between the battery and the NFC board, we'd get acceptable performance.

Two things made this solvable: we had a concrete target to design toward (Flipper Zero's 1.8mm), and the fix happened before the 3D model was locked. Catching it after lock-down would have meant re-doing the entire component placement sequence.

The ferrite sheet adds a small amount of thickness and cost. We decided that was non-negotiable — NFC without ferrite shielding next to a battery is a gamble we're not willing to take on a production device.

What I keep thinking about: the Flipper Zero being a known-good reference for these kinds of numbers is genuinely useful when you're building a device in a similar form factor. Having a public device you can reverse-engineer the constraints from is an underrated resource.

Has anyone here done NFC antenna tuning with battery interference? How much does the ferrite sheet actually help vs. just increasing the gap?

Subreddits sugeridos: r/electronics, r/rfelectronics, r/AskElectronics, r/FlipperZero, r/embedded
---

## [PT-BR] De 0,4mm para 1,8mm: como corrigimos o posicionamento da antena NFC que teria matado o rádio

Algumas semanas atrás, a antena NFC do nosso design estava a 0,4mm da bateria. O time de antenas sinalizou imediatamente: a essa distância, com a célula de lítio funcionando como um plano metálico, a performance NFC teria sido severamente degradada ou simplesmente não funcionaria. Não era um aviso — era um bloqueador.

Movemos o layout inteiro da sub-placa NFC/RFID. O novo espaço: 1,8mm. A referência que usamos: o Flipper Zero, que também roda uma antena NFC ao lado de uma bateria e tem performance conhecida nesse espaçamento. O time de antenas confirmou que 1,8mm é "razoável" e que com um ferrite sheet entre a bateria e a placa NFC, teríamos performance aceitável.

Duas coisas tornaram isso solucionável: tínhamos um alvo concreto para projetar (os 1,8mm do Flipper Zero), e a correção aconteceu antes do modelo 3D ser travado. Descobrir isso depois do lock-down teria significado refazer toda a sequência de posicionamento de componentes.

O ferrite sheet adiciona um pequeno aumento de espessura e custo. Decidimos que era inegociável — NFC sem blindagem ferrite ao lado de uma bateria é um risco que não estamos dispostos a correr em um dispositivo de produção.

O que continua me intrigando: o Flipper Zero como referência concreta para esses números é genuinamente útil quando você está construindo um dispositivo com form factor similar. Ter um dispositivo público cujas restrições físicas você pode estudar é um recurso que a maioria das pessoas subestima.

Alguém aqui já fez tuning de antena NFC com interferência de bateria? O ferrite sheet realmente ajuda ou o que importa mesmo é só aumentar o gap?

Subreddits sugeridos: r/electronics, r/rfelectronics, r/AskElectronics, r/FlipperZero, r/embedded
---
-->

## [EN] "The first prototype will not be perfect. It needs tuning." — and that's exactly the right expectation to set

Our antenna engineer said this about the Sub-GHz radio during last week's design review. It wasn't a concern — it was an explanation of how antenna development actually works.

Sub-GHz uses active tuning: an electronic circuit adjusts the antenna's matching network in real time to compensate for manufacturing variance and environmental factors. To calibrate active tuning, you need real measurements on physical hardware. Simulations give you direction. The prototype gives you ground truth.

The process goes: build prototype → measure actual resonance frequency → identify delta from target → swap passive components (capacitors, inductors) in the matching network → re-measure → iterate. There's no "push to production and hotfix." Every iteration is a new set of parts and 2–3 weeks of wait.

We were initially a little anxious about this. Then we looked at Flipper Zero's development history — they iterated through multiple sub-GHz antenna versions too. Every serious hardware product that ships with good RF performance got there through iteration, not through a perfect first pass.

What this means practically: the first prototype is for measurement, not for field use. We'll get real numbers for Sub-GHz resonance, LoRa performance, and NFC range. We'll then know exactly what to fix for the second prototype. The antenna team estimates the Sub-GHz will need 1–2 tuning rounds after the initial prototype measurements.

I think there's a broader lesson here: hardware development culture that hides imperfection in early prototypes produces products that ship with unresolved RF problems. Expecting imperfection and planning for iteration is what actually produces good antennas.

What's your experience with antenna tuning timelines? How many rounds does Sub-GHz typically take to converge?

Subreddits sugeridos: r/rfelectronics, r/electronics, r/AskElectronics, r/embedded, r/hardwaredev
---

## [PT-BR] "O primeiro protótipo não vai estar perfeito. Precisa de tuning." — e essa é exatamente a expectativa certa de se definir

Nosso engenheiro de antenas disse isso sobre o rádio Sub-GHz durante a revisão de design da semana passada. Não era uma preocupação — era uma explicação de como o desenvolvimento de antenas realmente funciona.

Sub-GHz usa active tuning: um circuito eletrônico ajusta a rede de matching da antena em tempo real para compensar variações de fabricação e fatores ambientais. Para calibrar o active tuning, você precisa de medições reais no hardware físico. Simulações te dão direção. O protótipo te dá a realidade.

O processo é: construir o protótipo → medir a frequência de ressonância real → identificar o delta em relação ao alvo → trocar componentes passivos (capacitores, indutores) na rede de matching → re-medir → iterar. Não tem "push pra produção e hotfix". Cada iteração é um novo conjunto de peças e 2-3 semanas de espera.

Ficamos um pouco apreensivos com isso no começo. Depois olhamos para o histórico de desenvolvimento do Flipper Zero — eles também iteraram por múltiplas versões da antena Sub-GHz. Todo produto de hardware sério que chega ao mercado com boa performance de RF chegou lá por iteração, não por um primeiro protótipo perfeito.

O que isso significa na prática: o primeiro protótipo é para medição, não para uso em campo. Vamos ter números reais de ressonância Sub-GHz, performance LoRa e alcance NFC. Depois vamos saber exatamente o que corrigir para o segundo protótipo. O time de antenas estima que o Sub-GHz vai precisar de 1-2 rodadas de tuning após as medições iniciais do protótipo.

Acho que há uma lição mais ampla aqui: uma cultura de desenvolvimento de hardware que esconde imperfeições nos protótipos iniciais produz produtos que chegam ao mercado com problemas de RF não resolvidos. Esperar imperfeição e planejar para iteração é o que realmente produz boas antenas.

Qual é a sua experiência com prazos de tuning de antena? Quantas rodadas o Sub-GHz normalmente leva para convergir?

Subreddits sugeridos: r/rfelectronics, r/electronics, r/AskElectronics, r/embedded, r/hardwaredev
---

## [EN] Here's exactly what needs to happen between today and May 20 — every step, every dependency, every team

We talk a lot about building in public. This is a chance to actually do it: here's the full timeline from where we are today to holding the first High Boy prototype.

The design lock-down happened this week. The mechanical team sent the DXF file to our PCB layout team. That kicks off the critical path.

PCB layout (main board + NFC/RFID board): estimated 2–3 weeks from now. One engineer with full allocation to this project. No parallel dependencies — they need the finalized DXF first, which they now have.

Antenna design (Sub-GHz, LoRa, NFC simulations): starts Monday when our antenna simulation engineer returns from vacation. Works in parallel with PCB layout. Outputs: antenna geometry files that feed into the layout.

End of April: both PCB layout and antenna designs should be complete. These are joined — antenna outputs need to be incorporated into the final PCB before the board goes to fabrication.

Early May (1–15): first prototype PCBs in production. Manufacturing target is 2 weeks from layout finalization to boards in hand.

May 15–20: first High Boy prototype in our hands.

This is the shortest realistic path. Any slip in PCB layout, any issue in antenna simulations requiring redesign, pushes the prototype date. We're not padding these estimates — they're tight.

One thing I think is worth being honest about: prototype delivery is not product launch. May 20 means we have something to measure and iterate on. It does not mean the device is ready to ship.

What's your experience with hardware timelines? How often do "2–3 week PCB layout" estimates actually hit?

Subreddits sugeridos: r/electronics, r/hardwaredev, r/FlipperZero, r/projectmanagement, r/embedded
---

## [PT-BR] Aqui está exatamente o que precisa acontecer entre hoje e 20 de maio — cada passo, cada dependência, cada time

Falamos muito em construir em público. Esta é uma chance de fazer isso de verdade: aqui está o timeline completo de onde estamos hoje até ter o primeiro protótipo do High Boy nas mãos.

O lock-down do design aconteceu essa semana. O time mecânico enviou o arquivo DXF para o time de layout de PCB. Isso inicia o caminho crítico.

Layout do PCB (placa principal + placa NFC/RFID): estimativa de 2-3 semanas. Um engenheiro com alocação total para esse projeto. Sem dependências paralelas — ele precisava do DXF finalizado, que agora tem.

Design de antenas (simulações Sub-GHz, LoRa, NFC): começa segunda-feira quando nosso engenheiro de simulações volta de férias. Trabalha em paralelo com o layout do PCB. Saídas: arquivos de geometria de antena que alimentam o layout.

Final de abril: layout de PCB e designs de antena devem estar completos. Esses se encontram — as saídas das antenas precisam ser incorporadas no PCB final antes de ir para fabricação.

Início de maio (1-15): produção dos primeiros PCBs do protótipo. Meta de manufatura é 2 semanas do layout finalizado até as placas em mão.

15-20 de maio: primeiro protótipo do High Boy em nossas mãos.

Este é o caminho mais curto realista. Qualquer atraso no layout de PCB, qualquer problema nas simulações de antena que exija redesign, empurra a data do protótipo. Não estamos adicionando margem nessas estimativas — elas são apertadas.

Uma coisa que acho que vale ser honesto sobre: entrega do protótipo não é lançamento do produto. 20 de maio significa que teremos algo para medir e iterar. Não significa que o dispositivo está pronto para envio.

Qual é a sua experiência com timelines de hardware? Com que frequência estimativas de "2-3 semanas de layout de PCB" realmente se cumprem?

Subreddits sugeridos: r/electronics, r/hardwaredev, r/FlipperZero, r/projectmanagement, r/embedded
---

<!-- ## [EN] Why we decided not to put a SMA connector on the High Boy (and what we're doing instead)

The most requested feature from our early community: a SMA connector for the LoRa/Sub-GHz antenna. External antenna, better range, looks like a serious radio tool. We wanted it too.

Two problems stopped us. First: industrial design. A visible SMA connector on the outside of the device makes it look like a walkie-talkie. The High Boy is a multi-tool for security researchers, not a field radio. Aesthetics matter for adoption, and we decided a device that looks like communications equipment creates the wrong first impression.

Second, and more practically: FCC certification. Adding a detachable external antenna connector changes your certification path significantly. You're no longer certifying a fixed system — you're certifying a device with an open RF interface, which means much more extensive testing, specific antenna certification requirements, and exposure to the "user can attach a power amplifier" scenario that complicates regulatory approval.

The solution we landed on: internal antenna as default, with a SMA module available for the GPIO header. The GPIO is pin-compatible with Flipper Zero modules — if you want better range, you connect an external module that adds SMA. The base device stays clean, the certification stays manageable, and power users get the hardware access they want.

The GPIO-compatible module approach also means we're not the only source of antenna modules. Anyone building for the Flipper Zero ecosystem can build for High Boy.

Tradeoff we accepted: the base device's LoRa range is limited by an internal antenna. We're not going to pretend that's as good as external SMA. For a lot of use cases it's fine. For people who need range, the module path is the answer.

Would you have made a different call here? Specifically on the FCC tradeoff — is there a path to SMA that doesn't blow up the certification process?

Subreddits sugeridos: r/rfelectronics, r/FlipperZero, r/hacking, r/electronics, r/AskElectronics
---

## [PT-BR] Por que decidimos não colocar um conector SMA no High Boy (e o que estamos fazendo em vez disso)

A feature mais pedida pela nossa comunidade inicial: um conector SMA para a antena LoRa/Sub-GHz. Antena externa, maior alcance, parece uma ferramenta de rádio a sério. Nós também queríamos.

Dois problemas nos frearam. Primeiro: design industrial. Um conector SMA visível do lado de fora do dispositivo faz parecer um walkie-talkie. O High Boy é uma ferramenta multi-uso para pesquisadores de segurança, não um rádio de campo. Estética importa para adoção, e decidimos que um dispositivo que parece equipamento de comunicações cria a impressão errada.

Segundo, e mais praticamente: certificação FCC. Adicionar um conector de antena externa destacável muda seu caminho de certificação significativamente. Você não está mais certificando um sistema fixo — está certificando um dispositivo com interface RF aberta, o que exige muito mais testes, requisitos específicos de certificação de antena, e exposição ao cenário "usuário pode conectar um amplificador de potência" que complica a aprovação regulatória.

A solução que encontramos: antena interna como padrão, com um módulo SMA disponível para o header GPIO. O GPIO é compatível com os módulos do Flipper Zero — se você quer maior alcance, você conecta um módulo externo que adiciona SMA. O dispositivo base fica limpo, a certificação fica gerenciável, e usuários avançados têm o acesso a hardware que querem.

A abordagem do módulo GPIO-compatível também significa que não somos a única fonte de módulos de antena. Qualquer pessoa construindo para o ecossistema do Flipper Zero pode construir para o High Boy.

Trade-off que aceitamos: o alcance LoRa do dispositivo base é limitado pela antena interna. Não vamos fingir que isso é tão bom quanto SMA externo. Para muitos casos de uso é suficiente. Para quem precisa de alcance, o caminho do módulo é a resposta.

Você teria feito uma escolha diferente? Especificamente sobre o trade-off da FCC — existe um caminho para o SMA que não complica o processo de certificação?

Subreddits sugeridos: r/rfelectronics, r/FlipperZero, r/hacking, r/electronics, r/AskElectronics
--- -->

## [EN] We changed both PCBs from 1.2mm to 1.6mm — a small number with real mechanical consequences

During last week's design review, our mechanical manufacturing partner flagged something we'd been borderline on: the 1.2mm PCB thickness on both the main board and the NFC/RFID sub-board was at the edge of acceptable mechanical tolerance for the enclosure design.

At 1.2mm, both boards had a real risk of flexion stress fractures at the mounting points during normal handling. This isn't a "might fail under abuse" problem — it's a "might fail under normal use" problem. The manufacturing team called it and we made the change to 1.6mm on the same call.

The consequence: the total device thickness increased. But we had headroom — the 21.9mm final thickness still comes in under the 25mm hard ceiling we'd set (equal to the Flipper Zero's thickness). The ferrite sheet between the battery and NFC board contributes to this budget too, so every sub-millimeter decision compounds.

What I found interesting: this decision was made by the mechanical manufacturing team, not the electrical engineers. The antenna team and PCB layout team didn't drive it — they would have been happy to keep 1.2mm if it didn't cause problems. The manufacturing partner's job is specifically to catch things that look fine in CAD but fail in production. This is one of the reasons distributing the engineering across specialists matters.

At 1.6mm, both boards are in standard fabrication territory. Better yield, easier to source, no exotic handling required. It's also a more common stack-up for the 6-layer main board we're running.

Has anyone here had a PCB mechanical failure that traced back to thickness selection? Curious whether 1.2mm would have actually caused issues or if we were being conservative.

Subreddits sugeridos: r/electronics, r/hardwaredev, r/AskElectronics, r/embedded, r/PrintedCircuitBoard
---

## [PT-BR] Mudamos os dois PCBs de 1,2mm para 1,6mm — um número pequeno com consequências mecânicas reais

Durante a revisão de design da semana passada, nossa parceira de manufatura mecânica sinalizou algo que estava na borda da tolerância: a espessura de 1,2mm dos PCBs — tanto na placa principal quanto na sub-placa NFC/RFID — estava no limite do aceitável para o design do gabinete.

A 1,2mm, ambas as placas tinham risco real de fratura por tensão de flexão nos pontos de montagem durante o uso normal. Não é um problema de "pode falhar com abuso" — é um problema de "pode falhar com uso normal". O time de manufatura sinalizou isso e fizemos a mudança para 1,6mm na mesma call.

A consequência: a espessura total do dispositivo aumentou. Mas tínhamos margem — os 21,9mm de espessura final ainda ficam abaixo do teto rígido de 25mm que definimos (igual à espessura do Flipper Zero). O ferrite sheet entre a bateria e a placa NFC também contribui para esse orçamento, então cada decisão de sub-milímetro se acumula.

O que achei interessante: essa decisão foi tomada pelo time de manufatura mecânica, não pelos engenheiros elétricos. O time de antenas e o time de layout de PCB não a impulsionaram — eles teriam ficado felizes com 1,2mm se não causasse problemas. O trabalho do parceiro de manufatura é especificamente detectar coisas que parecem boas no CAD mas falham na produção. Esta é uma das razões pelas quais distribuir a engenharia entre especialistas importa.

A 1,6mm, ambos os PCBs estão em território de fabricação padrão. Melhor yield, mais fácil de sourcear, sem manuseio exótico necessário. É também um stack-up mais comum para a placa principal de 6 camadas que estamos usando.

Alguém aqui já teve uma falha mecânica de PCB rastreada até a seleção de espessura? Curioso saber se 1,2mm teria realmente causado problemas ou se estávamos sendo conservadores.

Subreddits sugeridos: r/electronics, r/hardwaredev, r/AskElectronics, r/embedded, r/PrintedCircuitBoard
---
