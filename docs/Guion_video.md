# Guion para el video de demostración

Duración objetivo: **4 minutos 30 segundos**. Límite de la tarea: 5 minutos.

## 0:00–0:30 — Presentación

> Este proyecto implementa el control de una estación de llenado, sellado e inspección de envases mediante dos máquinas de estados finitos. La primera usa arquitectura Moore y controla el proceso principal. La segunda usa arquitectura Mealy y decide si el envase se acepta o se desvía hacia rechazo.

Muestra brevemente el circuito `main` y señala los dos bloques.

## 0:30–1:20 — Entradas, salidas y estados

> Las entradas E, L y S representan presencia del envase, fin de llenado y fin de sellado. I indica que la inspección terminó, G contiene el resultado de calidad y R confirma el retiro. RST reinicia las dos máquinas y CLK actualiza sus estados.

> Moore tiene cuatro estados: espera, llenado, sellado e inspección. Sus salidas LL, SL e INS dependen únicamente del estado. Mealy tiene cuatro estados: espera del resultado, retiro aceptado, retiro rechazado y rearme. Sus salidas de movimiento pueden reaccionar directamente al sensor R.

Muestra los diagramas o las tablas mientras explicas los estados.

## 1:20–1:45 — Decisiones de construcción

> Cada FSM utiliza dos biestables D para almacenar cuatro estados. La lógica combinacional calcula el siguiente estado. La señal Q, que equivale a INS, va de Moore a Mealy. La señal F vuelve de Mealy a Moore y confirma que el envase ya salió. El estado de rearme evita clasificar dos veces el mismo envase.

Abre brevemente `Proceso_Moore` y `Clasificacion_Mealy` para mostrar los biestables y las compuertas.

## 1:45–3:00 — Envase correcto

1. Reinicia: `RST=1`, pulso de reloj, `RST=0`.
2. Pon `E=1` y da un pulso: se activa `LL`.
3. Pon `L=1` y da un pulso: se activa `SL`.
4. Baja `L`, pon `S=1` y da un pulso: se activa `INS`.
5. Baja `S`, pon `I=1`, `G=1` y da un pulso: se activa `AV`, mientras `DV=0`.
6. Baja `E` e `I`; pon `R=1` sin pulsar: aparecen `F=1` y `OK=1`, y `AV` baja.
7. Da un pulso, baja `R` y da otro pulso para completar el rearme.

> En la confirmación de retiro se observa el comportamiento Mealy: F y OK responden a R antes del siguiente pulso de reloj.

## 3:00–4:05 — Envase defectuoso

Repite rápidamente las etapas de llenado y sellado. En inspección usa `I=1` y `G=0`.

> Como G vale cero, la máquina memoriza la ruta de rechazo. Se activan AV, DV y ERR. Aunque G cambie después, el destino permanece guardado en el estado B2.

Después baja `E` e `I` y pon `R=1`.

> Al confirmar el retiro, AV y DV bajan, F sube y OK permanece apagada porque este envase fue rechazado. Después del pulso, Moore vuelve a espera y Mealy realiza su rearme.

## 4:05–4:30 — Cierre

> De esta forma, Moore controla las acciones estables de cada etapa y Mealy responde al resultado de inspección y al retiro. El repositorio incluye el archivo de Logisim, las tablas, el documento de diseño, los diagramas y los vectores de prueba. La implementación fue comprobada con 1780 pasos de prueba sin fallos.

Termina mostrando el repositorio y el circuito nuevamente en reposo.

## Recomendaciones para grabar

- Practica una vez con el cronómetro antes de grabar.
- Mantén `CLK=0` mientras cambias sensores.
- Acerca la vista lo suficiente para que se lean las señales.
- Muestra el valor de las salidas antes de dar el siguiente pulso.
- Evita explicar cada compuerta; enfócate en estados, conexiones y decisiones de diseño.
