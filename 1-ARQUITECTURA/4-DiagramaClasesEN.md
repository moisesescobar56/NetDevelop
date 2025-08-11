# IMPLEMENTACION DE CLASES EN EL PROYECTO 

## PARTE 1 - Analisis de clases segun modelo de datos
Al inicio de todo proyecto es recomendable haber hecho un analisis de la solucion que quiere construir, con el fin de contemplar que datos llegara a manipular el proyecto al completarlo, de no realizarse el analisis los desarrolladores deberan realizar cambios constantes en el modelo de datos, lo cual afectara la duracion estimada de entrega. 

Para mitigar esta problematica, nos auxilaremos de buenas practicas y modelaremos el diagrama de clases de nuestra solucion. 
![image](https://github.com/user-attachments/assets/b50c27ce-6abc-4d71-bbce-e5aa906673ca)

## PARTE 2 - Creacion de clases
Las clases de nuestro modelo de datos debe crearse en la **"Capa de entidades (EN)"** como se muestra en el siguiente esquema: 
![image](https://github.com/user-attachments/assets/83880c6b-fb27-4909-b10f-94987ce025c5)

Es importante respetar el orden de creacion del diagrama de clases. Para el ejemplo solo se trabajara con las clases **Cargo y Empleado**, pero en un escenario real se deben crear todas las clases.

![image](https://github.com/user-attachments/assets/dcc9bfd9-6e92-4574-aef8-4fd7b8580d91)

**IMPORTANTE:** se recomienda primero crear los archivos de clases, establecerlas como **"public"** y luego codificarlas.

**Paso 1:** Ubicarse en la capa **"SistemaElParaisal.EN"** y dar clic derecho y seleccionar **"Agregar > Clase"**.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/6188006a-483d-4843-9ba3-3b90e78d749f" />


**Paso 2:** Nombrar la clase **"Cargo.cs"** y dar clic en **Agregar**.

<img width="1410" height="925" alt="image" src="https://github.com/user-attachments/assets/950fedbf-d0d4-4d6b-97f7-e976ad40ba89" />


**Paso 3:** Establecer como **"public"** la clase **"Cargo.cs"** y **Guardar** los cambios.

![image](https://github.com/user-attachments/assets/a37431da-d7b2-4e17-81cb-5b19ba0a4ddb)

**Paso 4:** Codificar las propiedades de **Cargo** segun el diagrama de clases y **Guardar** los cambios.

![image](https://github.com/user-attachments/assets/a8c4fc82-99d8-49e6-9bfa-34848c4d4875)

```csharp
public byte IdCargo { get; set; }  
public string Nombre { get; set; } = string.Empty;
```

**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/fb98e571-7e38-4100-b019-1b0742c6a8f8" />


**Paso 5:** Ubicarse en la capa **"SistemaElParaisal.EN"** y dar clic derecho y seleccionar **"Agregar > Clase"**.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/bd01027b-3e57-4c20-833d-cc1695f017aa" />


**Paso 6:** Nombrar la clase **"Empleado.cs"** y dar clic en **Agregar**.

<img width="1409" height="920" alt="image" src="https://github.com/user-attachments/assets/cc0fbdd0-50c8-4dea-ae4c-612e440408ff" />


**Paso 7:** Establecer como **"public"** la clase **"Empleado.cs"** y **Guardar** los cambios.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/eea02dbb-6ab7-47fb-8570-85cc0d0feed6" />

**Paso 8:** Codificar las propiedades de **Empleado** segun el diagrama de clases y **Guardar** los cambios.

![image](https://github.com/user-attachments/assets/c8f86b73-ae8e-42bc-a1f8-a3d33f00cfd8)

```csharp
public short IdEmpleado { get; set; }
public short IdCargo { get; set; } // FK
public string Nombre { get; set; } = string.Empty;
public string Apellido { get; set; } = string.Empty;
public string Telefono { get; set; } = string.Empty;
public string Clave { get; set; } = string.Empty;

// Propiedades virtuales para llaves foraneas (FK) para representar la Asociacion
public virtual Cargo Cargo { get; set; } = new Cargo(); 
```

**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/81d037d1-8012-4040-b47f-6324cd772d26" />


### **NOTA:** Al iniciar un proyecto es recomendable crear primero los archivos con accesibilidad publica y luego codificarlos. 

## Archivo **Cargo.cs**
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace SistemaElParaisal.EN
{
    public class Cargo
    {
        public byte IdCargo { get; set; }
        public string Nombre { get; set; } = string.Empty;
    }
}
```

## Archivo **Empleado.cs**
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace SistemaElParaisal.EN
{
    public class Empleado
    {
        public short IdEmpleado { get; set; }
        public short IdCargo { get; set; } // FK
        public string Nombre { get; set; } = string.Empty;
        public string Apellido { get; set; } = string.Empty;
        public string Telefono { get; set; } = string.Empty;
        public string Clave { get; set; } = string.Empty;

        // Propiedades virtuales para llaves foraneas (FK) para representar la Asociacion
        public virtual Cargo Cargo { get; set; } = new Cargo();
    }
}
```
