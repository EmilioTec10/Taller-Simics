# Academia Collaboration - Simics Project

Este proyecto proporciona un entorno de trabajo para la simulación y ejecución de código ensamblador, incluyendo la visualización del Triángulo de Pascal en un entorno de simulación. A continuación, se detallan los pasos para configurar el espacio de trabajo y ejecutar el código.

## Requisitos Previos

- **Simics 6.X.X**: Asegúrese de que Simics está instalado y configurado correctamente.
- **NASM (Netwide Assembler)**: Necesario para ensamblar el archivo de código `Pascal.asm`.

## Pasos para Configurar el Espacio de Trabajo

1. **Clonar el Repositorio**
   Acceda a [este enlace del repositorio](https://github.com/mmongeo/academia-collaboration) y clone o descargue el repositorio a su máquina local.

2. **Moverse a la Carpeta de Simics Project**
   Abra una terminal y navegue a la carpeta `simics-project` dentro del repositorio descargado.

3. **Crear el Espacio de Trabajo de Simics**
   Desde la carpeta `simics-project`, ejecute el binario `project-setup` para configurar el entorno de trabajo de Simics, utilizando el siguiente comando:

```bash
    cd simics-project ../instalation-directory/simics-6.X.X/bin/project-setup --ignore-existing-files
```

Esto creará un nuevo espacio de trabajo y habilitará algunos archivos del repositorio necesarios para el ejercicio.

4. **Verificar la Ejecución de Simics**
Ejecute el siguiente comando para verificar que Simics funciona correctamente desde la carpeta `simics-project`:

```bash
./simics
```

Si Simics se ejecuta sin problemas, puede salir de la simulación.

## Pasos para Ejecutar el Triángulo de Pascal

### 1. Compilar el Código

Compile el archivo de código ensamblador en un archivo binario con el siguiente comando en la terminal:

```bash
nasm Pascal.asm -o Pascal.bin
```


Esto generará un archivo llamado `Pascal.bin` en el directorio actual.

### 2. Iniciar Simics

Inicie Simics con el siguiente comando:


```bash
./simics targets/qsp-x86/lfsr.simics
```

Esto abrirá la consola de Simics.

### 3. Cargar el Archivo en Simics

Dentro de la consola de Simics, cargue el archivo binario en memoria con el siguiente comando:

```bash
load-file filename=Pascal.bin offset=0x100
```

Este comando cargará `Pascal.bin` en la dirección de memoria `0x100`.

### 4. Configurar Ventanas para Visualización

En la interfaz de Simics, seleccione la pestaña **Debug** y habilite las ventanas **Disassembly** y **Memory**. Esto le permitirá observar el código desensamblado y el contenido de la memoria durante la ejecución del programa.

### 5. Ejecución Paso a Paso del Código

Para ejecutar el código paso a paso:

- Use el comando `stepi` en la consola de Simics para avanzar instrucción por instrucción.
- Alternativamente, puede hacer clic en el botón **Step** en la ventana **Disassembly** para avanzar una instrucción a la vez.
- Para avanzar rápidamente hasta el final del programa, haga clic en la instrucción `syscall` en la ventana **Disassembly** y seleccione **Run Forward Until**. Esto le permitirá ver el resultado final en la ventana **Memory**.

## Visualización del Triángulo de Pascal en Memoria

El Triángulo de Pascal se almacena en memoria desde la dirección `0x100`. Los valores están organizados de izquierda a derecha, con tres espacios vacíos entre cada valor. Puede visualizar esta disposición en la ventana **Memory** de Simics, que muestra los valores de manera continua desde la dirección base especificada.

## Contribuciones

Las contribuciones a este proyecto son bienvenidas. Para contribuir:

1. Realice un **fork** del repositorio.
2. Cree una nueva **rama** para sus cambios.
3. Envíe un **pull request** detallando los cambios realizados.

---

**Nota:** Asegúrese de que `Pascal.asm` y los demás archivos necesarios del repositorio están en su lugar antes de iniciar los pasos de compilación y ejecución.
