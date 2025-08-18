# CONFIGURACIÓN CAPA UI EN WINDOWS FORMS

En todo proyecto **el equipo de desarrollo deben seguir convenciones** para tener **nombres de archivos estandarizados**, por ello es importante definir la nomenclatura y estandar a utilizar. Por comodidad en el **desarrollo .NET** se sigue las reglas del **estandar PasCal**, recomendado por Microsoft, que lo implementa en sus librerias y Frameworks. 

<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/1eaab0ef-96ec-4eda-a229-dc9f73d9e62e" />


## PARTE 1 - Creacion y configuracion de formularios, carpetas y clases

**Paso 1:** Abrir Visual Studio y Configurar los siguientes archivos:
- Administracion
  - AdminEmpleadoForm.cs
- Registro
  - RegistroEmpleadoForm.cs 
- Reportes
- ViewModels
- ToolsForms.cs

## Ver tutorial: [https://youtu.be/8F7qcFjpcFY](https://youtu.be/XbnnO9nBeb4)

**Resultado:**
<img width="1413" height="857" alt="image" src="https://github.com/user-attachments/assets/e1c7a48b-2dc6-4534-9519-33adba107004" />


## PARTE 2 - Configuracion de la clase ***"ToolsForms.cs"***
**Paso 1:** abrir la clase **"ToolsForms.cs"**.

<img width="1413" height="857" alt="image" src="https://github.com/user-attachments/assets/a19a9c08-9445-4001-a3ba-f2216563dae5" />

**Paso 2:** agregar los using de las referencias de las bibliotecas a utilizar.
```csharp
///Referencias
using System.Windows.Forms;
```

<img width="1413" height="857" alt="image" src="https://github.com/user-attachments/assets/c8919d06-8449-4e52-bf97-ffb532ad19df" />


**Paso 3:** programar los metodos de las herramientas a implementar en la clase **"ToolsForms.cs"**.
```csharp
public static long ObtenerIdGrid(DataGridView pDataGridView)
{
    // Metodo para obtener el id de registro seleccionado en un DataGridView
    try
    {
        long idTabla = 0;
        // Obtener la PK del registro seleccionado
        idTabla = Convert.ToInt64(pDataGridView.Rows[pDataGridView.CurrentRow.Index].Cells[0].Value.ToString());
        return idTabla;
    }
    catch (Exception ex)
    {
        return 0;
    }
}

public static DialogResult MessageBoxConfirmar()
{
    return MessageBox.Show("¿Desea eliminar el registro seleccionado?", "Eliminar", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
}
```
**Resultado:**
<img width="1647" height="857" alt="image" src="https://github.com/user-attachments/assets/9b81c579-685a-4500-b91a-5df613adacd1" />


**Paso 4:** minimizar o contraer la clase **"ToolsForms.cs"**.

<img width="1647" height="857" alt="image" src="https://github.com/user-attachments/assets/ed976bdd-6a2a-4ca3-82fe-0ce81d92db6b" />

**Resultado:** ubircarse al final del codigo del archivo.

<img width="1647" height="857" alt="image" src="https://github.com/user-attachments/assets/02d161bf-4cc1-4757-b19e-7b8581403bea" />

**Paso 5:** codificar una nuevo espacio de nombres, llamado **"ToolsForms"** y agregar un metodo extensivo de validacion para controles **"TextBox"** y **"ComboBox"** a la clase ***"ErrorProvider"*** nativa de .NET

```csharp
namespace ToolsForms
{
    public static class MyExtensions
    {
        public static bool ValidarControl(this ErrorProvider errorProvider, Control pControl, string pMensaje, string pRegex = null)
        {
            if (pControl is TextBox)
            {
                if (pControl.Text == null || pControl.Text.Trim() == string.Empty)
                {
                    errorProvider.SetError(pControl, pMensaje);
                    return false; // dato invalido
                }
                if (pRegex != null && pRegex.Trim() != "")
                {
                    if (!System.Text.RegularExpressions.Regex.IsMatch(pControl.Text, pRegex))
                    {
                        errorProvider.SetError(pControl, "Formato invalido");
                        return false; // formato invalido
                    }
                }
            }
            if (pControl is ComboBox && ((ComboBox)pControl).SelectedIndex <= 0)
            {
                errorProvider.SetError(pControl, pMensaje);
                return false; // dato invalido
            }
            return true; // dato valido
        }
    }
}
```

**Resultado:**

<img width="1580" height="920" alt="image" src="https://github.com/user-attachments/assets/c5fac415-e07c-4bf7-b0a6-7c3b25941ac5" />


**NOTA:** una vez configurada esta seccion de la guia, se puede avanzar en el diseño de los formularios.

## EJEMPLOS

### **AdminEmpleadoFrom.cs**
![image](https://github.com/user-attachments/assets/1184cf67-7df5-4856-90e7-059b4330d9c2)

### **RegistroEmpleadoFrom.cs**
![image](https://github.com/user-attachments/assets/5d227dc7-b75c-4174-89e9-aad63a943571)


