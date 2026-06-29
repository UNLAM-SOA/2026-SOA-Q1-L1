ref: https://hub.docker.com/_/eclipse-mosquitto
docker image:
`docker run -it --name mosquitto -p 1883:1883 -v "$PWD/mosquitto/config:/mosquitto/config" -v "$PWD/mosquitto/data:/mosquitto/data" -v "$PWD/mosquitto/log:/mosquitto/log" eclipse-mosquitto`
to run: 
`docker compose up -d`
to stop: 
`docker compose down`
logs: 
`docker compose logs -f`

emulador android (conectar al broker via 127.0.0.1):
tunel adb: 
`adb reverse tcp:1883 tcp:1883`
verificar: 
`adb reverse --list`
ver logs de la app: 
`adb logcat | Select-String "espejo|Aplicacion"`

