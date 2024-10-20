# Guía para subir un repositorio a GitHub

## 1. Configurar tu cuenta de GitHub en Git

Antes de comenzar, asegúrate de que Git esté configurado con tu nombre de usuario y correo electrónico de GitHub. Este paso es necesario para registrar tus cambios correctamente.

```bash
# Configurar tu correo electrónico
git config --global user.email "escribe_tu_correo"

# Configurar tu nombre de usuario
git config --global user.name "escribe_tu_usuario"
```

**Nota:** El correo electrónico y nombre de usuario deben coincidir con los de tu cuenta de GitHub.

---

## 2. Inicializar un repositorio en tu proyecto local

Navega hasta la carpeta de tu proyecto y ejecuta los siguientes comandos para inicializar el repositorio y realizar el primer commit.

```bash
# Inicializar el repositorio local
git init

# Verificar el estado de los archivos en tu carpeta (opcional)
git status

# Añadir todos los archivos al repositorio
git add .

# Confirmar los cambios con un mensaje de commit
git commit -m "Se agrega el proyecto inicial"
```

---

## 3. Crear el repositorio en GitHub

Antes de continuar, asegúrate de haber creado un nuevo repositorio en GitHub desde la interfaz web, sin ningún archivo inicial. Una vez que lo hayas creado, obtendrás la URL del repositorio (por ejemplo: `https://github.com/tu_usuario/nombre_de_repositorio.git`).

---

## 4. Vincular tu repositorio local con el remoto

Ahora necesitas vincular tu repositorio local con el repositorio remoto en GitHub.

```bash
# Cambiar el nombre de la rama principal a 'main' (opcional, si no se ha hecho ya)
git branch -M main

# Añadir el repositorio remoto (reemplaza la URL con la de tu propio repositorio)
git remote add origin https://github.com/tu_usuario/nombre_de_repositorio.git
```

---

## 5. Subir el proyecto a GitHub

Una vez que has enlazado el repositorio remoto, puedes subir tus archivos.

```bash
# Enviar los cambios locales al repositorio remoto
git push -u origin main
```

**Nota:** El parámetro `-u` solo es necesario la primera vez para establecer la rama principal de seguimiento. En los siguientes `git push` no será necesario especificarlo.

---

## 6. Hacer cambios en el proyecto y subirlos a GitHub

Cuando realices cambios adicionales en tu proyecto, sigue estos pasos para registrarlos y subirlos.

### 6.1 Registrar los nuevos cambios

```bash
# Ver el estado de los archivos
git status

# Añadir los archivos modificados o nuevos
git add .

# Confirmar los cambios con un mensaje descriptivo
git commit -m "Descripción de los cambios realizados"
```

### 6.2 Subir los nuevos cambios al repositorio

```bash
# Subir los nuevos commits al repositorio remoto
git push
```

---

### Consejos adicionales:

- **Mensajes de commit:** Es recomendable usar mensajes descriptivos y breves en inglés, como "Fix bug in login module" o "Update README".
- **Añadir archivos específicos:** Si no deseas añadir todos los archivos, puedes añadir solo los específicos, por ejemplo: `git add archivo.txt`.
- **Ignorar archivos:** Si hay archivos que no deseas incluir en el repositorio (como archivos de configuración locales), usa un archivo `.gitignore`.




