# CMD & Powershell cheat codes

- [CMD \& Powershell cheat codes](#cmd--powershell-cheat-codes)
  - [Comandos para eliminar archivos en una carpeta y sus subcarpetas usando CMD y Powershell en Windows 10](#comandos-para-eliminar-archivos-en-una-carpeta-y-sus-subcarpetas-usando-cmd-y-powershell-en-windows-10)
    - [PowerShell: eliminar los archivos `desktop.ini` en una carpeta y sus subcarpetas](#powershell-eliminar-los-archivos-desktopini-en-una-carpeta-y-sus-subcarpetas)
    - [CMD: Eliminar los archivos "desktop.ini" en una sola línea en una carpeta y sus subcarpetas](#cmd-eliminar-los-archivos-desktopini-en-una-sola-línea-en-una-carpeta-y-sus-subcarpetas)
    - [CMD: Eliminar los archivos "desktop.ini" ocultos en una sola línea en una carpeta y sus subcarpetas](#cmd-eliminar-los-archivos-desktopini-ocultos-en-una-sola-línea-en-una-carpeta-y-sus-subcarpetas)
    - [PowerShell: eliminar todas las carpetas vacías y sus subcarpetas en una ruta específica](#powershell-eliminar-todas-las-carpetas-vacías-y-sus-subcarpetas-en-una-ruta-específica)

## Comandos para eliminar archivos en una carpeta y sus subcarpetas usando CMD y Powershell en Windows 10

Estos apuntes tienen como ejemplo eliminar uno o varios archivos llamados `desktop.ini` en una carpeta y sus subcarpetas, pero sirve de ejemplo para poder hacer lo mismo con cualquier otro tipo de archivo que cumpla estas condiciones en la estructura de las carpetas.

### PowerShell: eliminar los archivos `desktop.ini` en una carpeta y sus subcarpetas

```powershell
Get-ChildItem -Path "RUTA_DE_LA_CARPETA" -Filter desktop.ini -File -Recurse | ForEach-Object { Remove-Item $_.FullName -Force }
```

Asegúrate de reemplazar `"RUTA_DE_LA_CARPETA"` con la ruta de la carpeta principal donde deseas buscar y eliminar los archivos `desktop.ini`.

Este comando buscará recursivamente todos los archivos `desktop.ini` dentro de la carpeta especificada y sus subcarpetas, y luego los eliminará utilizando `Remove-Item` con la opción `-Force` para forzar la eliminación sin pedir confirmación.

Si encuentras problemas con los permisos, podría ser necesario ejecutar PowerShell como administrador para asegurar los privilegios necesarios para eliminar estos archivos.

### CMD: Eliminar los archivos "desktop.ini" en una sola línea en una carpeta y sus subcarpetas

```shell
cd /d "RUTA_DE_LA_CARPETA" & del /s /q desktop.ini
```

### CMD: Eliminar los archivos "desktop.ini" ocultos en una sola línea en una carpeta y sus subcarpetas

```shell
cd /d "RUTA_DE_LA_CARPETA" & attrib -h -s /s /d desktop.ini & del /s /q desktop.ini
```

Este comando se ejecuta en el Símbolo del sistema (CMD) y realiza varias operaciones en una sola línea.

Aquí está desglosado paso a paso:

1. `cd /d "RUTA_DE_LA_CARPETA"`: Cambia el directorio de trabajo (`cd`) al especificado después de `/d`. Reemplaza `"RUTA_DE_LA_CARPETA"` con la ruta de la carpeta principal donde se encuentran los archivos `desktop.ini`. La opción `/d` es para cambiar la unidad de disco en caso de que la ruta sea de una unidad diferente.

2. `&`: Es un operador utilizado para ejecutar múltiples comandos en una sola línea. En este caso, se utiliza para separar las diferentes operaciones a realizar.

3. `attrib -h -s /s /d desktop.ini`: Este comando `attrib` modifica los atributos de los archivos `desktop.ini`. Explicando cada parte:

   - `-h -s`: Quita los atributos de oculto (`-h`) y de sistema (`-s`) de los archivos.
   - `/s`: Realiza la operación de manera recursiva en todas las subcarpetas.
   - `/d`: Procesa carpetas también.
   - `desktop.ini`: Especifica el nombre del archivo para el que se están cambiando los atributos.

4. `&`: Nuevamente, este operador `&` permite ejecutar otro comando en la misma línea.

5. `del /s /q desktop.ini`: Este comando `del` elimina (`del`) de forma recursiva (`/s`) y silenciosa (`/q`, sin pedir confirmación) todos los archivos `desktop.ini`.

En resumen, esta línea de comando ejecuta tres acciones consecutivas:

- Cambia al directorio especificado.
- Quita los atributos de oculto y de sistema de los archivos `desktop.ini` en esa carpeta y sus subcarpetas.
- Elimina todos los archivos `desktop.ini` de manera recursiva sin pedir confirmación.

### PowerShell: eliminar todas las carpetas vacías y sus subcarpetas en una ruta específica

```powershell
Get-ChildItem -Path "C:\ruta\inicial\a\analizar" -Directory -Recurse | Where { $_.GetFileSystemInfos().Count -eq 0 } | Remove-Item -Force -Recurse
```

Reemplaza `"C:\ruta\inicial\a\analizar"` con la ruta de la carpeta principal donde deseas eliminar las carpetas vacías y sus subcarpetas.

Este comando `Get-ChildItem` busca todas las carpetas y subcarpetas en la ruta proporcionada, el `Where` filtra las carpetas que tienen un conteo de archivos y subcarpetas igual a cero (es decir, están vacías) y finalmente `Remove-Item` elimina esas carpetas vacías.

> Por favor, ten cuidado al ejecutar este tipo de comandos, ya que eliminará permanentemente las carpetas vacías sin posibilidad de recuperación. Asegúrate de especificar la ruta correcta para evitar la pérdida accidental de datos.

Está es la explicación paso a paso del código de PowerShell:

1. **Get-ChildItem**: Este cmdlet de PowerShell se utiliza para obtener elementos (archivos, carpetas) en una ubicación específica.

2. `-Path "C:\ruta\inicial\a\analizar"`: Este argumento especifica la ruta donde se buscarán las carpetas vacías y sus subcarpetas. Reemplaza esta ruta con la ubicación real que quieres analizar.

3. `-Directory`: Este parámetro le dice a `Get-ChildItem` que solo seleccione carpetas (directorios) en lugar de archivos.

4. `-Recurse`: Este modificador permite que el comando busque de manera recursiva en todas las subcarpetas.

5. `Where { $_.GetFileSystemInfos().Count -eq 0 }`: Después de obtener todas las carpetas y subcarpetas, este filtro `Where` selecciona solo aquellas carpetas que tienen un conteo de elementos (archivos y subcarpetas) igual a cero. Esto identifica las carpetas vacías.

6. `Remove-Item -Force -Recurse`: Una vez que se identifican las carpetas vacías, `Remove-Item` se utiliza para eliminarlas. `-Force` indica que se eliminarán sin pedir confirmación y `-Recurse` asegura que las subcarpetas vacías también se eliminarán.

En resumen, el código busca todas las carpetas vacías y sus subcarpetas en una ruta determinada y las elimina sin solicitar confirmación. Recuerda que la eliminación es permanente y no se pueden recuperar las carpetas y archivos eliminados. Asegúrate de utilizarlo en la ruta correcta y con cuidado para evitar pérdida de datos no deseada.

