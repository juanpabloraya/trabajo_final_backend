
# Product Gallery API

Esta es una API para gestionar una galería de productos utilizando NestJS, Prisma, SQLite y JWT para la autenticación. La API permite crear, leer, actualizar y eliminar productos, con rutas protegidas para la creación y edición de productos.

## Requisitos

- Node.js (versión 20 o superior)
- npm (versión 10 o superior)

## Instalación

Sigue los pasos a continuación para instalar y ejecutar la aplicación:

1. Clonar el repositorio:
    ```bash
    git clone git@github.com:IonVillarreal/product-gallery.git
    cd product-gallery
    ```

2. Instalar las dependencias:
    ```bash
    npm install
    ```

3. Configurar el archivo `.env`:
    - Crea un archivo `.env` en el directorio raíz del proyecto y agrega la siguiente línea:
      ```plaintext
      JWT_SECRET=your_jwt_secret_key
      ```

4. Configurar Prisma:
    - Asegúrate de que el archivo `prisma/.env` contenga la URL de la base de datos apuntando a `file:./dev.db`.
    - Borrar el archivo `/prisma/dev.db` para luego recien crear el .env

5. Inicializar la base de datos:
    ```bash
    npx prisma migrate dev --name init
    ```

6. Ejecutar el script de seed para agregar datos de prueba:
    ```bash
    npm run seed
    ```

7. Iniciar la aplicación:
    ```bash
    npm run start:dev
    ```

8. Acceder a la documentación de la API:
    - Abre tu navegador y navega a `http://localhost:3000/api` para ver la documentación de Swagger.
## Uso

### Autenticación

La API utiliza JWT para la autenticación. Para acceder a las rutas protegidas, primero debes iniciar sesión y obtener un token.

#### Registro de usuario
```bash
POST /api/auth/register
```
Cuerpo de la solicitud:
```json
{
  "email": "user@example.com",
  "password": "yourpassword"
}
```

#### Inicio de sesión
```bash
POST /api/auth/login
```
Cuerpo de la solicitud:
```json
{
  "email": "user@example.com",
  "password": "yourpassword"
}
```
Respuesta:
```json
{
  "access_token": "your_jwt_token"
}
```

### Gestión de productos

#### Crear producto
```bash
POST /api/products
```
Encabezados:
```plaintext
Authorization: Bearer your_jwt_token
```
Cuerpo de la solicitud:
```json
{
  "name": "Product Name",
  "description": "Product Description",
  "price": 99.99
}
```

#### Obtener todos los productos
```bash
GET /api/products
```

#### Obtener un producto por ID
```bash
GET /api/products/:id
```

#### Actualizar producto
```bash
PATCH /api/products/:id
```
Encabezados:
```plaintext
Authorization: Bearer your_jwt_token
```
Cuerpo de la solicitud:
```json
{
  "name": "Updated Product Name",
  "description": "Updated Product Description",
  "price": 149.99
}
```

#### Eliminar producto
```bash
DELETE /api/products/:id
```
Encabezados:
```plaintext
Authorization: Bearer your_jwt_token
```
## Estrcutura del proyecto
```
└── 📁trabajo_final_backend 
    └── .env
    └── .env.example
    └── .eslintrc.js
    └── .gitignore
    └── 📁.husky
        └── 📁_
            └── .gitignore
            └── applypatch-msg
            └── commit-msg
            └── h
            └── husky.sh
            └── post-applypatch
            └── post-checkout
            └── post-commit
            └── post-merge
            └── post-rewrite
            └── pre-applypatch
            └── pre-auto-gc
            └── pre-commit
            └── pre-push
            └── pre-rebase
            └── prepare-commit-msg
    └── .prettierrc
    └── commitlint.config.js
    └── nest-cli.json
    └── package-lock.json
    └── package.json
    └── 📁prisma
        └── .env
        └── dev.db
        └── 📁migrations
            └── 📁20240524151440_init
                └── migration.sql
            └── migration_lock.toml
        └── schema.prisma
        └── seed.ts
    └── README.md
    └── 📁src
        └── app.controller.spec.ts
        └── app.controller.ts
        └── app.module.ts
        └── app.service.ts
        └── 📁auth
            └── auth.controller.spec.ts
            └── auth.controller.ts
            └── auth.module.ts
            └── auth.service.spec.ts
            └── auth.service.ts
            └── 📁dto
                └── login.dto.ts
                └── register.dto.ts
            └── jwt-auth.guard.ts
            └── jwt.strategy.ts
            └── local-auth.guard.ts
            └── local.strategy.ts
        └── main.ts
        └── prisma.module.ts
        └── prisma.service.ts
        └── 📁products
            └── 📁dto
                └── create-product.dto.ts
                └── update-product.dto.ts
            └── products.controller.spec.ts
            └── products.controller.ts
            └── products.module.ts
            └── products.service.spec.ts
            └── products.service.ts
        └── 📁users
            └── users.controller.spec.ts
            └── users.controller.ts
            └── users.module.ts
            └── users.service.spec.ts
            └── users.service.ts
    └── 📁test
        └── app.e2e-spec.ts
        └── jest-e2e.json
    └── tsconfig.build.json
    └── tsconfig.json
```