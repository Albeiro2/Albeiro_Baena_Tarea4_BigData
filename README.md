# Albeiro_Baena_Tarea4_BigData
Grupo: 2034

# Caso de uso y Diseño de la base de datos

Para desarrollar la actividad en la base de datos MongoDB, se escogió el siguiente caso de uso, extraído de kaggle.com.
Rendimiento Académico de estudiantes:
Este conjunto de datos contiene información detallada sobre 1000 estudiantes. Se enfoca en su origen demográfico, estudiando también el nivel educativo de sus padres y el desempeño de los estudiantes en tres exámenes estandarizados que son: matemáticas, lectura y escritura. 
En base a la información proporcionada por el dataset y con la ayuda de los comandos de MongoDB , realizaremos un análisis profundo, para darnos cuenta si el género influye, si los padres aportan en gran responsabilidad en los resultados académicos de los estudiantes. También conociendo la raza/etnia de los estudiantes con mejor promedio, para determinar que tanto influye pertenecer a un origen en específico. Los estudiantes también tuvieron la oportunidad de hacer una prueba antes de presentar sus exámenes, por ende, determinaremos que tanto impactó esta prueba previa en sus notas finales. 
Cabe mencionar que las notas van del 1 al 100, demás que este dataset no tiene valores faltantes, por lo que está listo para un análisis completo con los datos ofrecidos.

# Esquema de la base de datos:
- Colección: estudiantes (students)
- Descripción: estudiantes que hicieron los tres exámenes

# Documento

Ejemplo: 
```bash
  {
    "gender": "female",
    "race_ethnicity": "group B",
    "parental_level_of_education": "bachelor's degree",
    "lunch": "standard",
    "test_preparation_course": "none",
    "math_score": 72,
    "reading_score": 72,
    "writing_score": 74
  }
```

# Dataset Link: 
https://www.kaggle.com/datasets/sadiajavedd/students-academic-performance-dataset

# Implementación en MongoDB

Creamos la conexion desde Mongo Compas

<img width="962" height="488" alt="creamos la conexion" src="https://github.com/user-attachments/assets/f3ca2660-5d98-42eb-bacc-76d9663b7262" />

Procedemos a crear la base de datos 

<img width="608" height="468" alt="2  creamos la base de datos" src="https://github.com/user-attachments/assets/a319c449-7991-48b6-90af-420036e61e37" />

Importamos los datos del dataset

<img width="572" height="395" alt="3" src="https://github.com/user-attachments/assets/205a3483-081a-493a-b182-939bf042cedd" />

<img width="959" height="623" alt="4" src="https://github.com/user-attachments/assets/e5254150-5495-426f-883d-edf89fb25746" />

Evidenciamos que si importaron correctamente los datos 

<img width="1197" height="622" alt="5" src="https://github.com/user-attachments/assets/82562248-ad36-406a-852a-e0debd17a362" />

# Consultas desde Mongo Shell

En nuestra teminal ejecutamos el siguiente comandos para usar nuestra base de datos creada en compas

```bash
use bigdata
```
<img width="899" height="197" alt="image" src="https://github.com/user-attachments/assets/3a66f1b7-97fd-4ec8-8e8a-f3320ca57922" />

# Comandos de inserción 

Insertamos un estudiante utilizando el comando db.nuestracollecion.insertOne y llenamos los datos a cada campo

```bash
db.students.insertOne({
"gender": "male",
"race_ethnicity": "group A",
"parental_level_of_education": "Bachiller",
"lunch": "standard",
"test_preparation_course": "completed",
"math_score": 90,
"reading_score": 90,
"writing_score": 70 })
```
Resultado en consola
<img width="975" height="314" alt="image" src="https://github.com/user-attachments/assets/29c8c082-2265-4dcc-81e4-ebb7d3487b2e" />


Ahora para insetar varios estudiantes utilizamos el comando db.nuestracollecion.insertMany 

```bash
db.students.insertMany([ { "gender": "female", "race_ethnicity": "group C", "parental_level_of_education": "UNAD", "lunch": "standard", "test_preparation_course": "completed", "math_score": 69, "reading_score": 90, "writing_score": 88 }, { "gender": "male", "race_ethnicity": "group A", "parental_level_of_education": "UNAD", "lunch": "free/reduced", "test_preparation_course": "none", "math_score": 47, "reading_score": 59, "writing_score": 42 }, { "gender": "female", "race_ethnicity": "group B", "parental_level_of_education": "UNAD", "lunch": "standard", "test_preparation_course": "completed", "math_score": 88, "reading_score": 95, "writing_score": 92 } ])
```

```bash
sudo apt update -y
```

```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```

```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
```bash
sudo apt update -y
```
