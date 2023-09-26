# Email Microservice

Email microservice for EnviDat, based on jdrouet/catapulte:
https://github.com/jdrouet/catapulte

## Running

1. Create runtime.env with environment variables:

```dotenv
# LOG: debug
SMTP__HOSTNAME: YOUR_MAIL_SERVER
SMTP__PORT: YOUR_MAIL_PORT
```

2. Add you MJML templates to the `templates` directory.

3. Run the server

`docker compose -f docker-compose.main.yml up -d`

4. Use via a POST request:

```bash
curl -X 'POST' \
  'http://envidatdocker.wsl.ch:3010/templates/access-token/json' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "from": "envidat@wsl.ch",
  "params": {"user_email": "YOUR_USER@wsl.ch", "user_token": "jhsdgfiusdhfiudshf", "user_name": "Test", "site_url": "https://envidat.ch"},
  "to": "YOUR_USER@wsl.ch"
}'
```

```python
import requests

email_to = "YOUR_USER@wsl.ch"
headers = {"Content-Type": "application/json"}
params = {
    "from": "envidat@wsl.ch",
    "to": email_to,
    "params": {
        "user_email": email_to,
        "user_token": "jhsdgfiusdhfiudshf",
        "user_name": "Test",
        "site_url": "https://envidat.ch",
    }
}

r = requests.post(
    "http://envidatdocker.wsl.ch:3010/templates/access-token/json",
    headers=headers,
    json=params,
)

print(r.status_code)
```
