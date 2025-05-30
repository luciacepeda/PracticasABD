Realizado por Lucía Cepeda González

### SEMINARIO 2 

1. **¿Cómo se instala CLIPSPy?**  
   CLIPSPy es un wrapper de Python para trabajar con el motor de reglas CLIPS. Su instalación es muy sencilla mediante el gestor de paquetes `pip`. Solo debes ejecutar el siguiente comando en la terminal:

   ```bash
   pip install clipspy
   ```
   Este comando descarga e instala automáticamente la última versión disponible de CLIPSPy desde PyPI.

2. **¿Se pueden evaluar en Python expresiones CLIPS usando CLIPSPy? ¿Cómo?**  
   Sí, es completamente posible. CLIPSPy proporciona una interfaz que permite evaluar expresiones CLIPS directamente desde Python. Los pasos básicos son:

   * Importar el módulo `clips`.
   * Crear un entorno CLIPS con `clips.Environment()`.
   * Usar métodos como `eval()` para evaluar expresiones simples o `assert_string()` para insertar hechos.

   Ejemplo:

   ```python
   import clips
   env = clips.Environment()
   result = env.eval('(+ 3 4)')
   print(result)  # Imprime 7
   ```

3. **¿Se pueden usar funciones Python dentro de CLIPS usando CLIPSPy? ¿Cómo?**  
   Sí, CLIPSPy permite registrar funciones definidas en Python para que puedan ser llamadas desde dentro de reglas CLIPS. Esto se hace con el método `define_function` sobre el entorno CLIPS.

   Ejemplo:

   ```python
   import clips

   def saludar():
       print("Hola desde Python")

   env = clips.Environment()
   env.define_function(saludar)
   env.eval('(saludar)')
   ```

   Esta integración facilita una comunicación bidireccional entre CLIPS y Python.

4. **¿Qué métodos de CLIPSPy sirven para insertar o eliminar hechos en CLIPS?**  
      Para insertar un hecho se usa `assert_string` sobre el entorno. El hecho puede guardarse en una variable y luego eliminarse con `retract` pasándole esa misma variable.


5. **¿Cómo ejecutarías en Python un sistema de reglas guardado en un archivo `.clp` con CLIPSPy?**  
   ```python
   env = clips.Environment()
   env.load('mi_sistema.clp')
   env.reset()
   env.run()
   ```

6. **¿Cómo harías que un sistema basado en reglas `.clp` se convirtiera en un ejecutable?**  
   * En Python: escribir un script `.py` y usar `pyinstaller`:

     ```bash
     pyinstaller mi_script.py --onefile
     ```

   * En C/C++: crear un programa que use la API de CLIPS y compilarlo con `gcc`.

7. **¿Cómo incluirías una función C dentro de CLIPS?**  
   1. Defínela siguiendo las convenciones de CLIPS.
   2. Compílala como librería compartida (`.so` o `.dll`).
   3. Cárgala en CLIPS:

   ```clips
   (load "mi_funcion.so")
   ```
   
8. **¿Cómo integrarías un sistema de reglas `.clp` dentro de un programa en C?**  
   Incluyes los headers de CLIPS, creas un entorno, cargas el archivo `.clp`, haces `reset` y `run`. Al         compilar, enlazas con la biblioteca de CLIPS usando `-L` y `-lclips`.

9. **¿Qué funciones se usan en C para insertar o eliminar hechos en un entorno CLIPS?**  
    Para insertar: `EnvAssertString(env, "hecho")`, que devuelve un puntero al hecho. Para eliminar: `EnvRetract(env, puntero_hecho)`. Si no tienes el puntero, puedes obtenerlo con `FactIndex`.

10. **¿Es posible ejecutar varios sistemas de reglas diferentes en un solo programa en C?**  
   Sí. Puedes crear múltiples entornos con `CreateEnvironment()` y cargarlos con diferentes archivos `.clp`.    Así cada entorno funciona de manera independiente.

    ```c
    void *env1 = CreateEnvironment();
    void *env2 = CreateEnvironment();

    EnvLoad(env1, "reglas1.clp");
    EnvLoad(env2, "reglas2.clp");
    ```


