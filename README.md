# Simulador de Datapath monociclo RISC-V

Simulador interactivo de un **datapath monociclo basado en la arquitectura RISC-V RV64I**, diseñado para visualizar y comprender el funcionamiento interno de la ejecución de instrucciones en un procesador.

La herramienta permite escribir programas en ensamblador, ejecutarlos paso a paso y observar el recorrido de los datos, las señales de control, los registros y la memoria durante las distintas etapas de ejecución.

## Características principales

- **Editor de ensamblador:** permite escribir y modificar programas RISC-V.
- **Visualización del datapath:** muestra los componentes del procesador y las rutas de datos involucradas en cada instrucción.
- **Ejecución interactiva:** incluye ejecución automática, pausa, reanudación, reinicio, avance y retroceso por etapas, y ejecución rápida.
- **Etapas de ejecución:** permite estudiar las etapas IF, ID, EX, MEM y WB.
- **Señales de control:** visualiza señales como `RegWrite`, `ALUSrc`, `MemRead`, `MemWrite`, `MemtoReg`, `PCSrc` y `ALUop`.
- **Banco de registros:** permite consultar los 32 registros y visualizar sus valores en decimal, hexadecimal o sin signo.
- **Memoria de datos:** muestra los cambios producidos por las instrucciones de lectura y escritura.
- **Historial de ejecución:** registra las instrucciones ejecutadas y sus resultados.
- **Diagnóstico de errores:** detecta instrucciones no soportadas, errores de sintaxis, registros inválidos, inmediatos fuera de rango y problemas de acceso a memoria.
- **Ejemplos integrados:** incluye programas de operaciones aritméticas y lógicas, acceso a memoria, bucles y errores.
- **Extensiones opcionales:** permite habilitar instrucciones adicionales cuyo hardware se considera inferido.
- **Personalización visual:** ofrece temas claro y oscuro, zoom del datapath y niveles de detalle.
- **Pruebas automáticas:** incluye pruebas para verificar el comportamiento del motor de simulación.

## Instrucciones soportadas

El simulador implementa un subconjunto de instrucciones RISC-V, organizado por tipo.

| Tipo | Instrucciones |
|---|---|
| Aritméticas y lógicas tipo R | `add`, `sub`, `and`, `or`, `xor`, `slt` |
| Tipo I | `addi`, `andi`, `ori`, `xori`, `slti` |
| Carga de memoria | `ld` |
| Almacenamiento en memoria | `sd` |
| Bifurcación | `beq` |
| Extensiones opcionales | `sll`, `srl`, `sra`, `slli`, `srli`, `srai`, `lw`, `sw`, `bne`, `blt`, `bge` |

Las extensiones opcionales se encuentran desactivadas inicialmente y requieren habilitar el control correspondiente en la interfaz.

**Importante:** el simulador no implementa el conjunto completo de instrucciones RISC-V. Su objetivo es representar y explicar un subconjunto de operaciones de un datapath monociclo.

## Requisitos

- Un navegador web moderno, como Google Chrome, Mozilla Firefox, Microsoft Edge o Safari.
- El archivo HTML del simulador.

No es necesario instalar Python, Node.js, compiladores ni dependencias adicionales para utilizar la aplicación localmente.

## Ejecución

[text](https://candid-marzipan-c59178.netlify.app)

## Cómo utilizar el simulador

1. **Cargar un programa:** escribe las instrucciones en el editor o selecciona un ejemplo.
2. **Ejecutar:** inicia la simulación animada del programa.
3. **Avanzar por etapas:** utiliza los controles de paso anterior, paso siguiente y siguiente instrucción.
4. **Analizar el datapath:** observa los componentes activos y las rutas que recorren los datos.
5. **Consultar las señales:** revisa las señales de control asociadas a la instrucción actual.
6. **Inspeccionar los registros y la memoria:** comprueba cómo cambian los valores después de ejecutar las instrucciones.
7. **Revisar errores e historial:** identifica problemas en el programa y consulta las operaciones ejecutadas.

## Ejemplo de programa

```asm
addi x5, x0, 15
addi x6, x0, 4
add  x7, x5, x6
sub  x8, x5, x6
```

Este programa realiza las siguientes operaciones:

- Asigna el valor `15` al registro `x5`.
- Asigna el valor `4` al registro `x6`.
- Suma los valores de `x5` y `x6`, almacenando `19` en `x7`.
- Resta el valor de `x6` al de `x5`, almacenando `11` en `x8`.

Al ejecutarlo, es posible observar cómo cada instrucción recorre las etapas del datapath y cómo se actualiza el banco de registros.

## Pruebas automáticas

La aplicación incluye un botón **Ejecutar pruebas** que permite comprobar diferentes aspectos del motor de simulación, entre ellos:

- Operaciones aritméticas y lógicas.
- Comportamiento del registro `x0`.
- Lectura y escritura de memoria.
- Ejecución de bifurcaciones.
- Validación de registros e inmediatos.
- Detección de instrucciones no soportadas.
- Accesos a memoria inválidos o desalineados.
- Coherencia entre la ejecución y la visualización del datapath.

La interfaz muestra los resultados de las pruebas ejecutadas. La animación y los controles visuales también deben comprobarse manualmente.

## Tecnologías utilizadas

- **HTML5:** estructura de la aplicación.
- **CSS3:** diseño adaptable, temas visuales, animaciones y estilos.
- **JavaScript:** ensamblador simplificado, motor de ejecución, simulación de registros y memoria, controles interactivos y pruebas automáticas.
- **SVG:** representación gráfica del datapath y sus conexiones.

El proyecto está contenido en un archivo HTML que integra la estructura, los estilos y la lógica de simulación.

## Alcance y limitaciones

- La representación gráfica del datapath es conceptual y no constituye una reconstrucción exacta de un procesador físico.
- Solo se implementa