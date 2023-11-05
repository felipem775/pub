# Sistema de colas

## Sistema sencillo usando screen

En ocasiones podemos querer lanzar varios comandos que se ejecuten uno detrás de otro, bien porque son muy demandantes o simplemente necesitamos la salida de uno para poder realizar el siguiente paso.

Cuando lanzamos un comando en la terminal, no nos devuelve el control hasta finalizar la tarea, por lo que no podemos ir escribiendo otros comandos (en realidad sí pero a ciegas y con mucho peligro).
Existen multiples gestores de cola pero hace un tiempo encontré en [superuser](https://superuser.com/questions/220364/how-to-run-commands-as-in-a-queue/221770#221770) una forma muy ingeniosa de hacerlo.

Utilizando [GNU Screen](https://www.gnu.org/software/screen/), que es un software que permite mantener una sesión aunque tengamos cerrado el terminal, podemos lanzarle comandos a una sesión y éstos se ejecutarán uno tras otro.

Para preparar una cola nueva lo primero es ejecutar

```bash
screen -d -m -S queue
```

`-d -m` Arranca screen en *detached* mode. Es decir, crea la sesión pero no se une a ella.
`-S queue` Es para asignar el nombre de la sesión.

Podríamos tener diferentes colas simplemente usando el mismo comando y cambiando el nombre `queue`.

Enviamos comandos al terminal

```bash
screen -S queue -X stuff "echo first^M"
screen -S queue -X stuff "echo second^M"
```

Terminan los comandos en `^M` para enviar un cambio de línea.

Si queremos unirnos a la sesión para ver cómo van las tareas

```bash
screen -S queue -r
```

Y recordemos que para soltar la sesión usamos la combinación de teclas `control` + `a` y `d`