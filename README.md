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
Aplicacion y Resultado en consola

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
Aplicacion y Resultado en consola

<img width="975" height="314" alt="image" src="https://github.com/user-attachments/assets/29c8c082-2265-4dcc-81e4-ebb7d3487b2e" />


Ahora para insetar varios estudiantes utilizamos el comando db.nuestracollecion.insertMany 

```bash
db.students.insertMany([
{
"gender": "female",
"race_ethnicity": "group C",
"parental_level_of_education": "UNAD",
"lunch": "standard",
"test_preparation_course": "completed",
"math_score": 69,
"reading_score": 90,
"writing_score": 88 },
{
"gender": "male",
"race_ethnicity": "group A",
"parental_level_of_education": "UNAD",
"lunch": "free/reduced",
"test_preparation_course": "none",
"math_score": 47,
"reading_score": 59,
"writing_score": 42 },
{
"gender": "female",
"race_ethnicity": "group B",
"parental_level_of_education": "UNAD",
"lunch": "standard",
"test_preparation_course": "completed",
"math_score": 88,
"reading_score": 95,
 "writing_score": 92 } ])
```

Aplicacion y Resultado en consola

<img width="1014" height="517" alt="image" src="https://github.com/user-attachments/assets/d279e8ba-284f-4da8-9b24-1a0a77bff93f" />


# Comandos de selección

Para este paso, seleccionamos los datos ingresados recientemente, que son los padres que estudiaron en la UNAD,
el comando que usaremos sera db.nuestracoleccion.find donde debemos especificar los parametros de la seleccion

```bash
db.students.find({
  "parental_level_of_education": "UNAD"
})
```

Aplicacion y Resultado en consola

<img width="694" height="1018" alt="image" src="https://github.com/user-attachments/assets/4447cd64-3ecc-4c6a-a6b6-38b4ed202774" />

Para la siguiente consulta, seleccionamos los padres que estudiaron hasta Bachiller

```bash
db.students.find({
"parental_level_of_education": "Bachiller"
})
```
Aplicacion y Resultado en consola

<img width="920" height="462" alt="image" src="https://github.com/user-attachments/assets/c338bc5b-8710-406a-a135-a457b39812e3" />

En esta consulta seremos mas especificos, vamos a seleccionar solo a los estudiantes que aprobaron el examen math y writing por encima de 90, tomaremos los 5 primeros estudiantes que cumplan con la condición

```bash
db.students.find({
  "math_score": { "$gt": 90 },
  "writing_score": { "$gt": 90 }
}).limit(5).pretty()
```
Aplicacion y Resultado en consola

<img width="702" height="1355" alt="image" src="https://github.com/user-attachments/assets/de36ce97-e0f1-4455-956e-b8df5fd32196" />

Ahora seleccionamos estudiantes que reprobaron el examen de math y writing por debajo de 50, solo tendremos en cuenta a los 3 primeros estudiantes que cumplen con la condición

```bash
db.students.find({
  "math_score": { "$lt": 50 },
  "writing_score": { "$lt": 50 }
}).limit(3).pretty()
```

Aplicacion y Resultado en consola

<img width="699" height="1025" alt="image" src="https://github.com/user-attachments/assets/8eab8511-232a-449e-bd62-8041a938a6eb" />

Para la siguiente consula, seleccionamos los estudiantes que no hicieron el test y aprobaron con 100 en los 3 examenes

```bash
db.students.find({
  "test_preparation_course": "none",
  "math_score": 100,
  "reading_score": 100,
  "writing_score": 100
}).pretty()
```

Aplicacion y Resultado en consola

<img width="689" height="793" alt="image" src="https://github.com/user-attachments/assets/e4b8bdc1-4251-4152-a47a-d85002b2b94f" />

Para esta ultima consulta de seleccion, nos enfocaremos en los estudiantes del genero femenino que sacaron 100 en los 3 examenes

```bash
db.students.find({
  "gender": "female",
  "math_score": 100,
  "reading_score": 100,
  "writing_score": 100
}).pretty()
```
Aplicacion y Resultado en consola

<img width="692" height="794" alt="image" src="https://github.com/user-attachments/assets/2feef470-c224-4858-b798-945f474f6e7e" />

# Comandos de actualización 

Como primera actulización, actualizamos a los estudiantes donde los padres estudiando en la UNAD a ingenieros de sistemas, siempre que queramos hacer varias actulizacion o insercciones, que es manipulacion de datos, tendremos presente Many en los comandos  

```bash
db.students.updateMany(
{"parental_level_of_education": "UNAD" }, 
  { "$set": { "parental_level_of_education": "ingenieria de sistemas" } }
)
```

Aplicacion y Resultado en consola

<img width="921" height="332" alt="image" src="https://github.com/user-attachments/assets/774ea448-4b66-4edc-a8c4-78a0a7cfedde" />

Comprobamos la actulización usando comando de selcción

```bash
db.students.find({
"parental_level_of_education": “ingenieria de sistemas"
})
```
Aplicacion y Resultado en consola

<img width="956" height="661" alt="image" src="https://github.com/user-attachments/assets/f93b56e9-4dff-48b2-8f20-962443490583" />

Ahora actulizamos el documento que tiene a los padres que fueron bachiller y colocamos todas las notas en 100, como sabemos que solo existe un documento con esta condición, usamos upadateOne en vez de updateMany

```bash
db.students.updateOne(
  { "parental_level_of_education": "Bachiller" },
  { "$set": { 
      "math_score": 100, 
      "reading_score": 100, 
      "writing_score": 100 
    } 
  }
)
```


Aplicacion y Resultado en consola

<img width="581" height="335" alt="image" src="https://github.com/user-attachments/assets/b4eac457-dd6d-4222-9626-67e5f297efa6" />

Comprobamos la actualización 

```bash
db.students.find(
{ "parental_level_of_education": "Bachiller" }
)
```
Aplicacion y Resultado en consola

<img width="669" height="300" alt="image" src="https://github.com/user-attachments/assets/2789b5d6-49b0-4c3b-a168-f8ca44c7f8a4" />

# Comandos de eliminación 

Pare este primer ejemplo, eliminamos un estudiante que tienen padres ingenieros de sistema, usamos deleteOne y asi solo elimina uno, si queremos eleminar varios, tendriamos que usar deleteMany

```bash
db.students.deleteOne(
{ "parental_level_of_education": "ingeneria de sistemas" }
)
```
Aplicacion y Resultado en consola

<img width="920" height="95" alt="image" src="https://github.com/user-attachments/assets/35b74906-f482-4bc9-94f4-bee7d8897aa2" />

Comprobamos que solo quedan 2 estudiantes, donde antes eran 3 antes de la eliminación

```bash
db.students.find(
{ "parental_level_of_education": “ingenieria de sistemas" }
)
```
Aplicacion y Resultado en consola

<img width="921" height="582" alt="image" src="https://github.com/user-attachments/assets/bc6ee696-6989-4242-a3b0-3523e075f278" />

Para esta ultima eliminación, lo haremos sobre el estudiante que los padres son Bachiler

```bash
db.students.find(
{ "parental_level_of_education": "Bachiller" }
)
```
Aplicacion y Resultado en consola

<img width="920" height="151" alt="image" src="https://github.com/user-attachments/assets/0a932a3a-30ac-45d6-bf79-824ff442abe2" />

Por ultimo, comprabamos que se eliminó el estudiante 

```bash
db.students.find(
{ "parental_level_of_education": "Bachiller" }
)
```
Aplicacion y Resultado en consola

<img width="921" height="173" alt="image" src="https://github.com/user-attachments/assets/a4cc17d9-2e17-4b64-8ce1-272f46913738" />

# Consultas de agregación 

Para esta primera consulta, contamos todos los estudiantes que aprobaron en 100 los 3 exámenes

```bash
db.students.find(
{ "math_score": 100,
"reading_score": 100,
"writing_score": 100
}).count()
```
Aplicacion y Resultado en consola

<img width="386" height="227" alt="image" src="https://github.com/user-attachments/assets/fa2165f3-8b4f-438a-aa21-b6e190dbf9da" />

# Analisis
// Solo 3 estudiantes tuvieron puntaje perfecto en los 3 exámenes

Ahora, consultamos el promedio de la nota del examen de math

```bash
db.students.aggregate([
  {
    $group: {
      _id: null,
      promedio_math: { $avg: "$math_score" }
    }
  }
])
```
Aplicacion y Resultado en consola

<img width="661" height="297" alt="image" src="https://github.com/user-attachments/assets/737fe9e1-793a-4552-9001-4ac3c044aedd" />

# Analisis
// Colocamos null para indicar a mongo que son todos los estudiantes. Al parecer, la mayoría aprobó math

Ahora obtendremos el promedio de cada examen

```bash
db.students.aggregate([
  {
    $group: {
      _id: null,
      promedio_math: { $avg: "$math_score" },
      promedio_reading: { $avg: "$reading_score" },
      promedio_writing: { $avg: "$writing_score" }
    }
  }
])
```
Aplicacion y Resultado en consola

<img width="713" height="531" alt="image" src="https://github.com/user-attachments/assets/f9211cc8-efbf-4beb-b5f8-a3313598975e" />

# Analisis
// La mayoría de los estudiantes aprobaron los 3 exámenes, pero se evidencia que el examen al cual estaban mas preparados fue el de Reading y el de math fue el más difícil 

Para la siguiente consulta nos enfocaremos en obtener la cantidad de estudiantes que reprobaron los 3 examenes 

```bash
db.students.find({
  "math_score": { "$lt": 60 },
  "reading_score": { "$lt": 60 },
  "writing_score": { "$lt": 60 }
}).count()
```
Aplicacion y Resultado en consola

<img width="481" height="217" alt="image" src="https://github.com/user-attachments/assets/b86cb7f6-bef8-40f3-b168-e1e44b994591" />

# Analisis
// El 19% de los estudiantes reprobaron los 3 exámenes a la vez 

Ahora, obtendremos la cantidad de estudiantes que no hicieron el test

```bash
db.students.find({
  "test_preparation_course": "none"
}).count()
```
Aplicacion y Resultado en consola

<img width="503" height="172" alt="image" src="https://github.com/user-attachments/assets/7ed4438b-a868-4f2e-82c4-630b38e144da" />

También la cantidad que aprobaron los 3 exámenes y no hicieron el test

```bash
db.students.find({
  "test_preparation_course": "none",
  "math_score": { "$gt": 60 },
  "reading_score": { "$gt": 60 },
  "writing_score": { "$gt": 60 }
}).count()
```
Aplicacion y Resultado en consola

<img width="531" height="253" alt="image" src="https://github.com/user-attachments/assets/c8307146-13d9-4d69-b475-298e68db2d46" />

# Analisis
// La cantidad de estudiantes que no hicieron el test de prueba fue más de la mitad del total de los estudiantes, pero a pesar de eso, casi más de la mitad de los que no hicieron el test aprobó los 3 exámenes

Para la siguiente consultaa, nos basamos en el grupo etnico, queremos saber la suma total de las notas de wirting por grupo étnico 

```bash
 db.students.aggregate([
  {
    $group: {
      _id: "$race/ethnicity", 
      total_puntos_escritura: { $sum: "$writing_score" }
    }
  }
])
```
Aplicacion y Resultado en consola

<img width="1125" height="340" alt="image" src="https://github.com/user-attachments/assets/98be4dec-e0f4-446c-8336-05b9a037d2a6" />

# Analisis
// En el examen de writing notamos que el grupo C destaco en el examen, y los del grupo A fueron los que sacaron el menor total, podemos deducir que el grupo étnico influyo en el examen de writing.

Siguiendo lo anterior, obtenemos la suma total de las notas de math por grupo étnico 

```bash
db.students.aggregate([
  {
    $group: {
      _id: "$race/ethnicity", 
      total_puntos_escritura: { $sum: "$math_score" }
    }
  }
])
```
Aplicacion y Resultado en consola

<img width="1055" height="329" alt="image" src="https://github.com/user-attachments/assets/f11d4ddc-fbf6-4128-8a7d-b6d8312685fa" />

# Analisis
// Nuevamente los del grupo C tuvieron mejores notas y los del A menor nota

para finalizar con los grupos etnicos, finalmente obtenemos la suma total de las notas de reading por grupo étnico 

```bash
 db.students.aggregate([
  {
    $group: {
      _id: "$race/ethnicity", 
      total_puntos_escritura: { $sum: "$reading_score" }
    }
  }
])
```
Aplicacion y Resultado en consola

<img width="1159" height="347" alt="image" src="https://github.com/user-attachments/assets/7b896c62-55ab-48bb-9ca1-706cd12da83e" />

# Analisis
//Finalmente se concluye que el grupo A siempre fue el de la menor suma total de las notas y el grupo C los mejores, al parecer los del grupo C han tenido un mejor entorno para desarrollar sus habilidades académicas a diferencia del grupo A

Paara esta ultima consulta de agregación, obtendremos la nota minima y maxima del examen de math, writing y reading

Para writing

```bash
db.students.aggregate([
  {
    $group: {
      _id: null, 
      nota_minima: { $min: "$writing_score" }, 
      nota_maxima: { $max: "$writing_score" }  
    }
  }
])
```

Para math

```bash
db.students.aggregate([
  {
    $group: {
      _id: null, 
      nota_minima: { $min: "$math_score" }, 
      nota_maxima: { $max: "$math_score" }  
    }
  }
])
```

Para reading

```bash
db.students.aggregate([
  {
    $group: {
      _id: null, // Agrupación global
      nota_minima: { $min: "$reading_score" },
      nota_maxima: { $max: "$reading_score" }
    }
  }
])
```

Aplicacion y Resultado en consola

<img width="681" height="806" alt="image" src="https://github.com/user-attachments/assets/116dabce-0d15-4184-bf5c-99f3d8279677" />

# Analisis
// Podemos concluir , que hubo estudiantes a los cuales no han podado sacar ni un punto en math, resaltando que al menos la mayoría sabe leer y escribir, pero algunos no saben ni lo más básico de las matemáticas.


