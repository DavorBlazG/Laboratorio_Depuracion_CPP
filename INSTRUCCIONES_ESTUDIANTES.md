# Laboratorio: diagnosticar un programa en C++
**Curso:** Introducción a la Programación — Ciberseguridad

## Misión
Seis pequeños programas de un sistema de seguridad contienen defectos. Algunos ni siquiera compilan; otros compilan y entregan resultados equivocados. Su trabajo consiste en identificar y explicar la causa del error, corregir el código y comprobarlo con los casos de prueba.

## Método obligatorio
1. Leer el comportamiento esperado. Formular una hipótesis antes de modificar el programa.
2. Intentar compilar y ejecutar el archivo en Visual Studio (configuración Debug).
3. Si compila, colocar un breakpoint (F9), iniciar con F5 y avanzar con F10. Consultar las variables en **Depurar > Ventanas > Variables locales** o **Inspección** (Watch).
4. Anotar cuál fue la variable, expresión o instrucción que produjo el comportamiento incorrecto.
5. Corregir el mínimo necesario. Para los casos que piden validación de entradas, añadirla.
6. Ejecutar **todos** los casos de prueba indicados; ampliar con al menos una prueba propia.
7. Registrar el diagnóstico y las pruebas en `INFORME_EQUIPO.md`.

**Importante:** cada archivo contiene su propio `main()`. Compilar un caso por proyecto, o excluir de la compilación los demás archivos `.cpp` (varios `main()` provocarían un error del enlazador).

## Casos y criterios de aceptación

### 01 · El registro de alertas [Inicial]
Debe compilar e imprimir:
`Alertas registradas: 3` y `Estado: ATENCION`.

### 02 · Control de PIN [Inicial]
El PIN correcto es 2468. Con `2468`, debe mostrar `Acceso permitido`.
Con `1357` y con `0000`, debe mostrar `Acceso denegado`.
Se asume una entrada entera.

### 03 · Acumulador de alertas [Intermedio]
Pide las alertas registradas durante tres minutos. Debe mostrar la **suma de los tres valores**.
Pruebas: `2 5 4` -> total `11`; `0 0 0` -> total `0`; `7 1 2` -> total `10`.
Se asumen valores enteros no negativos.

### 04 · Política de puertos [Intermedio]
La política permite únicamente puertos **entre 1000 y 2000 inclusive**.
Pruebas: `80` -> fuera; `1000` -> dentro; `1500` -> dentro; `2000` -> dentro; `3000` -> fuera.
Se asume un número de puerto válido entre 0 y 65535.

### 05 · Porcentaje de paquetes sospechosos [Intermedio/Avanzado]
Se introducen dos números enteros en este orden: paquetes totales y paquetes sospechosos.
Calcular el porcentaje real `100 * sospechosos / total`, sin truncar la división entera.
Si el porcentaje es **20% o superior**, imprimir `ALERTA: trafico sospechoso`.
Pruebas: `20 3` -> `15%` y tráfico normal; `10 2` -> `20%` y alerta; `5 4` -> `80%` y alerta.
Casos límite: `0 0` -> `Sin paquetes para analizar`; `5 6` -> `Datos invalidos`.

### 06 · Racha de fallos de autenticación [Avanzado]
Introducir exactamente seis eventos: `1` significa fallo, `0` significa acceso correcto.
El programa debe calcular la **racha máxima de fallos consecutivos**; cuando la racha alcanza **3 o más**, mostrar una alerta.
Pruebas:
- `1 1 1 0 1 0` -> racha máxima `3` y alerta.
- `1 0 1 0 1 0` -> racha máxima `1` y sin alerta.
- `1 1 1 1 0 0` -> racha máxima `4` y alerta.
Se asume que cada entrada es 0 o 1.

## Evidencia a entregar
En el repositorio GitHub de ejercicios, dentro de `Semana_5_6/Depuracion/`:
- Código `.cpp` corregido de cada caso asignado.
- `INFORME_EQUIPO.md` con el siguiente esquema para cada caso:
  - **Comportamiento esperado**
  - **Qué ocurrió antes de corregir**
  - **Hipótesis inicial**
  - **Error localizado** (explicar la causa, no limitarse a indicar una línea)
  - **Variables observadas** con breakpoint/Watch/Locals
  - **Pruebas ejecutadas**: entrada y salida observada
  - **Explicación de la corrección**
  - **Una prueba propia**

Cada integrante debe poder justificar oralmente la solución. No se evalúa únicamente que el programa compile.
