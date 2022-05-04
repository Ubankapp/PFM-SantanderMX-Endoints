# PFM Santander MX

Endpoints del proyecto de PFM para Santander México.

## Obtener los presupuestos del usuario filtrados por mes.

### Petición
```bash
curl -X 'GET' \
  'http://{{ api_pfm_url }}/users/{{ user_id }}/budgets/?date_month={{ YYYY-MM }}' \
  -H 'accept: application/json'
```

### Ejemplo
```bash
curl -X 'GET' \
  'http://localhost:8000/users/479ec168013945d0b7042bc4e5d0c4fb/budgets/?date_month=2021-09' \
  -H 'accept: application/json'
```

### Respuesta

```json
[
    {
        "id": "45a80dbb-ea71-4ce3-90b3-6761bcbf365c",
        "category": {
            "id": "22118f55-e6a9-46b0-ae8f-a063dda396e0",
            "name": "shopping",
            "description": "Shopping",
            "metadata": {
                "icon": "icon.png"
            },
            "created_at": "2021-05-01T15:20:30-04:00",
            "updated_at": "2021-05-01T15:20:30-04:00",
            "code_type": "1ec6a6b5-65d5-4a8c-85d0-4364c141aefd"
        },
        "amount": "2400.00",
        "budget_date": "2021-09-09T15:20:30-04:00",
        "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb"
    }
]
```
## Obtener los presupuestos del usuario filtrados por categoría y por mes.

### Petición
```bash
curl -X 'GET' \
  'http://{{ api_pfm_url }}/users/{{ user_id }}/budgets/categories/{{ budget_id }}/?date_month={{ YYYY-MM }}' \
  -H 'accept: application/json'
```

### Ejemplo
```bash
curl -X 'GET' \
  'http://localhost:8000/users/479ec168013945d0b7042bc4e5d0c4fb/budgets/categories/22118f55-e6a9-46b0-ae8f-a063dda396e0/?date_month=2021-09' \
  -H 'accept: application/json'
```

### Respuesta

```json
[
    {
        "id": "45a80dbb-ea71-4ce3-90b3-6761bcbf365c",
        "category": {
            "id": "22118f55-e6a9-46b0-ae8f-a063dda396e0",
            "name": "shopping",
            "description": "Shopping",
            "metadata": {
                "icon": "icon.png"
            },
            "created_at": "2021-05-01T15:20:30-04:00",
            "updated_at": "2021-05-01T15:20:30-04:00",
            "code_type": "1ec6a6b5-65d5-4a8c-85d0-4364c141aefd"
        },
        "amount": "2400.00",
        "budget_date": "2021-09-09T15:20:30-04:00",
        "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb"
    }
]
```

## Detalle del presupuesto del usuario.

### Petición
```bash
curl -X 'GET' \
  'http://{{ api_pfm_url }}/users/{{ user_id }}/budgets/{{ budget_id }}/' \
  -H 'accept: application/json'
```

### Ejemplo
```bash
curl -X 'GET' \
  'http://localhost:8000/users/479ec168013945d0b7042bc4e5d0c4fb/budgets/45a80dbbea714ce390b3-6761bcbf365c/' \
  -H 'accept: application/json'
```
### Respuesta

```json
{
    "id": "45a80dbb-ea71-4ce3-90b3-6761bcbf365c",
    "category": {
        "id": "22118f55-e6a9-46b0-ae8f-a063dda396e0",
        "name": "shopping",
        "description": "Shopping",
        "metadata": {
            "icon": "icon.png"
        },
        "created_at": "2021-05-01T15:20:30-04:00",
        "updated_at": "2021-05-01T15:20:30-04:00",
        "code_type": "1ec6a6b5-65d5-4a8c-85d0-4364c141aefd"
    },
    "amount": "2400.00",
    "budget_date": "2021-09-09T15:20:30-04:00",
    "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb"
}
```
## Crear presupuesto

### Petición
```bash
curl -X 'POST' \
  'http://{{ api_pfm_url }}/pfm-service/users/{{ user_id }}/budgets/' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -d '{
  "amount": {{ amount }},
  "user": {{ user_id }},
  "category": {{ category_id }}
}'
```

### Ejemplo
```bash
curl -X 'POST' \
  'http://localhost:8000/pfm-service/users/479ec168013945d0b7042bc4e5d0c4fb/budgets/' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -d '{
  "amount": 9000,
  "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb",
  "category": "22118f55-e6a9-46b0-ae8f-a063dda396e0"
}'
```
### Respuesta 

```json
{
  "id": "b4cb85bd-11e4-4ce7-9ef9-e0782cea58c1",
  "category": {
    "id": "22118f55-e6a9-46b0-ae8f-a063dda396e0",
    "name": "shopping",
    "description": "Shopping",
    "metadata": {
      "icon": "icon.png"
    },
    "created_at": "2021-05-01T15:20:30-04:00",
    "updated_at": "2021-05-01T15:20:30-04:00",
    "code_type": "1ec6a6b5-65d5-4a8c-85d0-4364c141aefd"
  },
  "amount": "3000.00",
  "budget_date": "2021-09-09T15:20:30-04:00",
  "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb"
}
```

## Editar el presupuesto del usuario.

### Petición

```bash
curl -X 'PATCH' \
  'http://{{ api_pfm_url }}/pfm-service/users/{{ user_id }}/budgets/{{ budget_id }}/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "amount": 9000
}'
```

### Ejemplo

```bash
curl -X 'PATCH' \
  'http://localhost:8000/pfm-service/users/479ec168013945d0b7042bc4e5d0c4fb/budgets/45a80dbbea714ce390b3-6761bcbf365c/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "amount": 9000
}'
```
### Respuesta 

```json
{
  "id": "45a80dbb-ea71-4ce3-90b3-6761bcbf365c",
  "amount": "5100.00",
  "expenses_sum": "1000.00",
  "expenses_count": 2,
  "average": "500.00",
  "spent": "20.0",
  "budget_date": "2021-09-09",
  "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb",
  "category": "22118f55-e6a9-46b0-ae8f-a063dda396e0"
}
```

## Balance Mensual del usuario. 

### Petición
```bash
curl --request GET \
  --url 'http://{{ api_pfm_url }}/users/{{ user_id }}/transactions/balance/?year={{ YYYY-MM }}'
```

### Ejemplo
```bash
curl --request GET \
  --url 'http://localhost:8000/users/479ec168013945d0b7042bc4e5d0c4fb/transactions/balance/?year=2021'
```
### Respuesta

```json
[
    {
        "year": 2021,
        "months": [
            {
                "year": 2021,
                "month": "Enero",
                "incomes": 2000.0,
                "expenses": -2300.0,
                "balance": -300.0,
                "disabled": false
            },
            {
                "year": 2021,
                "month": "Febrero",
                "incomes": 2400.0,
                "expenses": 0.0,
                "balance": 2400.0,
                "disabled": true
            },
            {
                "year": 2021,
                "month": "Marzo",
                "incomes": 2100.0,
                "expenses": 0.0,
                "balance": 2100.0,
                "disabled": true
            },
            {
                "year": 2021,
                "month": "Abril",
                "incomes": 25000.0,
                "expenses": -700.0,
                "balance": 24300.0,
                "disabled": false
            },
            {
                "year": 2021,
                "month": "Mayo",
                "incomes": 210000.0,
                "expenses": -17000.0,
                "balance": 193000.0,
                "disabled": false
            },
            {
                "year": 2021,
                "month": "Junio",
                "incomes": 1100.0,
                "expenses": -170000.0,
                "balance": -168900.0,
                "disabled": false
            },
            {
                "year": 2021,
                "month": "Julio",
                "incomes": 21007.0,
                "expenses": -17002.0,
                "balance": 4005.0,
                "disabled": false
            },
            {
                "year": 2021,
                "month": "Agosto",
                "incomes": 1005.0,
                "expenses": -700.0,
                "balance": 305.0,
                "disabled": false
            },
            {
                "year": 2021,
                "month": "Septiembre",
                "incomes": 2500.0,
                "expenses": -58880.0,
                "balance": -56380.0,
                "disabled": false
            },
            {
                "year": 2021,
                "month": "Octubre",
                "incomes": 7100.0,
                "expenses": -200.0,
                "balance": 6900.0,
                "disabled": false
            },
            {
                "year": 2021,
                "month": "Noviembre",
                "incomes": 2105.0,
                "expenses": -800.0,
                "balance": 1305.0,
                "disabled": false
            },
            {
                "year": 2021,
                "month": "Diciembre",
                "incomes": 2100.0,
                "expenses": -1800.0,
                "balance": 300.0,
                "disabled": false
            }
        ]
    }
]
```

## Obtener las transacciones del usuario filtradas por mes. 

### Petición
```bash
curl --request GET \
  --url http://{{ api_pfm_url }}/user/{{ user_id }}/transactions/?date_month={{ YYYY-MM }}
```

### Ejemplo
```bash
curl --request GET \
  --url http://localhost:8000/user/479ec168013945d0b7042bc4e5d0c4fb/transactions/?date_month=2021-09
```

### Respuesta

```json
[
    {
        "id": "68e18783-8b51-4618-af83-50c77f25871d",
        "category": {
            "id": "22118f55-e6a9-46b0-ae8f-a063dda396e0",
            "name": "shopping",
            "description": "Shopping",
            "metadata": {
                "icon": "icon.png"
            },
            "created_at": "2021-05-01T15:20:30-04:00",
            "updated_at": "2021-05-01T15:20:30-04:00",
            "code_type": "1ec6a6b5-65d5-4a8c-85d0-4364c141aefd"
        },
        "amount": "1500.00",
        "description": "Transaccion de prueba 1",
        "transaction_date": "2021-09-09T15:20:30-04:00",
        "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb"
    }
]
```

## Obtener las transacciones del usuario filtradas por categoría y por mes.

### Petición
```bash
curl --request GET \
  --url http://{{ api_pfm_url }}/users/{{ user_id }}/transactions/categories/{{ category_id }}/?date_month={{ YYYY-MM }}
```

### Ejemplo
```bash
curl --request GET \
  --url http://localhost:8000/users/479ec168013945d0b7042bc4e5d0c4fb/transactions/categories/22118f55-e6a9-46b0-ae8f-a063dda396e0/?date_month=2021-09
```

### Respuesta

```json
[
    {
        "id": "68e18783-8b51-4618-af83-50c77f25871d",
        "category": {
            "id": "22118f55-e6a9-46b0-ae8f-a063dda396e0",
            "name": "shopping",
            "description": "Shopping",
            "metadata": {
                "icon": "icon.png"
            },
            "created_at": "2021-05-01T15:20:30-04:00",
            "updated_at": "2021-05-01T15:20:30-04:00",
            "code_type": "1ec6a6b5-65d5-4a8c-85d0-4364c141aefd"
        },
        "amount": "1500.00",
        "description": "Transaccion de prueba 1",
        "transaction_date": "2021-09-09T15:20:30-04:00",
        "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb"
    }
]
```

## Asignar nota.

### Petición
```bash
curl --request PATCH \
  --url http://{{ api_pfm_url }}/users/{{ user_id }}/transactions/{{ transaction_id }}/ \
  --header 'content-type: application/json' \
  --data '{"user_note" : {{ user_note }} }'
```

### Ejemplo
```bash
curl --request PATCH \
  --url http://localhost:8000/users/479ec168013945d0b7042bc4e5d0c4fb/transactions/68e18783-8b51-4618-af83-50c77f25871d/ \
  --header 'content-type: application/json' \
  --data '{"user_note" : "Transaccion de prueba 3"}'
```

### Respuesta

```json
{
  "id": "0b32a3b9-3396-4c19-b418-6236ab034a02",
  "amount": "8000.00",
  "description": "Prueba",
  "transaction_date": "2021-09-13T12:56:00-04:00",
  "user_note": "Transaccion de prueba 3",
  "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb",
  "category": "22118f55-e6a9-46b0-ae8f-a063dda396e0"
}
```
## Asignar categoría.

### Petición
```bash
curl --request PATCH \
  --url http://{{ api_pfm_url }}/users/{{ user_id }}/transactions/{{ transaction_id }}/ \
  --header 'content-type: application/json' \
  --data '{"category" : {{ category_id }}'
```

### Ejemplo
```bash
curl --request PATCH \
  --url http://localhost:8000/users/479ec168013945d0b7042bc4e5d0c4fb/transactions/0b32a3b9-3396-4c19-b418-6236ab034a02/ \
  --header 'content-type: application/json' \
  --data '{"category" : "22118f55-e6a9-46b0-ae8f-a063dda396e0"}'
```

### Respuesta

```json
{
  "id": "0b32a3b9-3396-4c19-b418-6236ab034a02",
  "amount": "8000.00",
  "description": "Prueba",
  "transaction_date": "2021-09-13T12:56:00-04:00",
  "user_note": "Transaccion de prueba 3",
  "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb",
  "category": "22118f55-e6a9-46b0-ae8f-a063dda396e0"
}
```

## Detalle de transaccion del usuario.

### Petición
```bash
curl --request GET \
  --url http://{{ api_pfm_url }}/users/{{ user_id }}/transactions/{{ transaction_id }}/
```

### Ejemplo
```bash
curl --request GET \
  --url http://localhost:8000/users/479ec168013945d0b7042bc4e5d0c4fb/transactions/68e18783-8b51-4618-af83-50c77f25871d/
```

### Respuesta

```json
{
    "id": "68e18783-8b51-4618-af83-50c77f25871d",
    "category": {
        "id": "22118f55-e6a9-46b0-ae8f-a063dda396e0",
        "name": "shopping",
        "description": "Shopping",
        "metadata": {
            "icon": "icon.png"
        },
        "created_at": "2021-05-01T15:20:30-04:00",
        "updated_at": "2021-05-01T15:20:30-04:00",
        "code_type": "1ec6a6b5-65d5-4a8c-85d0-4364c141aefd"
    },
    "amount": "1500.00",
    "description": "Transaccion de prueba 1",
    "transaction_date": "2021-09-09T15:20:30-04:00",
    "user": "479ec168-0139-45d0-b704-2bc4e5d0c4fb"
}
```
## Resumen de egresos y presupuestos por categoría..

### Petición
```bash
curl --request GET \
  --url 'http://{{ api_pfm_url }}/users/{{ user_id }}/transactions/expenses/summary/?date_month={{ YYYY-MM}}'
```

### Ejemplo
```bash
curl --request GET \
  --url 'http://localhost:8000/users/479ec168013945d0b7042bc4e5d0c4fb/transactions/expenses/summary/?date_month=2021-09'
```

### Respuesta

```json
[
    {
        "category": "Entretenimiento",
        "spend": 29880.0,
        "movements": 3,
        "percentage": 50.75
    },
    {
        "category": "Shopping",
        "spend": 29000.0,
        "movements": 3,
        "percentage": 49.25
    }
]
```

## Obtener la lista de catalogos

### Petición
```bash
curl --request GET \
  --url http://localhost:8000/pfm-service/catalogs/all/
```

## Obtener un catálogo

### Petición
```bash
curl --request GET \
  --url http://localhost:8000/pfm-service/catalogs/items/3954361d-ddf5-46dc-a8f8-af98ee9811da/
```

### Ejemplo
```bash
curl --request GET \
  --url http://localhost:8000/pfm-service/catalogs/items/3954361d-ddf5-46dc-a8f8-af98ee9811da/
```

### Respuesta 

```json
{
    "id": "3954361d-ddf5-46dc-a8f8-af98ee9811da",
    "name": "Sueldo",
    "description": "Sueldos, salarios, honorarios e ingresos por trabajo",
    "metadata": "OrderedDict([('short_name', 'SUELDO'), ('icon', 'assets/img/category/income.svg'), ('active', True), ('color', '#0E891A')])",
    "active": true,
    "process_name": "",
    "catalog": "c2a07389-da13-4420-9060-c6bef2d6bd03"
}
```

## Consultar una lista de catálogos

### Petición
```bash
curl --request GET \
  --url 'http://{{ api_pfm_url }}/pfm-service/catalogs/?catalog={{ catalog_name }}' 
```

### Ejemplo
```bash
curl --request GET \
  --url 'http://localhost:8000/pfm-service/catalogs/?catalog=incomes_categories' 
```

### Respuesta 

```json
{
    "incomes_categories": [
        {
            "id": "3954361d-ddf5-46dc-a8f8-af98ee9811da",
            "name": "Sueldo",
            "description": "Sueldos, salarios, honorarios e ingresos por trabajo",
            "metadata": "OrderedDict([('short_name', 'SUELDO'), ('icon', 'assets/img/category/income.svg'), ('active', True), ('color', '#0E891A')])",
            "active": true,
            "process_name": "",
            "catalog": "c2a07389-da13-4420-9060-c6bef2d6bd03"
        },
        {
            "id": "8ebba319-0042-41ff-bdbb-ba05cd824d52",
            "name": "Transferencias",
            "description": "Transferencias, depósitos y reembolsos recibidos",
            "metadata": "OrderedDict([('short_name', 'TRANSFERENCIAS'), ('icon', 'assets/img/category/income.svg'), ('active', True), ('color', '#0E891A')])",
            "active": true,
            "process_name": "",
            "catalog": "c2a07389-da13-4420-9060-c6bef2d6bd03"
        },
        {
            "id": "e131ca4e-28d2-48fc-ab73-ea92e48b084f",
            "name": "Rendimientos",
            "description": "Pago de dividendos e intereses ganados",
            "metadata": "OrderedDict([('short_name', 'RENDIMIENTOS'), ('icon', 'assets/img/category/income.svg'), ('active', True), ('color', '#0E891A')])",
            "active": true,
            "process_name": "",
            "catalog": "c2a07389-da13-4420-9060-c6bef2d6bd03"
        },
        {
            "id": "9abd4759-ab14-4e09-adc2-9c5dea1041b2",
            "name": "Rentas y arriendos",
            "description": "Ingresos por arriendos de muebles e inmuebles",
            "metadata": "OrderedDict([('short_name', 'RENTAS_ARRIENDOS'), ('icon', 'assets/img/category/income.svg'), ('active', True), ('color', '#0E891A')])",
            "active": true,
            "process_name": "",
            "catalog": "c2a07389-da13-4420-9060-c6bef2d6bd03"
        },
        {
            "id": "593cea05-8f4d-4b40-ad1b-d73e43c8d53d",
            "name": "Devolución de impuestos",
            "description": "Devoluciones del Servicio de Impuestos Internos",
            "metadata": "OrderedDict([('short_name', 'DEVOLUCION_IMPUESTOS'), ('icon', 'assets/img/category/income.svg'), ('active', True), ('color', '#0E891A')])",
            "active": true,
            "process_name": "",
            "catalog": "c2a07389-da13-4420-9060-c6bef2d6bd03"
        },
        {
            "id": "5f342655-bf27-4523-aa32-40d7cb48ae38",
            "name": "Subvención",
            "description": "Pensión, becas, subvención y ayudas familiares",
            "metadata": "OrderedDict([('short_name', 'SUBVENCION'), ('icon', 'assets/img/category/income.svg'), ('active', True), ('color', '#0E891A')])",
            "active": true,
            "process_name": "",
            "catalog": "c2a07389-da13-4420-9060-c6bef2d6bd03"
        },
        {
            "id": "763d39ca-45e8-4171-8a97-29ba9a37665c",
            "name": "Regalos y otros ingresos",
            "description": "Regalos hechos por transferencias y otros ingresos",
            "metadata": "OrderedDict([('short_name', 'REGALOS_OTROS_INGRESOS'), ('icon', 'assets/img/category/income.svg'), ('active', True), ('color', '#0E891A')])",
            "active": true,
            "process_name": "",
            "catalog": "c2a07389-da13-4420-9060-c6bef2d6bd03"
        }
    ]
}
```
