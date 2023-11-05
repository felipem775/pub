# Media

# Convertir a mp3

Para extraer el audio o convertir de otros formatos a mp3 o bien cambiar la calidad del archivo; podemos utilizar `ffmpeg`.

En el siguiente ejemplo vemos cómo convertir todos los ficheros `wav` de un directorio a mp3 en calidad 320 kbps.

```bash
for i in *.wav; do ffmpeg -i "$i" -ac 2 -ab 320k -ar 44100 -joint_stereo 0 "${i%.*}.mp3"; done
```

Parámetros:

- `-ac 2` especifica dos canales (stereo).
- `-ab 320k` la tasa de bits por segundo.
- `-ar 44100` salida a 44100 Hz.
- `-joint_stereo 0` especifica que se mantengan los canales de stereo por separado.

Información extraída de [este gist](https://gist.github.com/dominicthomas/52e610c9cd4083408371?permalink_comment_id=4265424#gistcomment-4265424).