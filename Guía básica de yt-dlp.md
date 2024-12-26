# Guía básica de yt-dlp: comandos prácticos

Algunos comandos útiles.

## 1. Ejemplo básico

```bash
yt-dlp --add-metadata --embed-thumbnail URL
```

### ¿Qué hace este comando?

- **`--add-metadata`**: Agrega información adicional, como el título, el autor y la fecha, al archivo descargado.
- **`--embed-thumbnail`**: Inserta la miniatura del video en el archivo descargado, ideal para organizadores multimedia.
- **`URL`**: Aquí debes reemplazar "URL" por el enlace de un video o su código.

### Ejemplos de URLs válidas:

1. URL completa: `https://www.youtube.com/watch?v=dQw4w9WgXcQ`
2. Enlace corto: `https://youtu.be/dQw4w9WgXcQ`
3. Solo el código del video: `dQw4w9WgXcQ`

### También puedes usar el código directamente en el comando:

```bash
yt-dlp https://youtu.be/dQw4w9WgXcQ  
yt-dlp --add-metadata dQw4w9WgXcQ  
```

## 2. Descargar con mejor calidad (video y audio)

Si quieres descargar la mejor calidad posible, utiliza:

```bash
yt-dlp -f bestvideo+bestaudio URL
```

### Variantes útiles:

1. **Con metadatos:**

   ```bash
   yt-dlp -f bestvideo+bestaudio --add-metadata URL  
   ```
2. **Con miniatura:**

   ```bash
   yt-dlp -f bestvideo+bestaudio --add-metadata --embed-thumbnail URL  
   ```

## 3. Mejor calidad con subtítulos y sin chat en vivo

Si buscas el mejor archivo de video/audio, con todos los subtítulos y sin los comentarios en vivo, usa:

```bash
yt-dlp -f bestvideo+bestaudio --sub-langs all --embed-subs --compat-options no-live-chat --add-metadata URL  
```

### Para agregar miniatura al video:

```bash
yt-dlp -f bestvideo+bestaudio --sub-langs all --embed-subs --compat-options no-live-chat --add-metadata --embed-thumbnail URL  
```

## 4. Subtítulos automáticos en inglés y español

Si solo quieres subtítulos generados automáticamente en inglés y español:

```bash
yt-dlp -f bestvideo+bestaudio --embed-subs --write-auto-subs --sub-langs en-orig,es-orig --compat-options no-live-chat --add-metadata URL  
```

### Con miniatura:

```bash
yt-dlp -f bestvideo+bestaudio --embed-subs --write-auto-subs --sub-langs en-orig,es-orig --compat-options no-live-chat --add-metadata --embed-thumbnail URL  
```

## 5. Descargar solo el audio

Si solo necesitas el audio de un video:

```bash
yt-dlp -x -f bestaudio --add-metadata URL  
```

### Variantes con miniatura:

1. **Formato predeterminado:**
   ```bash
   yt-dlp -x -f bestaudio --add-metadata --embed-thumbnail URL  
   ```
2. **Formato M4A:**
   ```bash
   yt-dlp -x -f bestaudio[ext=m4a] --add-metadata URL  
   yt-dlp -x -f bestaudio[ext=m4a] --add-metadata --embed-thumbnail URL  
   ```
