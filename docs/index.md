# Nimboestratus Deployer

Ejemplos de despliegue de modelos de ML en la nube.

Empezamos por crear un repositorio en github y clonamos a local.

La recomendación a usar github es crear una clave 

Luego, creamos un entorno virtual usando Poetry. Es una prueba después de
varios años luego que dejé de usarlo por problemas de rendimiento.

Como ya tenemos el proyecto creado desde github empezamos por

```bash
$ poetry init
```

Se pueden indicar dependencias en `pyproject.toml`, añadirlas con el comando `add`.

```bash
$ poetry add scikit-learn
```

Para activar el entorno virtual se utiliza

```bash
$ poetry shell
```

Para correr un script del proyecto dentro del entorno virtual, sin necesidad de
activarlo se utiliza `run` estando en la carpeta del proyecto

```bash
$ poetry run script.py
```


## Ejemplo 01

Tenemos un ejemplo de modelado de predecir el ingreso de unas personas
utilizando las variables numéricas de unos datos del censo.

No hacemos mucho énfasis en los detalles del modelo porque no es el objetivo del
ejercicio. Sin embargo, interesan especialmente los mecanismos del ajuste `fit`,
la predicción `predict`, y la serialización.

**click**

Funcionamiento básico de click https://palletsprojects.com/p/click/ mediante el
uso de decoradores.

- Carga del modelo
- Ingreso y preparación de los datos
  - Issues con numpy
- Ejecutar la predicción
- Estilo de codificación
  - isort
  - black
  - Cadena de documentación
  - Uso de Codeium
- Supresión de advertencias y mensajes de error

```bash
$ python click_predict_01.py -i "43,14344,0,40"
```

**Fastapi**


- Un vistazo al código y al punto final
  - Datos de entrada
  - Definición del modelo de dato y concordancia con los nombres que espera el modelo.

```bash
$ uvicorn fastapi_predict_01:app --reload
```



```json
{
  "age": 43,
  "capital_gain": 14344,
  "capital_loss": 0,
  "hours_per_week": 40
}
```

- Que recibe el servidor

```bash
curl -X 'POST' \
  'http://127.0.0.1:8000/predict' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "age": 43,
  "capital_gain": 0,
  "capital_loss": 0,
  "hours_per_week": 40
}'
```


## Ejemplo 02

## Ejemplo 03