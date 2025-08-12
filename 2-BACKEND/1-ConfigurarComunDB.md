## PARTE 3 - Configuracion de la comunDB
Para poder obtener acceso a la base de datos utilizando esta arquitectura, sera necesario crear un archivo comun que contenga metodos para conectarse a una base de datos, crear consultas y obtener los resultados. A continuacion se creara y configurara la clase ComunDB.

**Paso 1:** Ubicarse en la capa **"SistemaElParaisal.DAL"** y dar clic derecho y seleccionar **"Agregar > Clase"**.

![image](https://github.com/user-attachments/assets/f264c7fb-195b-43c3-a03f-b42bc0abde14)

**Paso 2:** Nombrar la clase **"ComunDB.cs"** y dar clic en **Agregar**.

![image](https://github.com/user-attachments/assets/be894ec9-9052-4585-9a65-24d27b8a4a46)

**Resultado:**
![image](https://github.com/user-attachments/assets/bca62f75-e4eb-47f0-9ffe-179c33d9d37a)

**Paso 3:** Establecer como **"public"** la clase **"ComunDB.cs"**

![image](https://github.com/user-attachments/assets/626de071-5dae-4384-ac90-8169fc14fdc7)

**Paso 4:** Agregar en la seccion de using las referencias a las bibliotecas de acceso a datos a utiizar.

```csharp
// Referencias
using System.Data;
using System.Data.SqlClient;
```

**Resultado:**
![image](https://github.com/user-attachments/assets/aa89eeb0-edde-46c8-98e5-245eb2a35bf7)

**Paso 5:** Agregar el String de conexion y metodos de acceso a datos.

```csharp
const string strConexion = @"Mi string de conexion aquí";

private static SqlConnection ObtenerConexion()
{
    SqlConnection conexion = new SqlConnection(strConexion);
    conexion.Open();
    return conexion;
}

public static SqlCommand ObtenerComando()
{
    SqlCommand comando = new SqlCommand();
    comando.Connection = ObtenerConexion();
    return comando;
}

public static SqlCommand ObtenerComando(SqlTransaction pTransaction)
{
    // Sobre carga del metodo ObtenerComando para crear comandos de transaccion
    SqlCommand comando = new SqlCommand();
    comando.Connection = pTransaction.Connection;
    comando.Transaction = pTransaction;
    return comando;
}

public static int EjecutarComando(SqlCommand pComando)
{
    int resultado = pComando.ExecuteNonQuery();
    pComando.Connection.Close();
    return resultado;
}

public static SqlDataReader EjecutarComandoReader(SqlCommand pComando)
{
    SqlDataReader reader = pComando.ExecuteReader(CommandBehavior.CloseConnection);
    return reader;
}

public static SqlTransaction CrearTransaction()
{
    SqlConnection conexion = ObtenerConexion();
    return conexion.BeginTransaction();
}
```

**Resultado:**
![image](https://github.com/user-attachments/assets/154ca133-ce3c-4143-8e05-5b2a354a973d)

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
using System.Data.SqlClient;

namespace SistemaElParaisal.DAL
{
    public class ComunDB
    {
        const string strConexion = @"Cadena de conexion aquí";

        private static SqlConnection ObtenerConexion()
        {
            SqlConnection conexion = new SqlConnection(strConexion);
            conexion.Open();
            return conexion;
        }

        public static SqlCommand ObtenerComando()
        {
            SqlCommand comando = new SqlCommand();
            comando.Connection = ObtenerConexion();
            return comando;
        }

        public static SqlCommand ObtenerComando(SqlTransaction pTransaction)
        {
            // Sobre carga del metodo ObtenerComando para crear comandos de transaccion
            SqlCommand comando = new SqlCommand();
            comando.Connection = pTransaction.Connection;
            comando.Transaction = pTransaction;
            return comando;
        }

        public static int EjecutarComando(SqlCommand pComando)
        {
            int resultado = pComando.ExecuteNonQuery();
            pComando.Connection.Close();
            return resultado;
        }

        public static SqlDataReader EjecutarComandoReader(SqlCommand pComando)
        {
            SqlDataReader reader = pComando.ExecuteReader(CommandBehavior.CloseConnection);
            return reader;
        }

        public static SqlTransaction CrearTransaction()
        {
            SqlConnection conexion = ObtenerConexion();
            return conexion.BeginTransaction();
        }
    }
}

```
