
## 1. Levantarlo en 5 minutos (solo en tu compu)

```bash
cd n8n-starter
cp .env.example .env
# genera tu clave y pégala en .env (reemplaza el valor de ejemplo):
openssl rand -base64 32
docker compose up -d
docker compose logs -f n8n   # Ctrl+C para salir de los logs
```

Abre **http://localhost:5678** y crea tu cuenta de owner.
Para pararlo: `docker compose down` (tus flujos quedan guardados
en el volumen `n8n_data`).

> Seguridad: esto es solo local. No expongas el puerto 5678 a
> internet sin HTTPS y contraseña, y actualiza la imagen cada mes
> (en 2026 hubo varios parches de seguridad en n8n).

## 2. Tu primer flujo (ya viene en este kit)

Archivo: `workflow-mi-primer-flujo.json`

1. En n8n: **Workflows → … → Import from File** y elige ese archivo.
2. Dale a **Execute Workflow**.
3. Vas a ver el top 5 de repos de Laravel por estrellas, sacado
   directo de la API de GitHub, sin ninguna credencial.

Flujo: `Manual Trigger → HTTP Request (api.github.com/search/repositories?q=laravel) → Code (arma el top 5)`.

## 3. Qué probar después (en ese orden)

1. Cambia el **Manual Trigger** por un **Schedule Trigger** diario
   a las 9:00 — ya tienes un reporte diario automático.
2. Agrega un nodo **Telegram** (crea un bot con @BotFather) para
   que el resumen te llegue a WhatsApp/Telegram en vez de
   entrar a n8n.
3. Agrega un nodo **MySQL** y guarda el top 5 cada día: ya tienes
   historial y práctica real con tu stack.
