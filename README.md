
# bubb-correios

Com esta biblioteca você consegue calcular valores/prazos e rastrear objetos diretamente do webservice dos Correios.

#### **Instalação via composer**

 - PHP >= 5.4
 - [Composer](https://getcomposer.org/)

#### **Composer Setup**
Adicione em seu composer.json

```json
{
    "require": {
        "bubb/bubb-correios": "dev-master"
    }
}
```

#### **Usage**

##### Rastrear objetos

```php
use BUBB\Correios\CorreiosTracking;
use BUBB\Correios\Exceptions\CorreiosTrackingException;

try
{
    $tracking = new CorreiosTracking('PO548836895BR');
    echo '<pre>' . json_encode($tracking->get(), true) . '</pre>';

} catch ( CorreiosTrackingException $e )
{
    echo $e->getMessage();
}

Its output would be:

```php
{
    "code": "PO548836895BR",
    "last_timestamp": 1502126880,
    "last_status": "Em trânsito para CTCE RIBEIRAO PRETO - RIBEIRAO PRETO/SP",
    "last_date": "2017-08-07 14:28",
    "last_locale": null,
    "delivered": false,
    "delivered_at": null,
    "tracking": [
        {
            "timestamp": 1502126880,
            "date": "2017-08-07 14:28",
            "place": "CTE VILA MARIA - SAO PAULO/SP Objeto encaminhado",
            "status": "Em trânsito para CTCE RIBEIRAO PRETO - RIBEIRAO PRETO/SP",
            "forwarded": null,
            "delivered": false
        },
        {
            "timestamp": 1502109900,
            "date": "2017-08-07 09:45",
            "place": "AGF JARDIM MARILIA - SAO PAULO/SP Objeto encaminhado",
            "status": "Em trânsito para CTE VILA MARIA - SAO PAULO/SP",
            "forwarded": null,
            "delivered": false
        },
        {
            "timestamp": 1501868640,
            "date": "2017-08-04 14:44",
            "place": "AGF JARDIM MARILIA - SAO PAULO/SP",
            "status": "Objeto postado",
            "forwarded": null,
            "delivered": false
        }
    ]
}
```