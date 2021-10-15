1. Como usuarie de QueMePongo quiero ver todas las prendas que tengo en mi guardarropas desde el navegador para poder administrarlas

Ruta:

```GET user/{userId}/prendas```

Request body:
```json
{
    "tipos": ["pantalon", "remera"],
    "talla": ["XL", "S"],
    "_page": 1
}
```

Response Codes:
- 404 User not found (cuando el usuario no existe)
- 403 Forbidden response (cuando intenta ingresar un usuario no administrador a las prendas de otro usuario)
- 401 Unauthenticated
- 200 OK

Response body:
```json
{
  "prendas": [
    {
      "id": 1,
      "tipo": "saco",
      "talle": "XL"
    },
    {
      "id": 2,
      "tipo": "remera",
      "talle": "S"
    }
  ]
}
```

2. Como usuario de QueMePongo, quiero crear una prenda desde el navegador

Ruta:

```
POST users/{userId}/prendas
```

Request Body
```json
{
    "tipo": "Camisa",
    "talle": "S"
}
```

Response Codes:
- 200 OK
- 404 User Not Found
- 403 Forbidden (intenta crear una prenda a un usuario que no es el mismo y no es administrador)
- 401 Unauthenticated

Response Body:
```json
{
    "id": 1,
    "tipo": "Camisa",
    "talle": "S"
}
```

3. Como usuarie de QueMePongo quiero ver una prenda en particular que tengo en mi guardarropas para poder editarla

Ruta:

```
GET user/{userId}/prendas/{prendaId}
```

Request Body: vacío

Response Codes:
- 200 OK
- 404 User Not Found/Prenda not found
- 403 Forbidden. Intenta ver prenda que pertenece a otro usuario.
- 401 Unauthenticated

Response Body:
```json
{
    "id": 1,
    "tipo": "Camisa",
    "talle": "S"
}
```


4. Como usuarie de QueMePongo, quiero poder eliminar una prenda de mi guardarropas

Ruta:

```
DELETE user/{userId}/prendas/{prendaId}
```

Request Body: vacío

Response Codes:
- 200 OK
- 404 User Not Found/Prenda not found
- 403 Forbidden. Intenta borrar prenda que pertenece a otro usuario.
- 401 Unauthenticated

Response Body:
```json
{
    "id": 1,
    "tipo": "Camisa",
    "talle": "S"
}
```

5. Como usuarie de QueMePongo, quiero poder ver mis eventos para administrarlos

```
GET user/{userId}/eventos
```

Request Body: vacío

Response Codes:
- 200 OK
- 404 User Not Found
- 403 Forbidden. Intenta acceder a los eventos de otro usuario (un usuario no administrador)
- 401 Unauthenticated

Response Body:
```json
{
    "eventos": [
        {
            "id": 3,
            "nombre": "granizo",
            "sugerencia": "salir con paraguas"
        },
        {
            "id": 4,
            "nombre": "Lluvia",
            "sugerencia": "No salir"
        }
    ]
}
```


6. Como usuarie de QueMePongo, quiero poder abrir las sugerencias de prendas para un evento en mi navegador
```
GET user/{userId}/eventos/{eventoId}/sugerencias
```

Request Body: vacío

Response Codes:
- 200 OK
- 404 User Not Found
- 403 Forbidden. Intenta acceder a las sugerencias que no le pertenece (usuario no administrador)
- 401 Unauthenticated

Response Body:
```json
{
    "prendas": [
        {
            "id": 1,
            "tipo": "saco",
            "talle": "XL"
        },
        {
            "id": 5,
            "tipo": "buzo",
            "talle": "XL"
        }
    ]
}
```
