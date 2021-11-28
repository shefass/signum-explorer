# Signum Explorer
This documentation is a work in progress. More details to follow.


## Requirements

A [Signum Node](https://github.com/signum-network/signum-node) with MariaDB version 3.3 or up is required.

### Linux

Install the following packages

```
sudo apt install python3-dev default-libmysqlclient-dev build-essential redis-server supervisor
```

### Windows

(python and other tools equivalent to the above list)

### Modules (all platforms)

The following python modules are required as well:
```
pip install celery django django-cache-memoize django-cors-headers django-filter django-redis djangorestframework gunicorn jsonschema mysqlclient pycoingecko python-redis-lock requests sentry-sdk simplejson supervisor whitenoise python-dotenv
```

## Set-up

Make a copy of the default environment configuration:

`cp .env.default .env`

Edit the `.env` to suit your needs.

See [DB ENGINES PARAMS](https://docs.djangoproject.com/en/2.2/ref/settings/#engine)

`DB_JAVA_WALLET` (signum full node database) Only requires read access

See additional info about set up DB [here](java_wallet)

To initilize the explorer database (DB_DEFAULT) run the following command:
`python manage.py migrate --no-input`

Start a django webserver to test if your instance works:
`python manage.py runserver 0.0.0.0:5000`

To run in production use the provided supervisord.conf to run the service with supervisord:
`/path/to/your/supervisord -c /supervisord.conf`
