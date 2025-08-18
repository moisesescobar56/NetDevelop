# Programación de funcionalidad BUSCAR

## PARTE 1 - Configurar Referencias y Conexión
**Paso 1:** Seleccionar el formulario y en la ventana de Propiedades dar clic sobre el menú de **Eventos**. 

<img width="1378" height="808" alt="image" src="https://github.com/user-attachments/assets/c605e645-e756-4a18-beaa-26333e48b46d" />

**Paso 2:** En el evento Load dar doble clic en el espacio en blanco para generar el evento Load del 
formulario.

<img width="1378" height="808" alt="image" src="https://github.com/user-attachments/assets/4339b7f9-b6ca-4133-affd-49925f851a61" />


**Resultado:**
<img width="1378" height="808" alt="image" src="https://github.com/user-attachments/assets/67423dca-8a8c-4c72-9c63-426fbbee5b67" />


**Paso 3:** Agregar referencias a librerías en el formulario.
```csharp
//Referencias
using SistemaElParaisal.EN;
using SistemaElParaisal.BL;
```
<img width="1378" height="808" alt="image" src="https://github.com/user-attachments/assets/57459406-271e-45b0-9b2e-e990678e011e" />


**Paso 4:** Agregar crear conexión a la base de datos mediante EmpleadoBL y agregar variable “lista” para cargar los empleados en el DataGridView. 
```csharp
// Conexion a la tabla de Empleados en la DB
EmpleadoBL empleadoBL = new EmpleadoBL();
//Variables
List<Empleado> lista = new List<Empleado>();
```
<img width="1378" height="808" alt="image" src="https://github.com/user-attachments/assets/3737a486-9e9f-4396-9c8f-08f7c7812d08" />


## PARTE 2 - Codificacion de ComboBox (Lista de selección de Cargos)

![image](https://github.com/user-attachments/assets/d620e7af-286c-4dc6-8f00-09791f5658ab)

**Paso 1:** Programar la lógica del método interno "CargarCargos()" para mostrar las cargos en forma de lista de selecciónen el control cargoComboBox.
```csharp
public void CargarCargos()
{
    // Conexion a la tabla de Cargo en la DB
    CargoBL cargoBL = new CargoBL();

    // Inicializar lista 
    List<Cargo> cargos = new List<Cargo>();
    cargos.Add(new Cargo { IdCargo = 0, Nombre = "SELECCIONAR" }); // Opcion por defecto

    // Obtener lista de Cargos de la DB
    cargos.AddRange(cargoBL.Buscar(new Cargo()));
    cargoComboBox.DataSource = cargos;

    // Configurar texto y valor de la lista de seleccion
    cargoComboBox.DisplayMember = "Nombre";
    cargoComboBox.ValueMember = "IdCargo";
}
```
**Resultado:**

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/2732fc34-ac32-47f9-a58b-c2ceacbe182d" />


- **DisplayMember:** es la propiedad del objeto VISIBLE para el usuario, representa el texto que muestra cada elemento. 
-  **ValueMember:** es la propiedad del objeto OCULTA para el usuario, que representa el valor de un elemento de la lista.

**Paso 2:** Codificar el evento Load del formulario. 
```csharp
//Cargar ComboBoxs en el formulario
CargarCargos();
```
**Resultado:**

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/39247449-3e41-41f1-9c67-bc88c816c6ea" />


**Paso 3:** Iniciar la aplicacion.
![image](https://github.com/user-attachments/assets/c44bad4d-30e8-452e-bc00-594b96ab4a43)

**Resultado:**
<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/daa0e257-d648-46a1-b979-c2508ee8d038" />

**NOTA:** recuerdar haber actualizado el archivo Program.cs con el formulario que deseas probar. 

**Paso 4:** Detener la aplicacion.
![image](https://github.com/user-attachments/assets/56e319f1-4420-4a3d-9c4f-e72252c891c3)

## PARTE 3 - Codificacion de Accion BUSCAR

**Paso 1:** Seleccionar el botón "buscarButton" y dar **doble clic** para generar evento click

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/7ac3c0fd-bd43-4548-b893-3155e64f3382" />


**Resultado:**
<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/a91a5498-7cb9-40f5-9328-e76c39b55aaf" />

**Paso 2:** Programar la lógica del método interno CargarLista para cargar mostrar los empleados en forma de tabla en el control **listaDataGridView**.
```csharp
private void CargarLista()
{
    listaDataGridView.DataSource = ""; // Vaciar DataGridView
    listaDataGridView.DataSource = lista; // Agregar objetos de lista
}
```
**Resultado:**
<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/3c8d2d47-66f6-4d8f-93b4-f880da65c13b" />

**Paso 3:** Programar el evento click de **"buscarButton"**, agregando la siguiente lógica. 
```csharp
// Obtener los filtros de busquedas
Empleado empleado = new Empleado();
empleado.Nombre = nombreApellidoTextBox.Text;
empleado.Telefono = telefonoTextBox.Text;
empleado.IdCargo = (byte)cargoComboBox.SelectedValue;

// Ejecutar busqueda
lista = empleadoBL.Buscar(empleado);
CargarLista();
```
**Resultado:**

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/5ff15605-3b4b-4763-b0b1-4bbbafe3886a" />

**Paso 4:** Iniciar la aplicacion.
![image](https://github.com/user-attachments/assets/c44bad4d-30e8-452e-bc00-594b96ab4a43)

**Resultado:** Dar clic en el botón **BUSCAR** y se mostrara la lista de empleados guardados.
<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/8cec15af-99ea-438a-91fa-35881684e5b2" />


#### MEJORAS: No se muestra el nombre del cargo en los empleados filtrados por el cargo **“Administrador”**.
![image](https://github.com/user-attachments/assets/866a03fa-be78-4180-8d80-63c21aee01ec)

***NOTA:*** *Al observar el resultado, la información de empleados se carga correctamente, pero los datos
no se muestran de una forma limpia y comprensible para el usuario, debido a que el usuario 
no puede interpretar cual es el cargo con valor “1”*

**Paso 5:** Detener la aplicacion.
![image](https://github.com/user-attachments/assets/56e319f1-4420-4a3d-9c4f-e72252c891c3)


## REVISAR EL MATERIAL: "TRATAMIENTO DE DATOS"

