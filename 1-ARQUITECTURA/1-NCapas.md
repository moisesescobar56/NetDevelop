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


## PARTE 2 - Dependencias N-Capas del proyecto
En este proyecto nos basaremos en la arquitectura de N-Capas en la cual creamos capas independientes con una unica funcion. Para la configuracion nos baseremos en el siguiente esquema:

![2023 G2_G5 - Desarrollo de CRUD en aplicación de Windows Forms](https://github.com/user-attachments/assets/0509b3e1-024f-4fe8-a8d8-aeb478db355a)


**Paso 1:** Ubicarse en la capa **"SistemaElParaisal.DAL"** y en la opcion de **"Dependencias"** dar clic derecho y seleccionar **"> Agregar referencia"**.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/468a640c-72fc-4e1a-b1e6-d6bd3b14a1d2" />

**Paso 2:** Ubicarse en la opcion **Proyectos > Solución** y marcar la opcion **"SistemaElParaisal.EN"**.

<img width="1407" height="923" alt="image" src="https://github.com/user-attachments/assets/e94cc35e-c5d3-44a3-a1f4-e0ac0eeff5be" />


**Paso 3:** Revisar que quede marcada la opcion **"SistemaElParaisal.EN"** y dar clic en **Aceptar**.

<img width="1408" height="923" alt="image" src="https://github.com/user-attachments/assets/511526f8-fd24-47bc-887b-857ddafe51fe" />

**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/7a9b54a6-1615-40fa-b384-85f9ab454dab" />


**Paso 4:** Ubicarse en la capa **"SistemaElParaisal.BL"** y en la opcion de **"Dependencias"** dar clic derecho y seleccionar **"> Agregar referencia"**.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/42a1909a-6e82-424e-bd28-29f5bfeb888a" />


**Paso 5:** Ubicarse en la opcion **Proyectos > Solución** y marcar las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.DAL"**,

**Paso 6:** Revisar que quede marcada las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.DAL"**, luego dar clic en **Aceptar**.

<img width="1413" height="922" alt="image" src="https://github.com/user-attachments/assets/9d22f7f3-b729-4a2b-a9c8-0eabb1067fa0" />

**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/909c11ec-4648-48d6-a069-8a2f2679b558" />


**Paso 7:** Ubicarse en la capa **"SistemaElParaisal.Pruebas"** y en la opcion de **"Dependencias"** dar clic derecho y seleccionar **"> Agregar referencia"**.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/671c8491-ab43-4c3d-981a-f11c863db1aa" />


**Paso 8:** Ubicarse en la opcion **Proyectos > Solución** y marcar las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.BL"**,

**Paso 9:** Revisar que quede marcada las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.BL"**, luego dar clic en **Aceptar**.

<img width="1410" height="923" alt="image" src="https://github.com/user-attachments/assets/ec70c98d-9d76-4228-ac40-a05872d9e528" />


**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/b1f07e9a-753f-4d01-aad8-ce9ade64e406" />

**Paso 10:** Ubicarse en la capa **"SistemaElParaisal.UI.WinForms"** y en la opcion de **"Dependencias"** dar clic derecho y seleccionar **"> Agregar referencia"**.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/873c917b-bedc-4ea1-852d-cd1f8de2160b" />


**Paso 11:** Ubicarse en la opcion **Proyectos > Solución** y marcar las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.BL"**,

**Paso 12:** Revisar que quede marcada las opciones **"SistemaElParaisal.EN"**  y **"SistemaElParaisal.BL"**, luego dar clic en **Aceptar**.

<img width="1410" height="924" alt="image" src="https://github.com/user-attachments/assets/a918276a-1a91-48e4-b4cb-ee4786e93dad" />


**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/c806c6e6-5124-4727-baf3-9f839cba63d2" />


