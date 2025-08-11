# CLONAR REPOSITORIO GIT EN VISUAL STUDIO
## CONFIGURACION DE GIT EN VS: Aplica para todos los miembros del equipo. 
**Paso 1:** En Visual Studio acceder al menu de **Herramientas > Opciones**

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/f00c5f2a-5e59-404c-b512-1e1d3572f315" />

**Paso 2:** Buscar en la ventana, **Control de codigo fuente > Configuracion Global de Git** y en esta seccion configurar el **Nombre de usuario y Correo electronico** de Azure DevOps, al finalizar dar clic en **Aceptar**.

<img width="1408" height="918" alt="image" src="https://github.com/user-attachments/assets/1ebbb526-f808-460b-92d2-3025750dd00e" />

## PARTE 1: Clonacion del proyecto desde Git.
**IMPORTANTE:** Este paso no aplica para el miembro del equipo que creo el proyecto y lo subio al repositorio de Azure DevOps.

**Paso 1:** Abrir en el navegador el proyecto de Azure DevOps, dirigirse a **Repos > Files** en la rama **main**.
<img width="1561" height="869" alt="image" src="https://github.com/user-attachments/assets/58cfb6e3-a5a0-4106-820e-fe8680850cfd" />

**Paso 2:** Dar clic en la opcion Clone.
<img width="1559" height="869" alt="image" src="https://github.com/user-attachments/assets/ee9ff8cf-0483-4a6b-ac9d-6b344938e864" />

**Paso 3:** Copiar la direccion HTTPS del repositorio.

<img width="1559" height="869" alt="image" src="https://github.com/user-attachments/assets/c7888550-d90d-4597-9e46-2d4653e6dc95" />

**Paso 4:** Abrir Visual Studio y seleccionar Clonar un repositorio.
<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/47376df5-91d2-4728-b841-c7a5ad180d24" />

**Resultado:**
<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/5cf9e88e-26c1-4ba0-a877-f5cc0efd90f5" />

**Paso 5:** Pegar la direccion HTTPS del repositorio y dar clic en Clonar.

<img width="1014" height="675" alt="image" src="https://github.com/user-attachments/assets/54b0ab04-0102-42f4-9b25-af8fcc429c3b" />

### NOTA: Iniciar sesion si es necesiario.


**Resultado:** No apareceran los archivos del proyecto, nos fijamos en la esquina inferior derecha, estamos en la rama **main** en el menu de **Cambios de GIT**.
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/746a5850-9ccd-4109-88c4-616824dcac31" />

**Paso 6:** Damos clic en **Explorador de soluciones** , ya aparecen los archivos de nuestro proyecto.
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/fe89e2c8-fd18-4ab4-b036-354e85a132e7" />

### ¡Felicitaciones! Has concluido la Lección 3
