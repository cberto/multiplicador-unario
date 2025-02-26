## Máquinas de Turing: Multiplicación en Unario y Conversión a Binario

A continuación, se presentará una Máquina de Turing que realiza la multiplicación de dos números en representación unaria y luego convierte el resultado a binario.

- **Nombre**: "Máquina de Turing para la Multiplicación Unaria"
- **Función que computa**: La máquina toma dos números en unario, representados por secuencias de 1s separadas por #, y calcula su producto en representación unaria
  Por ejemplo:

| Entrada (unaria) | Salida (unaria) |
| ---------------- | --------------- |
| 111#11 (3×2)     | 111111 (6)      |
| 11#11 (2×2)      | 1111 (4)        |
| 111#111 (3×3)    | 111111111 (9)   |

**Descripción y estrategia**: La entrada consta de dos números en unario separados por #.

Copia del Primer Factor: Se recorren los 1s del primer factor y se duplican en la posición correspondiente para cada 1 del segundo factor.

Marcado y Reubicación: Se usa el símbolo X para marcar las operaciones intermedias y el símbolo C para gestionar el cómputo.

Resultado Final: Se construye la salida en el mismo espacio de la cinta y se eliminan los símbolos auxiliares.

- **Formalismo**: MT = < Г, Σ, b, Q, q_0, F, δ>

  - **Alfabeto de la cinta**: Г = {1, #, X, C, b}
  - **Alfabeto de entrada**: Σ = {1, #}
  - **Símbolo blanco**: b = b
  - **Conjunto de estados**:  
    Q = {q0, q1, q2, q3, q4, q5, q6, q7, q8, q9, q10, q11, q12, q13, q14, q15, q16, q17, q18, q19, q20, q21, q22, q23, q24, q25, q26, q27, q28, q29, q30, q31, q32, q33, q34, q35}

  - **Estado inicial**: q0 = q0
  - **Estados finales**: F = {q4, q8, q14, q19, q29}
  - **Transiciones**:  
    δ = {

    - δ(q0, 1) = (q1, b, R)

    - δ(q1, #) = (q2, 1, R)
    - δ(q1, 1) = (q5, 1, R)
    - δ(q1, b) = (q1, b, R)

    - δ(q2, 1) = (q2, b, R)
    - δ(q2, b) = (q3, b, L)

    - δ(q3, 1) = (q4, 1, S)
    - δ(q3, b) = (q3, b, L)

    - δ(q5, #) = (q6, b, L)
    - δ(q5, 1) = (q9, 1, R)

    - δ(q6, 1) = (q6, b, L)
    - δ(q6, b) = (q7, b, R)

    - δ(q7, 1) = (q8, 1, S)
    - δ(q7, b) = (q7, b, R)

    - δ(q9, #) = (q10, #, R)
    - δ(q9, 1) = (q9, 1, R)

    - δ(q10, 1) = (q11, X, R)

    - δ(q11, 1) = (q15, X, R)
    - δ(q11, b) = (q12, b, L)

    - δ(q12, #) = (q13, b, L)
    - δ(q12, X) = (q12, b, L)

    - δ(q13, 1) = (q13, b, L)
    - δ(q13, b) = (q14, 1, S)

    - δ(q15, 1) = (q20, X, R)
    - δ(q15, b) = (q16, b, L)

    - δ(q16, #) = (q17, 1, L)
    - δ(q16, X) = (q16, b, L)

    - δ(q17, 1) = (q18, 1, L)

    - δ(q18, 1) = (q18, 1, L)
    - δ(q18, b) = (q19, b, R)

    - δ(q20, 1) = (q20, X, R)
    - δ(q20, b) = (q21, b, L)

    - δ(q21, X) = (q22, b, L)

    - δ(q22, #) = (q23, #, L)
    - δ(q22, X) = (q22, X, L)

    - δ(q23, 1) = (q24, 1, L)

    - δ(q24, 1) = (q24, 1, L)
    - δ(q24, b) = (q25, b, R)

    - δ(q25, 1) = (q26, b, R)

    - δ(q26, #) = (q27, 1, R)
    - δ(q26, 1) = (q30, 1, R)

    - δ(q27, 1) = (q28, 1, L)
    - δ(q27, X) = (q27, 1, R)

    - δ(q28, 1) = (q28, 1, L)
    - δ(q28, b) = (q29, b, R)

    - δ(q30, #) = (q31, #, R)
    - δ(q30, 1) = (q30, 1, R)

    - δ(q31, X) = (q32, C, R)

    - δ(q32, 1) = (q32, 1, R)
    - δ(q32, C) = (q32, C, R)
    - δ(q32, b) = (q33, 1, L)
    - δ(q32, X) = (q32, X, R)

    - δ(q33, #) = (q34, #, R)
    - δ(q33, 1) = (q33, 1, L)
    - δ(q33, C) = (q33, C, L)
    - δ(q33, X) = (q32, C, R)

    - δ(q34, 1) = (q35, 1, L)
    - δ(q34, C) = (q34, X, R)

    - δ(q35, #) = (q23, #, L)
    - δ(q35, X) = (q35, X, L)
      }

**Conversión del Resultado Unario a Binario**

Una vez obtenida la multiplicación en unario, se aplica la conversión a binario utilizando el método de divisiones sucesivas por 2, similar al procedimiento descrito en la primera máquina.

**Conversión del Resultado Unario a Binario**

| Unario (Resultado de Multiplicación) | binario |
| ------------------------------------ | ------- |
| 1                                    | 0       |
| 11                                   | 1       |
| 111                                  | 2       |
| 1111                                 | 3       |
| 11111                                | 4       |
| 111111                               | 5       |
| 1111111                              | 6       |
| 11111111                             | 7       |
| 111111111                            | 8       |

- **Diseño en JFlap**: ![Diseño JFlap](./resources/jflap.png)
- **Comprobaciones**:
  ![picture 0](./resources/comprobaciones.png)
- **Programa Simulator**: [Programa Simulator](http://turingmachinesimulator.com/shared/vitfcuxush)
- **Programa Prolog**: [Programa Prolog](./resources/multiplicacion_unario.pl)

- **Complejidad temporal**: 𝑂(𝑛), exprésado en términos de 𝑛 = 4 + 19 transiciones (máximo)
- **Complejidad espacial**: Si esta máquina de Turing utiliza 𝑛 = 3 + 4 celdas, entonces la complejidad espacial es 𝑂(𝑛)

### Complejidad Espacial

La máquina de Turing requiere un espacio proporcional a la longitud de la entrada y del resultado. Dado que la multiplicación en unario produce una salida de tamaño m × n para entradas de tamaño m y n, la complejidad espacial es:

O(m × n).

### Complejidad Temporal

El tiempo de ejecución depende de los pasos requeridos para replicar el primer operando tantas veces como indique el segundo operando y limpiar la cinta. Cada 1 en el primer operando debe procesarse por cada 1 en el segundo operando, por lo que el número de transiciones es proporcional a la multiplicación.

O(m × n) en la peor caso.

La conversión de unario a binario, basada en divisiones sucesivas, tiene una complejidad de O(log(m × n)).

### Conclusión

Esta máquina de Turing implementa la multiplicación unaria de manera eficiente dentro del marco de máquinas de Turing, aunque la representación unaria hace que el crecimiento del tamaño de la salida sea exponencial en comparación con la representación binaria. La conversión final a binario permite un almacenamiento más compacto y un procesamiento más eficiente en etapas posteriores.
