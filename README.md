


# EcomCore-API

Descripción del Proyecto

EcomCore-API es una plataforma de comercio electrónico simplificada diseñada para demostrar habilidades en la implementación de servicios backend y frontend utilizando Laravel y Vue.js. Este proyecto forma parte de una prueba técnica para una posición de backend de nivel medio y cubre aspectos clave de diseño arquitectónico, implementación en la nube, desarrollo de servicios RESTful, y documentación de API.

## Arquitectura 

<p align="center">
<iframe frameborder="0" style="width:100%;height:585px;" src="https://app.diagrams.net/?tags=%7B%7D#G1mCRuhp3zbcqcRtzLiXIq42Oq89-21QWi"></iframe>
</p>

Este proyecto utiliza Laravel en el backend y Vue.js en el frontend. Se eligió esta arquitectura por:
- Laravel proporciona un robusto framework PHP con excelente soporte para APIs
- Vue.js ofrece un framework frontend reactivo y fácil de usar
Descripción del Diagrama:
Frontend (Vue.js): Interactúa con el balanceador de carga.
Balanceador de Carga (ELB): Distribuye el tráfico entre las instancias EC2.
API Laravel: Gestiona las solicitudes y se divide en dos servicios principales.
Servicio de Catálogo: Maneja la gestión de productos.
Servicio de Pedidos: Maneja la gestión de pedidos.
MySQL: Base de datos para almacenar productos y pedidos.
Redis: Usado para caché y colas.
Cola de Tareas: Procesa tareas asíncronas.
Almacenamiento Local: Usado en desarrollo para archivos estáticos.
S3: Almacenamiento de archivos estáticos en producción.
EC2: Ejecuta la aplicación Laravel en la nube.
RDS: Proporciona una base de datos MySQL gestionada.
ElastiCache: Administra caché y colas.
CloudFront: CDN que sirve archivos estáticos.
IAM: Gestiona permisos y accesos.
CloudWatch: Monitoreo y logs de la aplicación.



## Installation 
Follow these steps to clone and install the project:

### Clone the project

Clone the repository from GitHub:

```bash
git clone https://github.com/lokogam/EcomCore-API.git
cd EcomCore-API
```

## Requirements

Make sure you have the following requirements installed on your machine:

- Docker
- Docker Compose

## Environment Configuration

Copy the example configuration file and update the environment variables as needed:

```bash
cp .env.example .env
```

### Configuración del entorno

Antes de instalar las dependencias, duplica el archivo `.env.example` y nómbralo `.env`. Luego, agrega las siguientes variables de entorno en el archivo `.env`:

```env
SANCTUM_STATEFUL_DOMAINS=localhost:8000
SESSION_DOMAIN=
SQS_PREFIX=http://localstack:4566/000000000000
SQS_QUEUE=your-queue-name
AWS_ACCESS_KEY_ID=test
AWS_SECRET_ACCESS_KEY=test
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=your-bucket-name
AWS_ENDPOINT=http://localstack:4566
AWS_USE_PATH_STYLE_ENDPOINT=true
QUEUE_CONNECTION=sqs
```

## Installing Dependencies

Use Docker to install the project's dependencies with Composer:

```bash
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php83-composer:latest \
    composer install --ignore-platform-reqs
```

## Bringing up the services

Use Docker Compose to bring up the services needed for the project:

```bash
./vendor/bin/sail up -d
```

## generate key 

generate the application key 

```bash
./vendor/bin/sail artisan key:generate
```

## Migrating the database

Run the migrations to set up the database:

```bash
./vendor/bin/sail artisan migrate
```


ejecuratar

```bash
./vendor/bin/sail artisan aws:setup 
```
documentacion 
http://localhost/api/documentation

## Accessing the application

The application will be available at http://localhost

frontend 
https://github.com/lokogam/VueShop-UI.git


<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

You may also try the [Laravel Bootcamp](https://bootcamp.laravel.com), where you will be guided through building a modern Laravel application from scratch.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains thousands of video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the [Laravel Partners program](https://partners.laravel.com).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[WebReinvent](https://webreinvent.com/)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[DevSquad](https://devsquad.com/hire-laravel-developers)**
- **[Jump24](https://jump24.co.uk)**
- **[Redberry](https://redberry.international/laravel/)**
- **[Active Logic](https://activelogic.com)**
- **[byte5](https://byte5.de)**
- **[OP.GG](https://op.gg)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
