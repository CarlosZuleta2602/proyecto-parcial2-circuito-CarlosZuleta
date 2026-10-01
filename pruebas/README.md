# Vectores de prueba

Los archivos de esta carpeta se usan con la herramienta de vectores de prueba de Logisim-evolution:

| Archivo | Circuito que debe seleccionarse | Filas |
|---|---|---:|
| `Proceso_Moore.txt` | `Proceso_Moore` de `Envases.circ` | 896 |
| `Clasificacion_Mealy.txt` | `Clasificacion_Mealy` de `Envases.circ` | 768 |
| `Sistema.txt` | `main` de `Envases_pruebas.circ` | 116 |

`Envases_pruebas.circ` contiene la misma lógica que `src/Envases.circ`. Solamente agrega nombres a los cinco monitores de salida del bloque Mealy para que la herramienta de vectores pueda encontrarlos. El archivo fuente entregado conserva el diseño visual construido por el estudiante y únicamente incorpora la realimentación `F` solicitada.
