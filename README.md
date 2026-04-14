# Procesamiento en Batch y Streaming con Kafka + Spark

Este proyecto implementa un sistema de procesamiento de datos en tiempo real utilizando **Apache Kafka** y **Apache Spark Structured Streaming**. Simula un entorno de sensores IoT donde un productor genera datos y un consumidor los procesa en tiempo real.

## Descripción del proyecto

El sistema está compuesto por dos componentes principales:

### Productor Kafka
Script en Python que genera datos simulados de sensores (temperatura, humedad, sensor_id y timestamp) y los envía continuamente a un topic de Kafka llamado `sensor_data`.

### Spark Streaming
Aplicación en Spark que:
- Lee datos desde Kafka
- Convierte JSON a esquema estructurado
- Procesa datos en tiempo real
- Calcula promedios de temperatura y humedad por sensor
- Agrupa los resultados en ventanas de 1 minuto

## Tecnologías utilizadas

- Python 3
- :contentReference[oaicite:0]{index=0} 4.0.2
- :contentReference[oaicite:1]{index=1} Structured Streaming
- Java JDK 17
- kafka-python
- pyspark

---

## Estructura del proyecto
├── kafka_producer.py
└── spark_streaming_consumer.py


## Requisitos previos

Antes de ejecutar el proyecto, asegúrate de tener:

- Kafka instalado y ejecutándose en `localhost:9092`
- Topic creado:
  ```bash
  kafka-topics.sh --create --topic sensor_data --bootstrap-server localhost:9092
  Java JDK 17 instalado

Apache Spark configurado con soporte para Kafka
Python 3 instalado
## Instalación de dependencias
pip install kafka-python pyspark

## Ejecución del proyecto
Iniciar Kafka

Inicia los servicios de Kafka.

Ejecutar el productor
python kafka_producer.py

Este script enviará datos simulados cada segundo al topic sensor_data.

Ejecutar el consumidor con Spark
spark-submit spark_streaming_consumer.py

Esto iniciará el procesamiento en tiempo real y mostrará los resultados en consola.

##Resultados esperados

El sistema mostrará en consola:

- Promedio de temperatura por sensor
- Promedio de humedad por sensor
- Agrupación por ventanas de tiempo de 1 minuto

## Notas técnicas
Se utiliza Java 17 por compatibilidad con Spark.
Versión de Kafka: 4.0.2
Se define un esquema estructurado para garantizar consistencia en los datos.
Se aplica procesamiento por ventanas para simular análisis de datos IoT en tiempo real.
