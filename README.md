# DS · Desarrollo de Software

Prácticas de la asignatura Desarrollo de Software del Grado en Ingeniería Informática de la Universidad de Granada.

La asignatura gira alrededor de los patrones de diseño, así que cada ejercicio consiste en resolver un problema aplicando uno de ellos. Se empieza con ejercicios sueltos en Java y Python, después se pasa a Flutter, y se termina con Triaccount, una aplicación completa para repartir gastos en grupo, con su propia API.

## Las prácticas

**P1 · Patrones de diseño en Java y Python.**
- **Ejercicio 1 · Factoría abstracta (Java).** Carreras de bicicletas de montaña y de carretera, en las que cada factoría crea tanto la carrera como sus bicicletas.
- **Ejercicio 2 · Decorador (Python).** Un modelo de lenguaje de Hugging Face resume un texto, y los decoradores le añaden traducción y expansión sin cambiar la clase original.
- **Ejercicio 3 · Estrategia (Python).** Un *scraper* de citas que puede funcionar con Selenium o con Beautiful Soup, y la estrategia se elige al ejecutarlo.
- **Ejercicio 4 · Filtros de intercepción (Java).** Antes de llegar a su destino, el correo y la contraseña de un cliente pasan por una cadena de filtros, que comprueba que el correo sea válido y que la contraseña no esté vacía, tenga letras y números y la longitud mínima.
- **Ejercicio 5 · Adaptador (Python).** El ejercicio de Adam: un navegador de Los Ángeles que da las distancias en millas, adaptado a un sistema que trabaja en kilómetros.

**P2 · Flutter.** Los mismos patrones, ahora en aplicaciones Flutter. El ejercicio grupal 1 lleva los filtros de intercepción a un formulario de registro, con un filtro más para no repetir correos. Los ejercicios individuales de Adam usan una factoría para estadísticas y un gestor de suscripciones.

**P3 · Sistema bancario con pruebas.** Cuentas y transacciones (depósitos, retiradas y transferencias) en Dart, con pruebas unitarias en `test/bank_test.dart`. Las pruebas no solo comprueban que el saldo cambia bien, sino también que el banco da error cuando se intenta ingresar o retirar una cantidad negativa o sacar más dinero del que hay.

**P4 · Triaccount.** Una aplicación para repartir los gastos de un grupo, al estilo de Tricount. La app en Flutter tiene registro e inicio de sesión, grupos y gastos, y se conecta a una API hecha con Ruby on Rails. Aquí se juntan varios patrones: los gastos pasan por una cadena de filtros antes de guardarse (sin palabrotas, sin fechas en el futuro, con al menos un participante y con foto si el gasto pasa de 50), y la forma de repartir el dinero es una estrategia que se puede cambiar: a partes iguales, por partes o por cantidades.

## Cómo ejecutarlo

### P1

- **Ejercicios en Java (1 y 4):** son proyectos de NetBeans, así que se pueden abrir directamente. El ejercicio 1 recibe cuántas bicicletas de montaña y de carretera hay:
  ```bash
  cd Practica1/Ejercicio1/src
  javac *.java
  java Main 3 4
  ```
- **Ejercicio 2:** necesita una cuenta de Hugging Face con un token de acceso.
  ```bash
  cd Practica1/Ejercicio2
  pip install requests huggingface-hub
  huggingface-cli login
  python3 main.py
  ```
  El texto, los modelos y los idiomas se configuran en `config.json`.
- **Ejercicio 3:**
  ```bash
  cd Practica1/Ejercicio3
  pip install selenium beautifulsoup4 requests
  python3 main.py
  ```
  La opción de Selenium usa el `chromedriver` de Linux que viene en la carpeta.

### P2, P3 y Triaccount (Flutter)

**Requisitos:** Flutter instalado.

```bash
cd Practica3          # o cualquiera de las apps de Practica2 o triaccount/practica4
flutter pub get
flutter run
flutter test          # en Practica3, para pasar las pruebas
```

Triaccount necesita además que la API esté funcionando. Necesita Ruby y Rails:

```bash
cd triaccount/triaccount_api
bundle install
bin/rails db:migrate
bin/rails server
```

## Estructura

```
Practica1/              <- patrones en Java y Python (un ejercicio por carpeta)
Practica2/              <- los patrones en Flutter
Practica3/              <- sistema bancario con pruebas
triaccount/practica4/   <- app de Triaccount en Flutter
triaccount/triaccount_api/ <- API en Ruby on Rails
triaccount/entrega/     <- lo que se entregó, con la memoria (P4.pdf) y el diagrama
banking_service_adam/   <- versión de Adam del sistema bancario, conectada a una API
```

## Créditos

Fernando Lanzarot Facio y Adam Navarro Megías. Copia del repositorio original [Adman23/practicasDS](https://github.com/Adman23/practicasDS).
