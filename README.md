# Albeiro_Baena_Tarea4_BigData
Grupo: 2034

# Caso de uso y Diseño de la base de datos

Para desarrollar la actividad en la base de datos MongoDB, se escogió el siguiente caso de uso, extraído de kaggle.com.
Rendimiento Académico de estudiantes:
Este conjunto de datos contiene información detallada sobre 1000 estudiantes. Se enfoca en su origen demográfico, estudiando también el nivel educativo de sus padres y el desempeño de los estudiantes en tres exámenes estandarizados que son: matemáticas, lectura y escritura. 
En base a la información proporcionada por el dataset y con la ayuda de los comandos de MongoDB , realizaremos un análisis profundo, para darnos cuenta si el género influye, si los padres aportan en gran responsabilidad en los resultados académicos de los estudiantes. También conociendo la raza/etnia de los estudiantes con mejor promedio, para determinar que tanto influye pertenecer a un origen en específico. Los estudiantes también tuvieron la oportunidad de hacer una prueba antes de presentar sus exámenes, por ende, determinaremos que tanto impactó esta prueba previa en sus notas finales. 
Cabe mencionar que las notas van del 1 al 100, demás que este dataset no tiene valores faltantes, por lo que está listo para un análisis completo con los datos ofrecidos.

# Esquema de la base de datos:
Colección: estudiantes (students)
Descripción: estudiantes que hicieron los tres exámenes

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

```bash
sudo apt update -y
```
