
# Programación de funcionalidad ELIMINAR

## PARTE 1 - Programación de Accion ELIMINAR
**Paso 1:** Ir al **Explorador de soluciones** y dar doble clic sobre el archivo **“AdminEmpleadoForm.cs”**. 

<img width="1378" height="881" alt="image" src="https://github.com/user-attachments/assets/70c8db75-bda9-46a4-8743-8efc9e9afbf5" />

**Paso 2:** Dar doble clic sobre el botón **"eliminarButton"**, para generar el **evento click**. 

<img width="1598" height="913" alt="image" src="https://github.com/user-attachments/assets/bf7f163b-5726-440b-93c3-3d447ad6a10d" />

**Resultado:**
<img width="1239" height="718" alt="image" src="https://github.com/user-attachments/assets/f910d7da-4b46-4857-8602-6eeb64486fe3" />


**Paso 3:** Agregar lógica del botón **ELIMINAR**, en el evento **eliminarButton_Click**. La siguiente lógica es para validar que se haya seleccionado un registro antes de eliminarlo y confirmar si **“¿Desea eliminar el registro seleccionado?”**.
```csharp
// Obtener llave primaria del registro seleccionado
short idTabla = (short)ToolsForms.ObtenerIdGrid(listaDataGridView);
if (idTabla > 0)
{
    if (ToolsForms.MessageBoxConfirmar() == DialogResult.Yes)
    {

    }
}
else
{
    MessageBox.Show("Primero debe seleccionar el registro que desea eliminar", "Info", MessageBoxButtons.OK, MessageBoxIcon.Information);
}
```
**Resultado:**
<img width="1616" height="902" alt="image" src="https://github.com/user-attachments/assets/42a162ce-89ab-4063-a124-9e960d9f08bf" />

**Paso 4:** Agregar la lógica para eliminar el registro seleccionado. 
```csharp
//Crear instancia del Empleado a eliminar
Empleado empleado = new Empleado() { IdEmpleado = idTabla };
//Ejecutar metodo para eliminar el registro seleccionado
if (empleadoBL.Eliminar(empleado) > 0)
{
    MessageBox.Show("Registro eliminado exitosamente", "Info", MessageBoxButtons.OK, MessageBoxIcon.Information);
    // Actualizar lista simulando click en boton de buscar
    buscarButton.PerformClick();
}
else
{
    MessageBox.Show("Ocurrio un error, por favor intente de nuevo", "Error", MessageBoxButtons.OK, MessageBoxIcon.Error);
}
```
**Resultado:**
<img width="1616" height="1040" alt="image" src="https://github.com/user-attachments/assets/78f1435f-3e57-442d-8a2b-30169077a262" />

**Paso 5:** Iniciar la aplicacion.
![image](https://github.com/user-attachments/assets/c44bad4d-30e8-452e-bc00-594b96ab4a43)

**Resultado:** Dar clic en el botón **BUSCAR** 
![image](https://github.com/user-attachments/assets/38b5bd74-039e-4d82-b83b-4a7cce0c1773)

**Paso 6:** Seleccionar un registro de la lista de empleado y dar clic en el boton **"ELIMINAR"**
![image](https://github.com/user-attachments/assets/03386867-9917-4c8b-9bfb-bd62447053bc)

**Paso 7:** Seleccionar la opción “SI” en la ventana de confirmacion. 
![image](https://github.com/user-attachments/assets/f9355b05-9d68-4c90-a5b2-20e9959e85f6)

**Resultado:** El registro se ha eliminado. Dar clic en Aceptar.
![image](https://github.com/user-attachments/assets/ef494e75-e893-4112-94ef-5b2474cdb32a)

**Paso 8:** Detener la aplicacion.
![image](https://github.com/user-attachments/assets/56e319f1-4420-4a3d-9c4f-e72252c891c3)
