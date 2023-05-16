# Email Microservice

Email microservice for EnviDat, based on jdrouet/catapulte:
https://github.com/jdrouet/catapulte

## Running

1. Create .run.env with environment variables:

```dotenv
# LOG: debug
SMTP__HOSTNAME: YOUR_MAIL_SERVER
SMTP__PORT: YOUR_MAIL_PORT
```

2. Add you MJML templates to the `templates` directory.

3. Run the server

`docker compose up -d`
