<h1 align="center"> Workshop03 </h1>

## Descripcion

Este workshop tiene como objetivo usar apache Kafka y modelos de prediccion para predecir puntuaciones de felicidad en diferentes países.

Pare esto seran necesarios 5 archivos CSV correspondientes a los anos 2015, 2016, 2017, 2018 y 2019 que contienen información sobre cada país contando con las siguientes columnnas:

* Country
* Rank
* Happines Score
* gdp_per_capita
* Social_Support
* Freedom
* Life_expectancy
* Generosity
* Corruption
* Year


## Objectivo

El obejtivo de este reto es poder predecir las puntuaciones de felicidad de cada pais mediante modelos de prediccion de regresion lineal, en este caso usando Ramdon Forest Regressor

## Que hay en el repositorio?

requirements.txt: En el encontraras las librerias necesarias para su correpto funcionamiento

# analisis folder:
eda.ipynb: En este encontrara el analisis estadistico de cada dataset y las metricas utilizadas para el entrenamiento del modelo 

modelo.ipynb: Aqui se realiza la generacion del modelo

# db folder:
db_postgres.py: Corresponde a las funciones decreacion de la base de datos y subida de la informacion a esta misma que seran llamadas posteriormente

# kafka components folder:
kafkaa.py: Esn este archivo se definen las funciones de kafka producer y consumer

producer.py: Este archivo contiene el productor Kafka que se encargara de aplicar las transformaciones a los datos y luego transmitirlos

consumer.py: Este archivo contiene el consumidor de Kafka que recibe los datos.

# modelo folder: 
Aqui se encuentra el modelo entrenado

## Instalacion

1. **clonar el repositorio:**
   - Clonar el repositorio del proyecto

     ```
     git clone https://github.com/DiegoFMoreno/etl_workshop_03
     ```

2. **Instale las bibliotecas necesarias:**
   - Instale las librerias necesarias que figuran en el archivo `requirements.txt`. Puedes hacer esto usando un administrador de paquetes como pip en Python. Ejecute el siguiente comando:

     ```
     pip install -r requirements.txt
     ```

3. **Configure the PostgreSQL Database Connection:**
   - Cree un archivo `db_config.json` en el directorio principal del proyecto.

        ```json
        {
            "user": "username",
            "password": "password",
            "database": "database"
        }
        ```

4. **Kafka:**
   - Incie el Docker Compose:
        ```bash
        docker-compose up
        ```
   - Ingrese al contenedor de Kafka :
        ```bash
        docker exec -it kafka bash 
        ```
   - Cree el Topic:
        
        Dentro del contenedor de Kafka, ejecute el siguiente comando para crear el topic `kafka-workshop`:
        ```bash
        kafka-topics --bootstrap-server kafka --create --topic kafka-workshop 
        ```  

5. **Visualizar el streaming:**
    - Abra dos terminales y ejecute el siguiente comando en cada terminal respectivamente:
        ```bash
        python kafka_consumer.py
        ```
        ```bash
        python kafka_producer.py
        ```
