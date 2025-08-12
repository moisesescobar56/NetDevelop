# Configuracion de la comunDB
Para poder obtener acceso a la base de datos utilizando esta arquitectura, sera necesario crear un archivo comun que contenga metodos para conectarse a una base de datos, crear consultas y obtener los resultados. A continuacion se creara y configurara la clase ComunDB.

### PARTE 1: Instalar Microsoft.Data.SqlClient en capa DAL

**Paso 1:** Ubicarse en la capa **"SistemaElParaisal.DAL"** y dar clic derecho y seleccionar **"Administrar paquetes nuget"**.
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/3ae68e90-0d04-46c7-8d08-d9de9a22610b" />

**Resultado:**

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/5707adad-060f-4ac8-a6a8-05f4ed9a535b" />

**Paso 2:** En la pestaña **"Examinar"**, buscar el paquete "Microsoft.Data.SqlClient".
```
Microsoft.Data.SqlClient
```
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/864764a9-90a2-4e50-81be-6f336fb97d4a" />

**Paso 3:** Seleccionar el primer resultado y dar clic en el boton **"Instalar"**.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/ff9c3c96-6974-4b2e-b4dc-cd25f1545e6e" />

**Paso 4:** Dar clic en **"Aplicar"** para aceptar la instalacion del paquete.

<img width="1409" height="920" alt="image" src="https://github.com/user-attachments/assets/5cb0eec7-affd-4155-b01d-79ea8d9d71ba" />

**Paso 5:** Dar clic en **"Aceptar"** para aceptar el uso de las licencias del paquete.

<img width="1411" height="924" alt="image" src="https://github.com/user-attachments/assets/b62577f7-dcba-4de5-9bf3-bf8a9a321dcc" />

**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/42b11992-94e1-4771-b00e-75120f90a5d2" />

### PARTE 2: Codificacion de clase ComunDB.cs

**Paso 1:** Ubicarse en la capa **"SistemaElParaisal.DAL"** y dar clic derecho y seleccionar **"Agregar > Clase"**.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/dc87e334-8fb0-4534-923b-1d9f78e4ec9c" />

**Paso 2:** Nombrar la clase **"ComunDB.cs"** y dar clic en **Agregar**.

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/ae6ad656-2bc3-447f-9d78-dc383ec86380" />


**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/4660c781-344f-44be-81dd-ceebdfc304e8" />

**Paso 3:** Establecer como **"public"** la clase **"ComunDB.cs"**

<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/187a7d53-ed94-4f97-8afe-c24f09d2a221" />


**Paso 4:** Agregar en la seccion de using las referencias a las bibliotecas de acceso a datos a utiizar.

```csharp
// referencias
using System.Data;
using Microsoft.Data.SqlClient;
```

**Resultado:**
<img width="1413" height="925" alt="image" src="https://github.com/user-attachments/assets/a0a38049-2696-48f7-8898-0518cb0a56c6" />


**Paso 5:** Agregar el String de conexion y metodos de acceso a datos.

```csharp
const string strConexion = @"Mi string de conexion aquí";

private static SqlConnection ObtenerConexion()
{
    var conexion = new SqlConnection(strConexion);
    conexion.Open();
    return conexion;
}

public static SqlCommand ObtenerComando()
{
    return new SqlCommand
    {
        Connection = ObtenerConexion()
    };
}

public static SqlCommand ObtenerComando(SqlTransaction transaccion)
{
    return new SqlCommand
    {
        Connection = transaccion.Connection,
        Transaction = transaccion
    };
}

public static int EjecutarComando(SqlCommand comando)
{
    try
    {
        return comando.ExecuteNonQuery();
    }
    finally
    {
        comando.Connection?.Close();
    }
}

public static SqlDataReader EjecutarComandoReader(SqlCommand comando)
{
    return comando.ExecuteReader(CommandBehavior.CloseConnection);
}

public static SqlTransaction CrearTransaccion()
{
    var conexion = ObtenerConexion();
    return conexion.BeginTransaction();
}
```

**Resultado:**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8e94c1e8-a32d-4c2f-b4b6-9f1ca8b0a1fe" />


### Configurar String de conexion
Ver video: https://youtu.be/oct6MWqZhoE?si=cSlDKBCiX8MflLDY

## Archivo **ComunDB.cs**
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
// Referencias
using System.Data;
using Microsoft.Data.SqlClient;

namespace SistemaElParaisal.DAL
{
    public class ComunDB
    {
        const string strConexion = @"Mi string de conexion aquí";

        private static SqlConnection ObtenerConexion()
        {
            var conexion = new SqlConnection(strConexion);
            conexion.Open();
            return conexion;
        }

        public static SqlCommand ObtenerComando()
        {
            return new SqlCommand  { Connection = ObtenerConexion() };
        }

        public static SqlCommand ObtenerComando(SqlTransaction transaccion)
        {
            return new SqlCommand
            {
                Connection = transaccion.Connection,
                Transaction = transaccion
            };
        }

        public static int EjecutarComando(SqlCommand comando)
        {
            try
            {
                return comando.ExecuteNonQuery();
            }
            finally
            {
                comando.Connection?.Close();
            }
        }

        public static SqlDataReader EjecutarComandoReader(SqlCommand comando)
        {
            return comando.ExecuteReader(CommandBehavior.CloseConnection);
        }

        public static SqlTransaction CrearTransaccion()
        {
            var conexion = ObtenerConexion();
            return conexion.BeginTransaction();
        }
    }
}
```
