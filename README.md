# LTI - Talent Tracking System | ENG

This project is a full-stack application with a React frontend and an Express backend using Prisma as an ORM. The frontend is set up with Create React App, and the backend is written in TypeScript.

## Explanation of Directories and Files

- `backend/`: It contains the server-side code written in Node.js.
  - `__test__`: It contains test units code files
  - `src/`: It contains the source code for the backend.
    - `index.ts`: The entry point for the backend server.
    - `application/`: It contains the application logic.
    - `domain/`: It contains the business logic.
    - `presentation/`: It contains code related to the presentation layer (such as controllers).
    - `routes/`: It contains the route definitions for the API.
  - `prisma/`: It contains the Prisma schema file for ORM.
  - `tsconfig.json`: TypeScript configuration file.
- `frontend/`: It contains the client-side code written in React.
  - `src/`: It contains the source code for the frontend.
  - `public/`: It contains static files such as the HTML file and images.
  - `build/`: It contains the production-ready build of the frontend.
- `.env`: It contains the environment variables.
- `docker-compose.yml`: It contains the Docker Compose configuration to manage your application's services.
- `README.md`: This file contains information about the project and instructions on how to run it.

## Project Structure

The project is divided into two main directories: frontend and backend.

### Frontend

The frontend is a React application, and its main files are located in the src folder. The public folder contains static assets, and the build directory contains the production build of the application.

### Backend

The backend is an Express application written in TypeScript. The src directory contains the source code, divided into several subdirectories:

- `application`: It contains the application logic.
- `domain`: It contains the domain models.
- `infrastructure`: It contains code related to the infrastructure.
- `presentation`: It contains code related to the presentation layer.
- `routes`: It contains the application routes.
- `tests`: It contains the application tests.

The `prisma` folder contains the Prisma schema.

### Unit Testing Structure

The backend includes a well-organized structure for unit tests using Jest and Supertest. Tests are located in the `backend/__tests__` folder and follow this structure:

- `__tests__/`: It contains unit test files for the backend.
    - `application/`: Unit tests for application logic.
      - `files/`: Test files such as sample PDFs.
        - `test-cv.pdf`: Sample PDF file used in tests.
      - `services/`:
        - `candidateService.test.ts`: Unit tests for the candidate service logic.
    - `domain/`:
      - `models/`: (Reserved for domain model tests)
    - `presentation/`:
      - `controllers/`: (Reserved for controller tests)
    - `routes/`:
      - `candidateRoutes.test.ts`: Unit tests for candidate API routes.

#### Running Unit Tests

To run the backend unit tests:

1. Install dependencies:
    ```sh
    npm install
    ```
2. Run the tests:
    ```sh
    npm test
    ```
3. (Optional) For coverage report:
    ```sh
    npm test -- --coverage
    ```

All tests use mocks for the database and external services, ensuring no real data is altered.

## First Steps

To get started with this project, follow these steps:

1. Clone the repo.
2. Install the dependencies for front end and back end:
```sh
cd frontend
npm install

cd ../backend
npm install
```
3. Build the back end server:
```
cd backend
npm run build
````
4. Start the backend server:
```
cd backend
npm start
```
5. In a new terminal window, build the frontend server:
```
cd frontend
npm run build
```
6. Start the frontend server:
```
cd frontend
npm start
```

The backend server will be running at http://localhost:3010, and the frontend will be available at http://localhost:3000.

## Docker y PostgreSQL

This project uses Docker to run a PostgreSQL database. Here’s how to get it up and running:

Install Docker on your machine if you haven't done so already. You can download it from here.
Navigate to the root directory of the project in your terminal.
Run the following command to start the Docker container:
```
docker-compose up -d
```
This will start a PostgreSQL database in a Docker container. The -d flag runs the container in detached mode, which means it runs in the background.

To access the PostgreSQL database, you can use any PostgreSQL client with the following connection details:
 - Host: localhost
 - Port: 5432
 - User: postgres
 - Password: password
 - Database: mydatabase

Please replace User, Password, and Database with the actual username, password, and database name specified in your .env file.

To stop the Docker container, run the following command:
```
docker-compose down
```

To generate the database using Prisma, follow these steps:

1. Make sure that the `.env` file in the root directory of the backend contains the `DATABASE_URL` variable with the correct connection string to your PostgreSQL database. If it doesn’t work, try replacing the full URL directly in `schema.prisma`, in the `url` variable.

2. Open a terminal and navigate to the backend directory where the `schema.prisma` file is located.

3. Run the following command to apply the migrations to your database:

```
npx prisma migrate dev
```

Once you have completed all the steps, you should be able to save new candidates, both via the web and via the API, and see them in the database.

```
POST http://localhost:3010/candidates
{
    "firstName": "Albert",
    "lastName": "Saelices",
    "email": "albert.saelices@gmail.com",
    "phone": "656874937",
    "address": "Calle Sant Dalmir 2, 5ºB. Barcelona",
    "educations": [
        {
            "institution": "UC3M",
            "title": "Computer Science",
            "startDate": "2006-12-31",
            "endDate": "2010-12-26"
        }
    ],
    "workExperiences": [
        {
            "company": "Coca Cola",
            "position": "SWE",
            "description": "",
            "startDate": "2011-01-13",
            "endDate": "2013-01-17"
        }
    ],
    "cv": {
        "filePath": "uploads/1715760936750-cv.pdf",
        "fileType": "application/pdf"
    }
}
```
-------------------------------------------------------------

# LTI - Sistema de Seguimiento de Talento | ES

Este proyecto es una aplicación full-stack con un frontend en React y un backend en Express usando Prisma como un ORM. El frontend se inicia con Create React App y el backend está escrito en TypeScript.

## Explicación de Directorios y Archivos

- `backend/`: Contiene el código del lado del servidor escrito en Node.js.
  - `__tests__`: Contiene el código para pruebas unitarias
  - `src/`: Contiene el código fuente para el backend.
    - `index.ts`: El punto de entrada para el servidor backend.
    - `application/`: Contiene la lógica de aplicación.
    - `domain/`: Contiene la lógica de negocio.
    - `presentation/`: Contiene código relacionado con la capa de presentación (como controladores).
    - `routes/`: Contiene las definiciones de rutas para la API.
  - `prisma/`: Contiene el archivo de esquema de Prisma para ORM.
  - `tsconfig.json`: Archivo de configuración de TypeScript.
- `frontend/`: Contiene el código del lado del cliente escrito en React.
  - `src/`: Contiene el código fuente para el frontend.
  - `public/`: Contiene archivos estáticos como el archivo HTML e imágenes.
  - `build/`: Contiene la construcción lista para producción del frontend.
- `.env`: Contiene las variables de entorno.
- `docker-compose.yml`: Contiene la configuración de Docker Compose para gestionar los servicios de tu aplicación.
- `README.md`: Este archivo, contiene información sobre el proyecto e instrucciones sobre cómo ejecutarlo.

## Estructura del Proyecto

El proyecto está dividido en dos directorios principales: `frontend` y `backend`.

### Frontend

El frontend es una aplicación React y sus archivos principales están ubicados en el directorio `src`. El directorio `public` contiene activos estáticos y el directorio `build` contiene la construcción de producción de la aplicación.

### Backend

El backend es una aplicación Express escrita en TypeScript. El directorio `src` contiene el código fuente, dividido en varios subdirectorios:

- `application`: Contiene la lógica de aplicación.
- `domain`: Contiene los modelos de dominio.
- `infrastructure`: Contiene código relacionado con la infraestructura.
- `presentation`: Contiene código relacionado con la capa de presentación.
- `routes`: Contiene las rutas de la aplicación.
- `tests`: Contiene las pruebas de la aplicación.

El directorio `prisma` contiene el esquema de Prisma.

### Estructura de Pruebas Unitarias

El backend incluye una estructura organizada para pruebas unitarias utilizando Jest y Supertest. Las pruebas se encuentran en la carpeta `backend/__tests__` y siguen esta estructura:

- `__tests__/`: Contiene los archivos de pruebas unitarias del backend.
    - `application/`: Pruebas de la lógica de aplicación.
      - `files/`: Archivos de prueba, como PDFs de ejemplo.
        - `test-cv.pdf`: Archivo PDF de ejemplo usado en pruebas.
      - `services/`:
        - `candidateService.test.ts`: Pruebas unitarias para la lógica del servicio de candidatos.
    - `domain/`:
      - `models/`: (Reservado para pruebas de modelos de dominio)
    - `presentation/`:
      - `controllers/`: (Reservado para pruebas de controladores)
    - `routes/`:
      - `candidateRoutes.test.ts`: Pruebas unitarias para las rutas de la API de candidatos.

#### Ejecución de Pruebas Unitarias

Para ejecutar las pruebas unitarias del backend:

1. Instala las dependencias:
    ```sh
    npm install
    ```
2. Ejecuta las pruebas:
    ```sh
    npm test
    ```
3. (Opcional) Para ver el reporte de cobertura:
    ```sh
    npm test -- --coverage
    ```

Todas las pruebas utilizan mocks para la base de datos y servicios externos, asegurando que no se alteren datos reales.

## Primeros Pasos

Para comenzar con este proyecto, sigue estos pasos:

1. Clona el repositorio.
2. Instala las dependencias para el frontend y el backend:
```sh
cd frontend
npm install

cd ../backend
npm install
```
3. Construye el servidor backend:
```
cd backend
npm run build
````
4. Inicia el servidor backend:
```
cd backend
npm start
```
5. En una nueva ventana de terminal, construye el servidor frontend:
```
cd frontend
npm run build
```
6. Inicia el servidor frontend:
```
cd frontend
npm start
```

El servidor backend estará corriendo en http://localhost:3010 y el frontend estará disponible en http://localhost:3000.

## Docker y PostgreSQL

Este proyecto usa Docker para ejecutar una base de datos PostgreSQL. Así es cómo ponerlo en marcha:

Instala Docker en tu máquina si aún no lo has hecho. Puedes descargarlo desde aquí.
Navega al directorio raíz del proyecto en tu terminal.
Ejecuta el siguiente comando para iniciar el contenedor Docker:
```
docker-compose up -d
```
Esto iniciará una base de datos PostgreSQL en un contenedor Docker. La bandera -d corre el contenedor en modo separado, lo que significa que se ejecuta en segundo plano.

Para acceder a la base de datos PostgreSQL, puedes usar cualquier cliente PostgreSQL con los siguientes detalles de conexión:
 - Host: localhost
 - Port: 5432
 - User: postgres
 - Password: password
 - Database: mydatabase

Por favor, reemplaza User, Password y Database con el usuario, la contraseña y el nombre de la base de datos reales especificados en tu archivo .env.

Para detener el contenedor Docker, ejecuta el siguiente comando:
```
docker-compose down
```

Para generar la base de datos utilizando Prisma, sigue estos pasos:

1. Asegúrate de que el archivo `.env` en el directorio raíz del backend contenga la variable `DATABASE_URL` con la cadena de conexión correcta a tu base de datos PostgreSQL. Si no te funciona, prueba a reemplazar la URL completa directamente en `schema.prisma`, en la variable `url`.

2. Abre una terminal y navega al directorio del backend donde se encuentra el archivo `schema.prisma`.

3. Ejecuta el siguiente comando para aplicar las migraciones a tu base de datos:
```
npx prisma migrate dev
```

Una vez has dado todos los pasos, deberías poder guardar nuevos candidatos, tanto via web, como via API, y verlos en la base de datos.

```
POST http://localhost:3010/candidates
{
    "firstName": "Albert",
    "lastName": "Saelices",
    "email": "albert.saelices@gmail.com",
    "phone": "656874937",
    "address": "Calle Sant Dalmir 2, 5ºB. Barcelona",
    "educations": [
        {
            "institution": "UC3M",
            "title": "Computer Science",
            "startDate": "2006-12-31",
            "endDate": "2010-12-26"
        }
    ],
    "workExperiences": [
        {
            "company": "Coca Cola",
            "position": "SWE",
            "description": "",
            "startDate": "2011-01-13",
            "endDate": "2013-01-17"
        }
    ],
    "cv": {
        "filePath": "uploads/1715760936750-cv.pdf",
        "fileType": "application/pdf"
    }
}
```
