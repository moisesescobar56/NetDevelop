## CONFIGURACION DE GIT EN VS: Aplica para todos los miembros del equipo. 
**Paso 1:** En Visual Studio acceder al menu de **Herramientas > Opciones**

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/f00c5f2a-5e59-404c-b512-1e1d3572f315" />

**Paso 2:** Buscar en la ventana, **Control de codigo fuente > Configuracion Global de Git** y en esta seccion configurar el **Nombre de usuario y Correo electronico** de Azure DevOps, al finalizar dar clic en **Aceptar**.

<img width="1408" height="918" alt="image" src="https://github.com/user-attachments/assets/1ebbb526-f808-460b-92d2-3025750dd00e" />


**NOTA:** Esta configuracion es necesaria para identificar quien modifica archivos en cualquier proyecto modificado en la computadora.

## PARTE 3: Asociacion del proyecto de Visual Studio con Git (Azure Repos).
**Paso 1:** Acceder al proyecto **SistemaElParaisal** en Azure DevOps.
**Paso 2:** Acceder a la opcion **Repos > Files** del proyecto **SistemaElParaisal** en Azure DevOps.
![image](https://github.com/user-attachments/assets/3f08fbdf-e123-4e7e-875e-483bdba892ed)
**Resultado:**
![image](https://github.com/user-attachments/assets/6bd7a241-237a-4b44-ac62-572cb5ff6ba5)
**Paso 3:** Hasta el final de la pagina web, Configurar el **.gitignore** como **"Visual Studio"** y dar clic en **Initialize**..
![image](https://github.com/user-attachments/assets/a7a9ed5f-615e-4372-b049-6e6d371b2eed)
**Paso 5:** Dar clic en la opcion Clone.
![image](https://github.com/user-attachments/assets/204b2e7c-c348-4679-b462-0207f6b2b297)
**Paso 6:** Copiar la direccion HTTPS del repositorio.
![image](https://github.com/user-attachments/assets/e39f5fdd-9af9-4040-a8a8-5e83dd7becce)
### IMPORTANTE: REVISAR TENER ACCESO A INTERNET y GUARDA CAMBIOS EN VISUAL STUDIO.
**Paso 7:** En Visual Studio dar clic derecho en la solucion y seleccionar **Crear respositorio de Git**.
![image](https://github.com/user-attachments/assets/f1e952da-ce1e-44ab-9f74-82ce7084d806)
![image](https://github.com/user-attachments/assets/ef72e194-5243-49c1-b380-32fd2ab230eb)
**Paso 8:** Seleccionar la opcion, **Repositorio remoto existente**
![image](https://github.com/user-attachments/assets/71a670c2-839a-4872-a037-e02e6ef38044)
**Paso 9:** Dar clic en Crear y Enviar los Cambios
![image](https://github.com/user-attachments/assets/006794cc-8465-45fd-8029-b031837e3d7c)
**Paso 10:** Inicia sesion en Git Credential Manager con tu cuenta de Azure DevOps.
![image](https://github.com/user-attachments/assets/a82b40d5-41e1-4ce3-b514-a7704fe9fd42)
**Termina el inicio de sesion**
![image](https://github.com/user-attachments/assets/c641bc4f-4b71-46a3-87aa-0d9090344927)
**Paso 11:** Regresa al menu Repos de tu proyecto, ahora tendras 2 ramas, **main y master**. Por defecto Visual Studio sube los cambios en la rama master. 
![image](https://github.com/user-attachments/assets/13670b58-f3cf-4c4a-9be6-696e3f28ab2c)
**Paso 12:** Accede a la rama **master** y tendras los archivos del proyecto.
![image](https://github.com/user-attachments/assets/a24d98d8-c279-42a4-880e-a9f0e196262f)

## PARTE 4: Clonacion del proyecto desde Git.
**IMPORTANTE:** Este paso no aplica para el miembro del equipo que creo el proyecto y lo subio al repositorio de Azure DevOps.

**Paso 1:** Abrir en el navegador el proyecto de Azure DevOps, dirigirse a **Repos > Files** en la rama **master**.
![image](https://github.com/user-attachments/assets/58e37d80-921f-4645-b6a5-74bbd18eb9dc)
**Paso 2:** Dar clic en la opcion Clone.
![image](https://github.com/user-attachments/assets/16f4ea39-4383-42c2-9043-6875c1126864)
**Paso 3:** Copiar la direccion HTTPS del repositorio.
![image](https://github.com/user-attachments/assets/4f24f3ff-e0c4-4ccf-9474-91322cf80e46)
**Paso 4:** Abrir Visual Studio y seleccionar Clonar un repositorio.
![image](https://github.com/user-attachments/assets/32abb7af-369b-4116-bc44-d65d16e0f09a)
**Resultado:**
![image](https://github.com/user-attachments/assets/c8d320b3-d719-4507-8d3c-6a5f7739b344)
**Paso 5:** Pegar la direccion HTTPS del repositorio y dar clic en Clonar.
![image](https://github.com/user-attachments/assets/508f9055-f72e-42b5-a377-74bee6fe4f23)
**Resultado:** No apareceran los archivos del proyecto, porque si nos fijamos en la esquina inferior derecha, estamos en la rama **main**
![image](https://github.com/user-attachments/assets/e7789ab7-930d-4216-8980-d88ebcaee57b)
**Paso 6:** Dar clic en la rama **main**
![image](https://github.com/user-attachments/assets/0258dada-f392-412d-bbe2-f1ad2c0affd3)
**Paso 7:** Dar clic en Remotos y seleccionar la rama **master**
![image](https://github.com/user-attachments/assets/882dad27-ca61-4e86-9de1-cdf5349efa3f)
**Resultado:** Ya aparecen los archivos de nuestro proyecto.
![image](https://github.com/user-attachments/assets/8816a678-36e2-4d77-b358-c67a75cad37e)
**Paso 8:** Dar doble clic sobre la **solucion** para abrir el proyecto. 
![image](https://github.com/user-attachments/assets/ab9ea0e9-88de-4072-a94c-9e30e7401e40)
**Resultado:**
![image](https://github.com/user-attachments/assets/3c755ad9-da18-4e98-b585-2c229648e7f3)
