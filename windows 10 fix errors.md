# Solución para algunos errores en Windows 10

Nota: Estos códigos son una solución general para algunos problemas en Windows. No esperes una solución garantizada si previamente no has investigado la naturaleza del problema de tu sistema.

## 1. Entrar a modo seguro

Una manera sencilla es abrir **Símbolo del Sistema (CMD)** como administrador. Hay muchas maneras de abrirlo, pero lo más clásico en usar la ventana de ejecutar **Windows + R** y escribir `cmd` y **aceptar**.

Para activar el modo seguro escribimos la siguiente línea de código:

```shell
    bcdedit /set {default} safeboot minimal
```

## 2. Reiniciar Windows y arrancar en modo seguro

Observar que en cmd también se puede programar el reinicio si se desea:

<table>
   <tr>
   <th> Ejecución inmediata </th>
   <th> Ejecución programada </th>
   </tr>
   <tr>
   <td>

```shell
#inmediato
#Apagar
shutdown -s
#Reiniciar
shutdown -r
#Hibernar
shutdown -h
#Cerrar sesión
shutdown -l
```

</td>
<td>

```shell
#3600s = 1h
#Apagar
shutdown -s -t 3600
#Reiniciar
shutdown -r -t 3600
#Hibernar
shutdown -h -t 3600
#Cerrar sesión
shutdown -l -t 3600
```

</td>
</tr>
</table>

> **OJO** que hemos activado el modo seguro para que siempre que arranquemos el sistema arranque como modo seguro. Así que cuando hayamos reiniciado el sistema en modo seguro vamos a desactivarlo para que el siguiente reinicio vuelva Windows en modo normal.

Entonces, para desactivar el modo seguro y restaurar el modo normal escribimos:

```shell
bcdedit /deletevalue {default} safeboot
```

## 3. Escribimos en cmd el código para reparar Windows

```shell
sfc /scannow

dism /online /cleanup-image /restorehealth

chkdsk c: /f

chkdsk c: /f /r
```

## 4. Reinicio y regresar al Modo Normal

Solo hace falta reiniciar y Windows se encargará de ejecutar `chkdsk` en el disco C antes de arrancar el sistema. Cuando termine ya debería de solucionarse el problema.
