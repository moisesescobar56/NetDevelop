## CONFIGURACION DE GIT EN VS: Aplica para todos los miembros del equipo. 
**Paso 1:** En Visual Studio acceder al menu de **Herramientas > Opciones**

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/f00c5f2a-5e59-404c-b512-1e1d3572f315" />

**Paso 2:** Buscar en la ventana, **Control de codigo fuente > Configuracion Global de Git** y en esta seccion configurar el **Nombre de usuario y Correo electronico** de Azure DevOps, al finalizar dar clic en **Aceptar**.

<img width="1408" height="918" alt="image" src="https://github.com/user-attachments/assets/1ebbb526-f808-460b-92d2-3025750dd00e" />


**NOTA:** Esta configuracion es necesaria para identificar quien modifica archivos en cualquier proyecto modificado en la computadora.

## PARTE 1: Asociacion del proyecto de Visual Studio con Git (Azure Repos).
**Paso 1:** Acceder al proyecto **SistemaElParaisal** en Azure DevOps.
**Paso 2:** Acceder a la opcion **Repos > Files** del proyecto **SistemaElParaisal** en Azure DevOps.
![image](https://github.com/user-attachments/assets/3f08fbdf-e123-4e7e-875e-483bdba892ed)
**Resultado:**
![image](https://github.com/user-attachments/assets/6bd7a241-237a-4b44-ac62-572cb5ff6ba5)

**Paso 4:** Copiar la direccion HTTPS del repositorio.
<img width="1366" height="738" alt="image" src="https://github.com/user-attachments/assets/7f1cabb1-058a-49d3-8f2e-7d1e43a078ab" />

### IMPORTANTE: *REVISAR TENER ACCESO A INTERNET y GUARDA CAMBIOS EN VISUAL STUDIO.*
**Paso 7:** En Visual Studio dar clic derecho en la solucion y seleccionar **Crear respositorio de Git**.
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/36195915-e6c0-4a7f-a2d3-5237d9b0b6d0" />

**Paso 8:** Seleccionar la opcion, **Repositorio remoto existente** y pegar la Url copiada anteriormente.
<img width="1410" height="929" alt="image" src="https://github.com/user-attachments/assets/f20722aa-ba2d-4901-89eb-14cc54dadcf1" />

**Paso 9:** Dar clic en **Crear y Enviar los Cambios**.

<img width="1410" height="922" alt="image" src="https://github.com/user-attachments/assets/015df35d-4251-4cde-82f5-346d5b1eb508" />

**Paso 10:** Inicia sesion en Git Credential Manager con tu cuenta de Azure DevOps.
<img width="1413" height="982" alt="image" src="https://github.com/user-attachments/assets/7c078a21-d420-4086-88cf-a6b073e370a2" />

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/6cc48f05-55ae-49c9-bd74-df19a8508a68" />

**Termina el inicio de sesion**

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/887072de-8a4a-4b63-90b5-ac876b6a4f0d" />

**Resultado**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/af0f475a-4bba-4e3c-9411-35473c1e6f77" />


**Paso 11:** Regresa al menu Repos de tu proyecto, ahora tendras 1 rama **main**. 
<img width="1559" height="869" alt="image" src="https://github.com/user-attachments/assets/267aa6b8-4cb4-4c2f-9eae-dfcb5b274886" />


### ¡Felicitaciones! Has concluido la Lección 2
