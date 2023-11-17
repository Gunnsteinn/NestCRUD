<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="200" alt="Nest Logo" /></a>
</p>

# Nestjs CRUD Template

1. Clonar proyecto
2. `yarn install`
3. Clonar el archivo `.env.template` y renombrarlo a `.env`
4. Cambiar las variables de entorno
5. Levantar la base de datos

```
docker-compose up -d
```

6. Ejecutar SEED

```
http://localhost:3000/api/seed
```

7. Levantar: `yarn start:dev`

# Curls importantes para validar la api:

## GETs:

1. Limpiar y cargar datos a la DB.

```
curl --location --request GET 'localhost:3000/api/seed' \
--header 'Content-Type: application/json'
```

2. Traer 10 valores con offset 0. Esto esta setea por defecto.

```
curl --location --request GET 'localhost:3000/api/products' \
--header 'Content-Type: application/json'
```

3. Traer 20 valores con offset 5.

```
curl --location --request GET 'localhost:3000/api/products?limit=20&offset=5' \
--header 'Content-Type: application/json'
```

4. Traer valor por su id.

```
curl --location --request GET 'localhost:3000/api/products/528d6d03-32ea-462c-b2c9-05f4807e14bc' \
--header 'Content-Type: application/json'
```

5. Traer valor por su slug.

```
curl --location --request GET 'localhost:3000/api/products/men_3d_small_wordmark_tee' \
--header 'Content-Type: application/json'
```

6. Traer valor por su title.

```
curl --location --request GET 'localhost:3000/api/products/Men%E2%80%99s%203D%20Small%20Wordmark%20Tee' \
--header 'Content-Type: application/json'
```

## POST:

1. Crear un nuevo valor incluyendo su relación con la tabla de imagenes.

```
curl --location --request POST 'http://localhost:3000/api/products' \
--header 'Content-Type: application/json' \
--data-raw '{
    "title": "Willy'\''s shirt",
    "sizes": [
        "SM",
        "M",
        "L"
    ],
    "gender": "men",
    "price": 151.01,
    "images": [
        "http://image1.jpg",
        "http://image1.jpg"
    ]
}'
```

## PATCH:

1. Actualizar un valor por su id incluyendo su relación con la tabla de imagenes.

```
curl --location --request POST 'http://localhost:3000/api/products' \
--header 'Content-Type: application/json' \
--data-raw '{
    "title": "Willy'\''s shirt",
    "sizes": [
        "SM",
        "M",
        "L"
    ],
    "gender": "men",
    "price": 151.01,
    "images": [
        "http://image1.jpg",
        "http://image1.jpg"
    ]
}'
```

## DELETE:

1. Elimina un valor por su id incluyendo su relación con la tabla de imagenes.

```
curl --location --request DELETE 'http://localhost:3000/api/products/2b4a0868-747c-4894-8354-ba88460e1a99' \
--header 'Content-Type: application/json' \
--data-raw '{
    "title": "Willy'\''s jacket",
    "price": 151.01,
    "images": [
        "http://image1.jpg"
    ]
}'
```
