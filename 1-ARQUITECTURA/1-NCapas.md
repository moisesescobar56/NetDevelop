# ARQUITECTURA DE N-CAPAS EN .NET
## PARTE 1 - Creacion de la arquitectura N-Capas del proyecto
**Paso 1:** Abrir Visual Studio y Crear un nuevo proyecto.

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/c52e1137-235a-4d1d-b6d3-487d657bcbca" />



**Paso 2:** Seleccionar Crear una solucion en blanco y dar clic en Siguiente.

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/bea80627-b000-4bab-8459-9c7458d2cbcc" />



**Paso 3:** Nombrar a la solucion en blanco y dar clic en Crear.
```
SistemaElParaisal
```

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/f7689d7c-f4ad-4ecf-b842-86a21f3d4675" />


**Resultado:**

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/f5df2633-085b-44c0-8597-335efd1beacc" />



**Paso 4:** Dar clic derecho en la solucion y seleccionar **"Agregar > Nuevo proyecto"**. 

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/26b4ff0b-42b4-46e8-8dcd-a5c1aa704af0" />



**Paso 5:** Seleccionar una **Biblioteca de clases (.NET)** y dar clic en Siguiente.

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/e5374519-1aeb-425e-837f-6ece6c84d4cd" />


**Paso 6:** Nombrar a la **Biblioteca de clases (.NET)** y dar clic en Crear.
```
SistemaElParaisal.EN
```

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/6686b773-a0d8-426f-b95c-7b7cac4ec035" />

-
<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/f1cc9b0f-3b22-4ac2-b0e0-ef45f951d60f" />


**NOTA:** Eliminar el archivo **Class1.cs** siempre, solo aplica para **Biblioteca de clases (.NET)**


<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/0d7ce0c3-abb6-4c37-9a51-1580023e05b9" />


**Paso 7:** Crear como **Biblioteca de clases (.NET)** las capas:
- SistemaElParaisal.DAL
- SistemaElParaisal.BL

**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/c448fb1f-fed6-49d6-aa97-43fc9721577a" />


**Paso 8:** Dar clic derecho en la solucion y seleccionar **"Agregar > Nuevo proyecto"**. 

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/977435b0-d6d2-48cc-9909-8ee22cedc3b3" />

**Paso 9:** Seleccionar un **Proyecto de prueba unitaria(.NET)** y dar clic en Siguiente.

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/89b32314-15dc-42bd-be62-676525655a46" />


**Paso 10:** Nombrar al **Proyecto de prueba unitaria "MSTest" (.NET )** y dar clic en Siguiente.
```
SistemaElParaisal.Pruebas
```

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/ff5c8724-c984-4898-ab7e-1b849dc82708" />

-
<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/68c7becf-5ba0-4e5a-b2b2-706b8cd24ff4" />


**NOTA:** Eliminar el archivo Test1.cs siempre, solo aplica para **Proyecto de prueba unitaria "MSTest" (.NET)**

<img width="1416" height="925" alt="image" src="https://github.com/user-attachments/assets/d20e1d0f-7b89-49b5-a9e9-8945958899a2" />


**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/1a6c2a70-26b1-4264-bd0c-4eb5b985195c" />


**Paso 11:** Dar clic derecho en la solucion y seleccionar **"Agregar > Nuevo proyecto"**. 

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/8e684553-f089-48c3-896c-abd82f52d174" />

**Paso 12:** Agregar a la solucion un proyecto de tipo **"Aplicacion de Windows Forms (.NET)"**.

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/9561e54f-8427-4d7c-8dd0-32ba6e87f708" />

**Paso 13:** Nombrar el proyecto de tipo **"Aplicacion de Windows Forms (.NET)"** y dar clic en Siguiente.
```
SistemaElParaisal.UI.WinForms
```

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/88d556e8-3b49-4581-8b80-0df50dfbd511" />

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/d18e2e3c-625a-44f3-9b83-2730d585ca57" />

**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/6a27b214-83b8-49c9-9432-ed02e8c311a5" />


## PARTE 2 - Configuracion de la arquitectura N-Capas del proyecto
En este proyecto nos basaremos en la arquitectura de N-Capas en la cual creamos capas independientes con una unica funcion. Para la configuracion nos baseremos en el siguiente esquema:

![2023 G2_G5 - Desarrollo de CRUD en aplicación de Windows Forms](https://github.com/user-attachments/assets/0509b3e1-024f-4fe8-a8d8-aeb478db355a)


**Paso 1:** Ubicarse en la capa **"SistemaElParaisal.DAL"** y en la opcion de **"Referencias"** dar clic derecho y seleccionar **"> Agregar referencia"**.

![image](https://github.com/user-attachments/assets/2cf46927-d789-44f8-ba98-86e0b29cd227)

**Paso 2:** Ubicarse en la opcion **Proyectos > Solución** y marcar la opcion **"SistemaElParaisal.EN"**.

![image](https://github.com/user-attachments/assets/884568aa-ccc2-4628-b506-c57d303425c7)

**Paso 3:** Revisar que quede marcada la opcion **"SistemaElParaisal.EN"** y dar clic en **Aceptar**.

![image](https://github.com/user-attachments/assets/81866b3a-7dfa-4811-a1a8-39a29c4a340e)

**Resultado:**
![image](https://github.com/user-attachments/assets/9a26324e-4522-468d-99a7-11c2801d694d)

**Paso 4:** Ubicarse en la capa **"SistemaElParaisal.BL"** y en la opcion de **"Referencias"** dar clic derecho y seleccionar **"> Agregar referencia"**.

![image](https://github.com/user-attachments/assets/822a08e9-8937-4228-853a-54c94cd0f30e)

**Paso 5:** Ubicarse en la opcion **Proyectos > Solución** y marcar las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.DAL"**,

**Paso 6:** Revisar que quede marcada las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.DAL"**, luego dar clic en **Aceptar**.

![image](https://github.com/user-attachments/assets/363e99e3-60c3-46b8-b333-b71775b4942e)


**Resultado:**
![image](https://github.com/user-attachments/assets/f535cf15-fad5-4e10-aaba-9fdec6a639b4)

**Paso 7:** Ubicarse en la capa **"SistemaElParaisal.PruebasUnitarias"** y en la opcion de **"Referencias"** dar clic derecho y seleccionar **"> Agregar referencia"**.

![image](https://github.com/user-attachments/assets/8fe5c5e8-933c-4371-be2b-2ef2ff6ae01a)

**Paso 8:** Ubicarse en la opcion **Proyectos > Solución** y marcar las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.BL"**,

**Paso 9:** Revisar que quede marcada las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.BL"**, luego dar clic en **Aceptar**.

![image](https://github.com/user-attachments/assets/c7a11c9b-f673-4d76-9a5d-dd0ba58ff69d)

**Resultado:**
![image](https://github.com/user-attachments/assets/2def6596-0a93-4295-ae88-767738c36c5e)

**Paso 10:** Ubicarse en la capa **"SistemaElParaisal.UI.WinForms"** y en la opcion de **"Referencias"** dar clic derecho y seleccionar **"> Agregar referencia"**.

![image](https://github.com/user-attachments/assets/fcf7f924-cb18-4e0f-b9c0-d0378d5738e0)

**Paso 11:** Ubicarse en la opcion **Proyectos > Solución** y marcar las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.BL"**,

**Paso 12:** Revisar que quede marcada las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.BL"**, luego dar clic en **Aceptar**.

![image](https://github.com/user-attachments/assets/19c80196-e377-4857-ab5c-81769b798a33)

**Resultado:**
![image](https://github.com/user-attachments/assets/26c7a597-c8b0-432b-b692-e5676a03caff)

