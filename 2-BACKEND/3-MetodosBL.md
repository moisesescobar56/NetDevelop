# CODIFICACION DE METODOS EN LA CAPA BL

## PARTE 1 - Analisis de metodos segun diagrama de clases
Es recomendable haber definido en algun documento (diagrama de clases) los metodos intermediarios correspondientes a cada clase de nuestro modelo de datos (tablas de la base de datos). Antes de iniciar debemos auxiliarnos en el diagrama de clases e identificar los metodos a crear para cada clase en la capa BL.
![image](https://github.com/user-attachments/assets/b50c27ce-6abc-4d71-bbce-e5aa906673ca)

## PARTE 2 - Creacion de clases y metodos
Los metodos intermediarios con la **"Capa de interfaz de Usuario (UI)"**, deben crearse en la **"Capa de Logica de Negocios (BL)"** como se muestra en el siguiente esquema: 

![image](https://github.com/user-attachments/assets/f87d8242-b7fa-4357-b04f-e44b1ba6549f)

Es importante respetar el orden de creacion del diagrama de clases. Para el ejemplo solo se trabajara con los metodos  de las clases **Cargo y Empleado**, pero en un escenario real se iran creando las clases segun sea necesario.

![image](https://github.com/user-attachments/assets/dcc9bfd9-6e92-4574-aef8-4fd7b8580d91)

**IMPORTANTE:** se recomienda primero crear los archivos de clases, establecerlas como **"public"** y luego codificarlas.


## PARTE 3 - Metodos EmpleadoBL
**Paso 1:** Ubicarse en la capa **"SistemaElParaisal.BL"** y dar clic derecho y seleccionar **"Agregar > Clase"**.

<img width="1413" height="944" alt="image" src="https://github.com/user-attachments/assets/7fc47d0d-0786-4e10-922c-88799ac7bef8" />

**Paso 2:** Nombrar la clase **"EmpleadoBL.cs"** y dar clic en **Agregar**.

<img width="1412" height="941" alt="image" src="https://github.com/user-attachments/assets/47677f9a-964b-4fcf-981b-d9da0c4c40a7" />

**Paso 3:** Establecer como **"public"** la clase **"EmpleadoBL.cs"** y **Guardar** los cambios.

<img width="1413" height="944" alt="image" src="https://github.com/user-attachments/assets/8796ccfd-d6d0-444f-b119-5cc23741f962" />

**Paso 4:** Agregar en la seccion de using las referencias a las bibliotecas del proyecto a utilizar.

```csharp
//Referencias
using System.Security.Cryptography;
// Referencias del proyecto
using SistemaElParaisal.EN;
using SistemaElParaisal.DAL;
```
**Resultado:**
<img width="1413" height="944" alt="image" src="https://github.com/user-attachments/assets/3a96684f-4137-43ed-b46f-9e3b899cffbe" />


**Paso 4:** Codificar los metodos intermediarios CRUD de **EmpleadoBL** segun el diagrama de clases y **Guardar** los cambios.

![image](https://github.com/user-attachments/assets/f5f35585-645f-45aa-8347-88327f4dc4ad)

```csharp
private static string CifrarSha256(string pTexto)
{ 
    byte[] bytes = Encoding.Unicode.GetBytes(pTexto); // Codificar el texto a bytes
    // Crear y usar SHA256 de forma segura
    using (SHA256 sha256 = SHA256.Create()) 
    {
        byte[] hash = sha256.ComputeHash(bytes);
        // Convertir hash a cadena hexadecimal
        StringBuilder hashString = new StringBuilder();
        foreach (byte x in hash)
        {
            hashString.AppendFormat("{0:x2}", x);
        }
        return hashString.ToString();
    }
}
public int Guardar(Empleado pEmpleado)
{
    pEmpleado.Clave = CifrarSha256(pEmpleado.Clave); // encriptar contraseña
    return EmpleadoDAL.Guardar(pEmpleado);
}
public int Modificar(Empleado pEmpleado)
{
    pEmpleado.Clave = CifrarSha256(pEmpleado.Clave); // encriptar contraseña
    return EmpleadoDAL.Modificar(pEmpleado);
}
public int Eliminar(Empleado pEmpleado)
{
    return EmpleadoDAL.Eliminar(pEmpleado);
}
public Empleado ObtenerPorId(short pIdEmpleado)
{
    return EmpleadoDAL.ObtenerPorId(pIdEmpleado);
}
public List<Empleado> Buscar(Empleado pEmpleado)
{
    return EmpleadoDAL.Buscar(pEmpleado);
}
```
- **CifrarSha256:** Metodo secreto creado para cifrar textos generando un Hash unico de SHA256.

### NOTA: El metodo CifrarSha256 solo se usa en clases de Usuario que necesiten encriptar campos como clave/contraseña o similar. Para otras clases no debe incluirse. 

**Resultado:**
<img width="1413" height="1032" alt="image" src="https://github.com/user-attachments/assets/8c9b80ac-c546-4a02-a1b3-4c924e7a5c79" />


## PARTE 4 - Metodos CargoBL
**Paso 1:** Ubicarse en la capa **"SistemaElParaisal.BL"** y dar clic derecho y seleccionar **"Agregar > Clase"**.

<img width="1413" height="888" alt="image" src="https://github.com/user-attachments/assets/8247508c-a810-417d-8abd-4d8d6a05ecac" />


**Paso 2:** Nombrar la clase **"CargoBL.cs"** y dar clic en **Agregar**.

<img width="1409" height="888" alt="image" src="https://github.com/user-attachments/assets/ff070ef6-db8c-47eb-a747-8bf96e5637a2" />


**Paso 3:** Establecer como **"public"** la clase **"CargoBL.cs"** y **Guardar** los cambios.

<img width="1413" height="888" alt="image" src="https://github.com/user-attachments/assets/11f0f53d-0033-4fe6-a9de-a2c67b909c58" />


**Paso 4:** Agregar en la seccion de using las referencias a las bibliotecas del proyecto a utilizar.

```csharp
// Referencias
using SistemaElParaisal.EN;
using SistemaElParaisal.DAL;
```
**Resultado:**
<img width="1413" height="888" alt="image" src="https://github.com/user-attachments/assets/67875869-0f87-4dbc-8a0e-6fcd0e5c0a6f" />


**Paso 4:** Codificar los metodos intermediarios de **CargoBL** segun el diagrama de clases y **Guardar** los cambios.

![image](https://github.com/user-attachments/assets/4ee01977-4ec0-4b54-aa1d-5298ad77d3d6)

```csharp
public Cargo ObtenerPorId(byte pIdCargo)
{
    return CargoDAL.ObtenerPorId(pIdCargo);
}
public List<Cargo> Buscar(Cargo pCargo)
{
    return CargoDAL.Buscar(pCargo);
}
```

**Resultado:**
<img width="1413" height="888" alt="image" src="https://github.com/user-attachments/assets/e02c860b-c252-47e5-b446-06478433b94b" />


### **NOTA:** Al iniciar un proyecto es recomendable crear primero los archivos con accesibilidad publica y luego codificarlos. 

## Archivo **CargoBL.cs**
```csharp
// Referencias
using SistemaElParaisal.EN;
using SistemaElParaisal.DAL;

namespace SistemaElParaisal.BL
{
    public class CargoBL
    {
        public Cargo ObtenerPorId(byte pIdCargo)
        {
            return CargoDAL.ObtenerPorId(pIdCargo);
        }
        public List<Cargo> Buscar(Cargo pCargo)
        {
            return CargoDAL.Buscar(pCargo);
        }
    }
}
```

## Archivo **EmpleadoBL.cs**
```csharp
//Referencias
using SistemaElParaisal.DAL;
// Referencias del proyecto
using SistemaElParaisal.EN;
using System.Security.Cryptography;
using System.Text;

namespace SistemaElParaisal.BL
{
    public class EmpleadoBL
    {
        private static string CifrarSha256(string pTexto)
        { 
            byte[] bytes = Encoding.Unicode.GetBytes(pTexto); // Codificar el texto a bytes
            // Crear y usar SHA256 de forma segura
            using (SHA256 sha256 = SHA256.Create()) 
            {
                byte[] hash = sha256.ComputeHash(bytes);
                // Convertir hash a cadena hexadecimal
                StringBuilder hashString = new StringBuilder();
                foreach (byte x in hash)
                {
                    hashString.AppendFormat("{0:x2}", x);
                }
                return hashString.ToString();
            }
        }
        public int Guardar(Empleado pEmpleado)
        {
            pEmpleado.Clave = CifrarSha256(pEmpleado.Clave); // encriptar contraseña
            return EmpleadoDAL.Guardar(pEmpleado);
        }
        public int Modificar(Empleado pEmpleado)
        {
            pEmpleado.Clave = CifrarSha256(pEmpleado.Clave); // encriptar contraseña
            return EmpleadoDAL.Modificar(pEmpleado);
        }
        public int Eliminar(Empleado pEmpleado)
        {
            return EmpleadoDAL.Eliminar(pEmpleado);
        }
        public Empleado ObtenerPorId(short pIdEmpleado)
        {
            return EmpleadoDAL.ObtenerPorId(pIdEmpleado);
        }
        public List<Empleado> Buscar(Empleado pEmpleado)
        {
            return EmpleadoDAL.Buscar(pEmpleado);
        }
    }
}
```
