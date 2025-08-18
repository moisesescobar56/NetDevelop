# Programación de funcionalidad GUARDAR

## PARTE 1 - Programación del boton NUEVO

**Paso 1:** Abrir el formulario "AdminEmpleadoForm.cs".

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/70c8db75-bda9-46a4-8743-8efc9e9afbf5" />


**Paso 2:** dar doble clic sobre el boton **"NUEVO"** para generar el “Evento Click”

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/3157b480-51e2-470e-91c6-ebcb9d25f585" />

**Resultado:**

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/ec01ea54-1046-40fa-a844-d1ef0868158b" />

**Paso 3:** Programar la lógica para abrir el formulario **“RegistroEmpleadoForm.cs”**
```csharp
// Abrir formulario para registrar un nuevo cliente 
RegistroEmpleadoForm frmRegistro = new RegistroEmpleadoForm();
frmRegistro.ShowDialog();
```
**Resultado:**

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/b42880bf-7de7-41e7-86e5-a7725df2cbd5" />

## PARTE 2 - Codificacion de ComboBox y Load
**Paso 1:** Abrir el formulario **"RegistroEmpleadoForm.cs"**.

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/01b66ff3-b814-42ef-9bf2-114ccd13c67c" />

**Paso 2:** Agregar un ErrorProvider al formulario, arrastrándolo y dejándolo caer en el Diseño del formulario “RegistroEmpleadoForm.cs” 

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/00e01158-cb48-4ea3-a209-486bc1d98eab" />

**Resultado:**

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/6df3ff12-695f-4fa6-9021-09cd3be62e1e" />


**Paso 3:** Cambiar el nombre del “errorProvider1” a **“errorProvider”** en la ventana de **Propiedades**.

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/8ddd9a46-1cb2-4853-be79-2a03cc3f4241" />

**Paso 4:** Seleccionar el formulario “RegistroEmpleadoForm.cs” en el diseño y en la ventana de propiedades, seleccionar la opción **Eventos**.

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/57515e00-30b0-4257-b3a6-c757cf0f624e" />

**Paso 5:** Generar el evento Load del formulario, dando doble click en la opción **Load**. 

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/cbb86001-7f84-4f4e-a9ed-550f4b2289c3" />

**Resultado**

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/46b375f8-0078-4447-b5b3-4efcc468cc64" />

**Paso 6:** Agregar referencias a bibliotecas en el formulario.
```csharp
//Referencias del proyecto
using SistemaElParaisal.EN;
using SistemaElParaisal.BL;
// Extension de metodos
using ToolsForms;
```
**Resultado:**

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/b0a05caf-6890-4189-9dbf-3fa94ba92fe0" />

**Paso 7:** Agregar conexión a la base de datos mediante instancia a la clase **EmpleadoBL**. 
```csharp
// Conexion a la tabla de Empleados en la DB
EmpleadoBL empleadoBL = new EmpleadoBL();
```

**Resultado:**

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/c57e0f7a-cbdb-4efc-a158-ce7ada5a98be" />


**Paso 8:** Agregar a la lógica la variable “idEmpleado” para almacenar la llave primaria de cualquier registro de "Empleado" que se desee modificar. Debe **asignar el mismo tipo de dato** a como en esta en la **EN**.
```csharp
// Variables
public short idEmpleado = 0; // variable del mismo tipo que la PK
```
<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/e7f5cfaa-aefc-4d94-8539-149b5788f6d0" />

**Paso 9:** Programar la lógica del método interno **"CargarCargos()"** que nos permitirá mostrar en forma de lista de selección las cargos en un formulario.
```csharp
public void CargarCargos()
{
    // Conexion a la tabla de Cargo en la DB
    CargoBL cargoBL = new CargoBL();

    // Inicializar lista 
    List<Cargo> cargos = new List<Cargo>();
    cargos.Add(new Cargo { IdCargo = 0, Nombre = "SELECCIONAR" });

    // Obtener lista de Cargos de la DB
    cargos.AddRange(cargoBL.Buscar(new Cargo()));
    cargoComboBox.DataSource = cargos;

    // Configurar texto y valor de la lista de seleccion
    cargoComboBox.DisplayMember = "Nombre";
    cargoComboBox.ValueMember = "IdCargo";
}
```

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/ca895518-bf73-44f5-a979-f2e212d6b947" />

**Paso 10:** Codificar la lógica del evento Load.
```csharp
//Cargar ComboBoxs en el formulario
CargarCargos();

if (idEmpleado > 0)
{
    // Si "idEmpleado" es mayor que cero se esta modificando un empleado
    Empleado empleado = empleadoBL.ObtenerPorId(idEmpleado); // buscar por id al empleado
    
    // Cargar datos del empleado en los controles del formulario
    nombreTextBox.Text = empleado.Nombre;
    apellidoTextBox.Text = empleado.Apellido;
    telefonoTextBox.Text = empleado.Telefono;
    cargoComboBox.SelectedValue = empleado.IdCargo; // seleccionar cargo segun empleado
    claveTextBox.Enabled = false; // deshabilidad TextBox de clave

    this.Text = "Editar Empleado"; // titulo del formulario
}
```
<img width="1378" height="889" alt="image" src="https://github.com/user-attachments/assets/c7db9c6c-33a3-46be-89e4-7f59f0c89e17" />

**Paso 11:** Iniciar la aplicacion.
![image](https://github.com/user-attachments/assets/c44bad4d-30e8-452e-bc00-594b96ab4a43)

**Paso 12:** Dar clic en **NUEVO**.
<img width="1378" height="889" alt="image" src="https://github.com/user-attachments/assets/e7e0f642-6977-45ba-92cc-b3d1c4eeae61" />

**Resultado:** Verificar que se cargue la lista de desplegable **Cargos**.
<img width="1378" height="889" alt="image" src="https://github.com/user-attachments/assets/de5e3359-6a53-4b09-9590-320b5ee3b373" />

**Paso 12:** Detener la aplicacion.
![image](https://github.com/user-attachments/assets/56e319f1-4420-4a3d-9c4f-e72252c891c3)

## PARTE 3 - Programación de Accion GUARDAR y CANCELAR

**Paso 1:** Dar doble clic sobre el botón **"cancelarButton"**, para generar el evento **click**. 

<img width="1378" height="730" alt="image" src="https://github.com/user-attachments/assets/3fd1bedc-5e4b-4094-80f3-9d70270fb8ea" />

**Resultado:**
<img width="1378" height="847" alt="image" src="https://github.com/user-attachments/assets/59e6cc25-8af0-4d95-9ee2-f8632c8d40e2" />

**Paso 2:** Codificar la lógica del botón **CANCELAR**. 
```csharp
// this = Formulario actual y Close() = evento para cerrar un formulario
this.Close();
```

<img width="1378" height="847" alt="image" src="https://github.com/user-attachments/assets/c6693f93-ab6f-4389-9e0a-7ad210709d5f" />

**Paso 3:** Dar doble clic sobre el botón **"guardarButton"**, para generar el evento click.

<img width="1378" height="847" alt="image" src="https://github.com/user-attachments/assets/d7624fdc-581e-4849-9b2a-a01b2e3b1c33" />

**Resultado:**
<img width="1378" height="847" alt="image" src="https://github.com/user-attachments/assets/3a9d8586-0c93-4340-bcad-2feaadcb5498" />

**Paso 4:** Programar método interno **"ValidarControles"** para validar que el usuario complete los campos obligatorios del formulario. 
```csharp
private bool ValidarControles()
{
    errorProvider.Clear(); // Limpiar errores
    bool datosValidos = true; // Si el valor es True los datos son correctos
    datosValidos = errorProvider.ValidarControl(nombreTextBox, "Campo obligatorio");
    datosValidos = errorProvider.ValidarControl(apellidoTextBox, "Campo obligatorio");
    datosValidos = errorProvider.ValidarControl(telefonoTextBox, "Campo obligatorio", @"^[0-9]{8}$");
    datosValidos = errorProvider.ValidarControl(cargoComboBox, "Campo obligatorio");
    
    if (idEmpleado == 0) // id es cero, no se esta editando
    {
        // Agregar aqui validaciones necesarias al guardar un nuevo registro
        datosValidos = errorProvider.ValidarControl(claveTextBox, "Campo obligatorio", @"^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$");
    }
return datosValidos;
}
```

<img width="1674" height="1000" alt="image" src="https://github.com/user-attachments/assets/d701506d-7d6e-4585-8c56-c9cb33d1988b" />

### IMPLEMENTACION DE EXTENSION DE ERROR PROVIDER


Este metodo recibe 2 parametros obligatorios (**pControl**, **pMensaje**) y 1 opcional ([**pRegex** = null]).
1. **Control pControl:** puede ser cualquier control de tipo **TextBox** o **ComboBox**.
2. **string pMensaje:** define el mensaje a mostrar en el control si el valor del control no es valido.
3. **string pRegex:** define la [Regular Expression](https://www.ibm.com/docs/es/i/7.5?topic=expressions-regular), funciona comparando el valor del control versus el REGEX(Regular Expression), si coincide el dato es valido.

![image](https://github.com/user-attachments/assets/b3c3a4f4-4b78-4651-846d-37ea3b497e09)

**NOTA:** REGEX es util para validar formatos como numero de telefono, dui o ID, fechas, reglas para contraseñas, etc.
- Regex que valida numero de telefono de 8 digitos: ^[0-9]{8}$
- Regex que valida contraseña que contengas mayusculas, minusculas y numeros: ^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$
- Los Regex se pueden solicitar a ***ChatGPT, Copilot o cualquier IA***.

## CONTINUACION 
**Paso 5:** Codificar la lógica del botón **GUARDAR**. Agregar un **[Try/Catch](https://learn.microsoft.com/es-es/dotnet/csharp/fundamentals/exceptions/exception-handling)** para gestionar los errores de ejecución al guardar un registro. 
```csharp
int resultado = 0; // resultado del comando en la DB
try
{

}
catch (Exception ex)
{
    MessageBox.Show(ex.Message, "Error", MessageBoxButtons.OK, MessageBoxIcon.Error);
}
```
<img width="1674" height="1000" alt="image" src="https://github.com/user-attachments/assets/349d5eee-7b72-432f-be21-9149ee6074fd" />

**Paso 6:** Agregar a la lógica un if para la validación de campos obligatorios. 
```csharp
if (ValidarControles() == true)
{

}
```
<img width="1674" height="1000" alt="image" src="https://github.com/user-attachments/assets/39e9c89a-ad7f-4500-845f-ff9b7582f8f8" />

**Paso 7:** Agregar lógica para obtener los valores en los controles del formulario.
```csharp
// Capturar datos del formulario
Empleado empleado = new Empleado(); // instancia de empleado
empleado.Nombre = nombreTextBox.Text;
empleado.Apellido = apellidoTextBox.Text;
empleado.Telefono = telefonoTextBox.Text;
empleado.Clave = claveTextBox.Text;
empleado.IdCargo = (byte)cargoComboBox.SelectedValue;
```
<img width="1674" height="1000" alt="image" src="https://github.com/user-attachments/assets/eb58faf8-ed8b-41cd-8dbe-75f923805ef3" />

**IMPORTANTE:** la conversion al obtener un valor del comboBox debe ser segun el tipo de dato de la propiedad en la clase.

**Paso 8:** Agregar lógica para GUARDAR o MODIFICAR un registro de empleado, verificando si se registro o no.
```csharp
if (idEmpleado == 0)
{                        
    resultado = empleadoBL.Guardar(empleado); //Se esta guardando un nuevo empleado
}
else
{                        
    empleado.IdEmpleado = idEmpleado; 
    resultado = empleadoBL.Modificar(empleado); //Se esta modificando un empleado existente
}
// Verficiacion del resultado en la base de datos
if (resultado > 0)
{
    MessageBox.Show("Registro guardado exitosamente", "Info", MessageBoxButtons.OK, MessageBoxIcon.Information);
    this.Close();
}
else
{
    MessageBox.Show("Ocurrio un error, por favor intentelo de nuevo", "Error", MessageBoxButtons.OK, MessageBoxIcon.Error);
}
```

<img width="1674" height="1000" alt="image" src="https://github.com/user-attachments/assets/8f16b808-3b97-4f5e-a141-9d47d1ff9a45" />

**Metodo completo:**
```csharp
            int resultado = 0; // resultado del comando en la DB
            try
            {
                if (ValidarControles() == true)
                {
                    // Capturar datos del formulario
                    Empleado empleado = new Empleado(); // instancia de empleado
                    empleado.Nombre = nombreTextBox.Text;
                    empleado.Apellido = apellidoTextBox.Text;
                    empleado.Telefono = telefonoTextBox.Text;
                    empleado.Clave = claveTextBox.Text;
                    empleado.IdCargo = (byte)cargoComboBox.SelectedValue;

                    if (idEmpleado == 0)
                    {
                        resultado = empleadoBL.Guardar(empleado); //Se esta guardando un nuevo empleado
                    }
                    else
                    {
                        empleado.IdEmpleado = idEmpleado;
                        resultado = empleadoBL.Modificar(empleado); //Se esta modificando un empleado existente
                    }
                    // Verficiacion del resultado en la base de datos
                    if (resultado > 0)
                    {
                        MessageBox.Show("Registro guardado exitosamente", "Info", MessageBoxButtons.OK, MessageBoxIcon.Information);
                        this.Close();
                    }
                    else
                    {
                        MessageBox.Show("Ocurrio un error, por favor intentelo de nuevo", "Error", MessageBoxButtons.OK, MessageBoxIcon.Error);
                    }
                }
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message, "Error", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
```

**Paso 9:** Iniciar la aplicacion.
![image](https://github.com/user-attachments/assets/c44bad4d-30e8-452e-bc00-594b96ab4a43)

**Paso 10:** Dar clic en **NUEVO**.

<img width="1378" height="889" alt="image" src="https://github.com/user-attachments/assets/e7e0f642-6977-45ba-92cc-b3d1c4eeae61" />

**Paso 11:** Completar los datos del formulario y dar clic en el boton **"GUARDAR"**

<img width="1674" height="1000" alt="image" src="https://github.com/user-attachments/assets/6a6528b4-f017-4794-a0a8-775b252ccf19" />

**Paso 12:** Dar clic en **Aceptar** y luego dar clic en el boton **BUSCAR**.

<img width="1674" height="1000" alt="image" src="https://github.com/user-attachments/assets/c786b1ef-dd62-45c1-bb08-ce20b6d55fa3" />

**Resultado:**

<img width="1674" height="1000" alt="image" src="https://github.com/user-attachments/assets/8145879d-56d6-40e0-8f7f-9f0c67e23341" />


**Paso 13:** Detener la aplicacion.
![image](https://github.com/user-attachments/assets/56e319f1-4420-4a3d-9c4f-e72252c891c3)


## CORRECCIONES
En el procedimiento almacenado **"SP_ModificarEmpleado"** se actualizo, debido a que al momento de editar los registros, no se actualizara el campo ***"Clave"***, por lo cual solo se modifico para que se actualice con el mismo valor.

![image](https://github.com/user-attachments/assets/15f55e0b-6f1a-4169-aff8-bc728a2add00)

```sql
USE ElParaisalDB
GO
-- Modificar Empleado
ALTER PROCEDURE SP_ModificarEmpleado
    @IdEmpleado SMALLINT,
    @IdCargo TINYINT,
    @Nombre VARCHAR(50),
    @Apellido VARCHAR(50),
    @Telefono NCHAR(8),
    @Clave VARCHAR(250)
AS
BEGIN
    IF EXISTS (SELECT * FROM Empleado WHERE Telefono = @Telefono AND IdEmpleado != @IdEmpleado)
		BEGIN
			PRINT 'Empleado ya registrado';
		END
    ELSE
		BEGIN
			UPDATE Empleado
			SET IdCargo = @IdCargo, Nombre = @Nombre, Apellido = @Apellido, Telefono = @Telefono, Clave = Clave
			WHERE IdEmpleado = @IdEmpleado;
			PRINT 'Empleado modificado correctamente';
		END
END;
GO
```

## Archivo **RegistroEmpleadoForm.cs**
```csharp
//Referencias del proyecto
using SistemaElParaisal.EN;
using SistemaElParaisal.BL;
// Extension de metodos
using ToolsForms;

namespace SistemaElParaisal.UI.WinForms
{
    public partial class RegistroEmpleadoForm : Form
    {
        // Conexion a la tabla de Empleados en la DB
        EmpleadoBL empleadoBL = new EmpleadoBL();

        // Variables
        public short idEmpleado = 0; // variable del mismo tipo que la PK

        public RegistroEmpleadoForm()
        {
            InitializeComponent();
        }
        public void CargarCargos()
        {
            // Conexion a la tabla de Cargo en la DB
            CargoBL cargoBL = new CargoBL();

            // Inicializar lista 
            List<Cargo> cargos = new List<Cargo>();
            cargos.Add(new Cargo { IdCargo = 0, Nombre = "SELECCIONAR" });

            // Obtener lista de Cargos de la DB
            cargos.AddRange(cargoBL.Buscar(new Cargo()));
            cargoComboBox.DataSource = cargos;

            // Configurar texto y valor de la lista de seleccion
            cargoComboBox.DisplayMember = "Nombre";
            cargoComboBox.ValueMember = "IdCargo";
        }
        private void RegistroEmpleadoForm_Load(object sender, EventArgs e)
        {
            //Cargar ComboBoxs en el formulario
            CargarCargos();

            if (idEmpleado > 0)
            {
                // Si "idEmpleado" es mayor que cero se esta modificando un empleado
                Empleado empleado = empleadoBL.ObtenerPorId(idEmpleado); // buscar por id al empleado

                // Cargar datos del empleado en los controles del formulario
                nombreTextBox.Text = empleado.Nombre;
                apellidoTextBox.Text = empleado.Apellido;
                telefonoTextBox.Text = empleado.Telefono;
                cargoComboBox.SelectedValue = empleado.IdCargo; // seleccionar cargo segun empleado
                claveTextBox.Enabled = false; // deshabilidad TextBox de clave

                this.Text = "Editar Empleado"; // titulo del formulario
            }
        }

        private void cancelarButton_Click(object sender, EventArgs e)
        {
            // this = Formulario actual y Close() = evento para cerrar un formulario
            this.Close();
        }

        private bool ValidarControles()
        {
            errorProvider.Clear(); // Limpiar errores
            bool datosValidos = true; // Si el valor es True los datos son correctos
            datosValidos = errorProvider.ValidarControl(nombreTextBox, "Campo obligatorio");
            datosValidos = errorProvider.ValidarControl(apellidoTextBox, "Campo obligatorio");
            datosValidos = errorProvider.ValidarControl(telefonoTextBox, "Campo obligatorio", @"^[0-9]{8}$");
            datosValidos = errorProvider.ValidarControl(cargoComboBox, "Campo obligatorio");

            if (idEmpleado == 0) // id es cero, no se esta editando
            {
                // Agregar aqui validaciones necesarias al guardar un nuevo registro
                datosValidos = errorProvider.ValidarControl(claveTextBox, "Campo obligatorio", @"^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$");
            }
            return datosValidos;
        }
        private void guardarButton_Click(object sender, EventArgs e)
        {
            int resultado = 0; // resultado del comando en la DB
            try
            {
                if (ValidarControles() == true)
                {
                    // Capturar datos del formulario
                    Empleado empleado = new Empleado(); // instancia de empleado
                    empleado.Nombre = nombreTextBox.Text;
                    empleado.Apellido = apellidoTextBox.Text;
                    empleado.Telefono = telefonoTextBox.Text;
                    empleado.Clave = claveTextBox.Text;
                    empleado.IdCargo = (byte)cargoComboBox.SelectedValue;

                    if (idEmpleado == 0)
                    {
                        resultado = empleadoBL.Guardar(empleado); //Se esta guardando un nuevo empleado
                    }
                    else
                    {
                        empleado.IdEmpleado = idEmpleado;
                        resultado = empleadoBL.Modificar(empleado); //Se esta modificando un empleado existente
                    }
                    // Verficiacion del resultado en la base de datos
                    if (resultado > 0)
                    {
                        MessageBox.Show("Registro guardado exitosamente", "Info", MessageBoxButtons.OK, MessageBoxIcon.Information);
                        this.Close();
                    }
                    else
                    {
                        MessageBox.Show("Ocurrio un error, por favor intentelo de nuevo", "Error", MessageBoxButtons.OK, MessageBoxIcon.Error);
                    }
                }
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message, "Error", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
        }
    }
}
```
