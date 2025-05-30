Realizado por Lucía Cepeda González

### SEMINARIO 2 
---

1. **¿Cómo se instala CLIPSPy?**  
   Puedes instalar CLIPSPy con el comando `pip install clipspy` en cualquier sistema operativo compatible con Python.

2. **¿Se pueden evaluar en Python expresiones CLIPS usando CLIPSPy? ¿Cómo?**  
   Sí, es posible. Primero se importa el módulo `clips`, se crea un entorno (`Environment()`), y luego se llama a `eval()` o `assert_string()` en dicho entorno para evaluar la expresión CLIPS.

3. **¿Se pueden usar funciones Python dentro de CLIPS usando CLIPSPy? ¿Cómo?**  
   Sí. Primero defines la función en Python, creas un entorno CLIPS y luego registras la función con `add_python_function`. Así, puede ser invocada desde CLIPS.

4. **¿Qué métodos de CLIPSPy sirven para insertar o eliminar hechos en CLIPS?**  
   Para insertar un hecho se usa `assert_string` sobre el entorno. El hecho puede guardarse en una variable y luego eliminarse con `retract` pasándole esa misma variable.

5. **¿Cómo ejecutarías en Python un sistema de reglas guardado en un archivo .clp con CLIPSPy?**  
   Se crea un entorno, se carga el fichero con `load`, se hace un `reset` y luego se ejecuta con `run`.

6. **¿Cómo harías que un sistema basado en reglas .clp se convirtiera en un ejecutable?**  
   Si estás usando Python, puedes hacer un script que lo cargue y ejecute. En C o C++, puedes compilar un programa que use la biblioteca de CLIPS y lea el archivo `.clp` para ejecutarlo.

7. **¿Cómo incluirías una función C dentro de CLIPS?**  
   La defines siguiendo las convenciones de CLIPS, la compilas como una librería compartida y la cargas en CLIPS con `load`. Una vez cargada, la puedes llamar desde tus reglas.

8. **¿Cómo integrarías un sistema de reglas .clp dentro de un programa en C?**  
   Incluyes los headers de CLIPS, creas un entorno, cargas el archivo `.clp`, haces `reset` y `run`. Al compilar, enlazas con la biblioteca de CLIPS usando `-L` y `-lclips`.

9. **¿Qué funciones se usan en C para insertar o eliminar hechos en un entorno CLIPS?**  
   Para insertar: `EnvAssertString(env, "hecho")`, que devuelve un puntero al hecho. Para eliminar: `EnvRetract(env, puntero_hecho)`. Si no tienes el puntero, puedes obtenerlo con `FactIndex`.

10. **¿Es posible ejecutar varios sistemas de reglas diferentes en un solo programa en C?**  
    Sí. Puedes crear múltiples entornos con `CreateEnvironment()` y cargarlos con diferentes archivos `.clp`. Así cada entorno funciona de manera independiente.
