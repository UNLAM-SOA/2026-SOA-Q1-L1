# Mosquitto (Broker MQTT)

Broker MQTT para el proyecto Smart Mirror, basado en la imagen oficial de Eclipse Mosquitto.

> Referencia: https://hub.docker.com/_/eclipse-mosquitto

## Docker

| Acción | Comando |
| ------ | ------- |
| Levantar el broker | `docker compose up -d` |
| Detener el broker | `docker compose down` |
| Ver logs | `docker compose logs -f` |

## Emulador Android

Conectar al broker vía `127.0.0.1`.

Crear el túnel ADB:

```sh
adb reverse tcp:1883 tcp:1883
```

Verificar el túnel:

```sh
adb reverse --list
```

Ver logs de la app:

```powershell
adb logcat | Select-String "espejo|Aplicacion"
```

## Publicar y suscribir mensajes

Enviar mensaje al tópico de distancia:

```sh
docker exec -it mosquitto mosquitto_pub -t "espejo/sensor/distancia1" -m "42"
```

Enviar mensaje al tópico de luz:

```sh
docker exec -it mosquitto mosquitto_pub -t "espejo/sensor/luz" -m "800"
```

Leer todos los tópicos de espejo:

```sh
docker exec -it mosquitto mosquitto_sub -t "espejo/#" -v
```
