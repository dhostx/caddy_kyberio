# Kyberio module for Caddy

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with Kyberio's Domainrobot accounts.

## Caddy module name

```
dns.providers.kyberio
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
  "module": "acme",
  "challenges": {
    "dns": {
      "provider": {
        "name": "kyberio",
        "api_token": "THE_ZONE_KEY"
      }
    }
  }
}
```

or with the Caddyfile:

```
your.domain.com {
  respond "Hello World"	# replace with whatever config you need...
  tls {
    dns kyberio {env.THE_ZONE_KEY}
  }
}
```

You can replace `{env.THE_ZONE_KEY}` with the actual auth token if you prefer to put it directly in your config instead of an environment variable.

## Authenticating

For each zone, a zone key is required. To generate the key, open your DNS record in the Domainrobot, click on "Passwort für dynamic DNS generieren" and save the zone. The generated password will be shown in the form.
