# REPASO

## Pasos Generales:

Una línea de pensamiento para cada ejercicio podría ser:
1. **¿Qué componente inicia la acción?**
2. **¿Qué Context/Provider interviene?**
3. **¿Qué servicio o función se necesita?**
4. **¿Qué ocurre en Firebase/Firestore?**
5. **¿Cómo vuelve el resultado a la UI?**

## 🛒 Carrito + Reducer

1. **Agregar un producto al carrito**
    - ¿Desde dónde se dispara la acción?
    - ¿Qué `action` debería enviarse?
      { type: "AddToCart", payload: producto }
    - ¿Qué hace el reducer?
    - ¿Cómo llega el nuevo estado a la interfaz?

2. **Agregar nuevamente un producto que ya está en el carrito**
    - ¿Qué debería detectar el reducer?
    - ¿Se agrega otro elemento o aumenta `quantity`?
    - ¿Qué estado debería devolver?

3. **Eliminar un producto del carrito**
    - ¿Qué información necesita la acción?
    - ¿Qué responsabilidad tiene el reducer?
    - ¿Qué componentes deberían actualizarse?

4. **Calcular el total del carrito**
    - ¿Dónde conviene obtener este dato?
    - ¿Es estado real o estado derivado?
    - ¿Qué ocurre cuando cambia la cantidad de un producto?

5. **Vaciar el carrito después de confirmar una orden**
    - ¿En qué momento debería vaciarse?
    - ¿Qué pasa si la creación de la orden falla?
    - ¿Qué acciones/contextos participan?

## 👤 Auth + Firebase

6. **Un usuario intenta realizar el checkout sin estar autenticado**
    - ¿Dónde detectarías la situación?
    - ¿Qué contexto proporciona esa información?
    - ¿Qué debería ocurrir con el carrito?

7. **Registro de un nuevo usuario**
    - ¿Qué ocurre primero: Firebase Authentication o Firestore?
    - ¿Qué información se guarda en cada lugar?
    - ¿Cómo relacionamos el usuario autenticado con su documento en Firestore?

8. **Inicio de sesión y recuperación de la sesión**
    - ¿Cómo sabe React que el usuario ya está autenticado?
    - ¿Qué ocurre al recargar la página?
    - ¿Qué responsabilidad tiene `AuthProvider`?

9. **Cerrar sesión**
    - ¿Qué debería cambiar en Firebase?
    - ¿Qué debería cambiar en el estado de React?
    - ¿Qué partes de la aplicación deberían reaccionar?

## 📦 Productos + Firestore

10. **Mostrar el catálogo**
	- ¿De dónde vienen los productos?
	- ¿Qué servicio consulta Firestore?
	- ¿Dónde se almacena el resultado?
	- ¿Cómo llega finalmente al componente?

11. **Un producto modifica su stock**
	- ¿Quién puede realizar esa modificación?
	- ¿Dónde se realiza realmente la actualización?
	- ¿Qué papel cumplen las reglas de Firestore?

12. **Un usuario intenta modificar directamente el precio de un producto**
	- ¿Dónde debería bloquearse?
	- ¿Puede confiarse solamente en una validación del frontend?
	- ¿Qué debería establecer Firestore?

### 🔎 Filtros y catálogo

13. **Filtrar productos por categoría**
	- ¿Dónde debe vivir el estado del filtro?
	- ¿Se modifica la fuente original de productos?
	- ¿Cómo obtenemos la lista filtrada?

14. **Buscar productos por nombre**
	- ¿Qué ocurre cuando el usuario escribe?
	- ¿Qué datos necesitamos?
	- ¿El filtro se realiza en frontend o consultando Firestore?

15. **Combinar búsqueda + categoría + ordenamiento**
	- ¿En qué orden aplicarías cada operación?
	- ¿Qué estado necesitas mantener?
	- ¿Qué información debería permanecer sin modificar?

## Ejercicios Tipo

### 🟡 1. Persistencia del Carrito/Favoritos 💾

- Actualmente, si el usuario recarga la página, pierde el carrito. Queremos conservarlo.

Definir:
- ¿Dónde almacenarían la información?
- ¿Cuándo guardarían el carrito?
- ¿Cuándo lo recuperarían?
- ¿Qué ocurre durante la carga inicial?
- ¿Qué pasa si el usuario cierra sesión?

Preguntas:
- ¿Guardaríamos el Snapshot del Producto?

---

### 🟢 2. Reviews de productos ⭐

**Nueva funcionalidad:**  
- Los usuarios autenticados pueden dejar una valoración de 1 a 5 estrellas y un comentario sobre un producto. Las reviews deben mostrarse en el detalle del producto.

Definir:
1. ¿Dónde se almacenan las reviews?
2. ¿Cómo se relacionan con el producto y el usuario?
3. ¿Qué información debería tener una review?
4. ¿Qué Context/Provider necesitamos?
5. ¿Qué operaciones contra Firestore necesitamos?
6. ¿Quién puede crear una review?
7. ¿Quién puede modificar/eliminar una review?
8. ¿Qué reglas de Firestore necesitamos?
9. ¿Puede un usuario dejar más de una review?
10. ¿Cómo calculamos el promedio de estrellas?
11. ¿Qué ocurre si el producto no tiene reviews?

Preguntas:
- ¿Qué información guardarías en la review y cuál consultarías desde el usuario/producto en lugar de duplicarla?
