# pg_magento_plugin
Plugin para Magento 2

# ClickPayRedeban Magento module

Este módulo es una solución que permite muy fácilmente, a los usuarios de Magento procesar pagos con tarjeta de crédito a través de nuestra plataforma.

## Instalación

Primero que nada, necesita añadir nuestro repositorio en su archivo `composer.json`.

Revise el ejemplo siguiente:


```js
...
    "respositories": [
        {
            "type": "vcs",
            "url": "https://github.com/clickpayredeban/pg-magento-plugin.git"
        }
    ]
...
```

**Path sencillo**:

`composer config repositories.clickpayredeban vcs https://github.com/clickpayredeban/pg-magento-plugin.git`

Ahora ejecute el siguiente comando para instalar nuestro paquete:


`composer require clickpayredeban/magento2`

Una vez que la instalación es completada, ejecute los siguientes comandos en su terminal bash. 


```bash
# Update dependency injection
php bin/magento setup:di:compile

# Update module registry
php bin/magento setup:upgrade

# This command is optional for production environments
php bin/magento setup:static-content:deploy
```
Ahora usted podrá ver las configuraciones de CickPayRedeban en el admin de su Magento en la siguiente ruta: `Stores > Configuration > Sales > Payment Methods`.


## Notificaciones de fraude vía webhook 

Cuando ClickPayRedeban detecta un posible fraude utilizamos notificaciones a través de webhook para notificar al Admin de Magento para actualizar el estado de una orden.

El path del webhook por defecto es:

`/V1/clickpayredeban/notification/listener`

Así, las posibles notificaciones de fraudes serán enviadas a:

`https://magentodomain.com/V1/clickpayredeban/notification/listener`
