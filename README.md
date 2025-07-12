# 🛒 Guitar LA Catalog - React.js
🌐 *[guitar-la.4hmartin.com](https://guitar-la.4hmartin.com/)*
---
## Description

The project simulates the behaviour of an e-commerce shopping cart where the products in the catalogue are electric guitars and the user can add, consult, update and delete products (guitars) from the cart.

In the drop-down menu of the shopping cart, the user can see the list of added guitars, update their quantity and check the toal amount to be paid for all the selected products as well as empty the cart completely.

## Features

✅ **Refactoring:** The project in its first version was developed using *custom hook* and to deepen the practice of new ways of handling the state, all the logic is migrated to the use of **`useReducer`**.

✅ List of guitars in the collection:
- **Items:** List of guitars extracted from file with array of typed objects.
- **'Agregar al carrito' Button:** Allows you to add the item to the cart.

✅ Item's Cart:
- **Selected products:** The selected item/product is displayed with its unit price, giving the user the possibility to increase the quantity up to a maximum of 5 items or to remove it from the cart.
- **Total:** Calculation to the total amount to be paid for the products in the shopping cart using **`useMemo`**. 
- **'Vaciar carrito' Button:** Allows you to reset the shopping cart status by discarding all products.

✅ **Data persistence** using **Local Storage**, ensuring information is not lost when the page is reloaded.

## Technologies

- ⚛️ **React.js** + **Typescript**
- 🛠️ **useReducer** for advanced state management
- 💽 **useMemo** for optimizing performance by memoizing calculations
- 💾 **Local Storage** for client-side data persistence

## 🛠️ React Hooks Used

### useReducer

`useReducer` is a React Hook that provides an alternative to `useState` for managing more complex state logic. It is particularly useful when:

- The new state depends on the previous state.
- The state consists of multiple sub-values.
- Complex state transitions or conditional logic are required.

In this project, `useReducer` is used to handle all logic related to cart management.

**Reducer Location:**  
`cart-reducer.ts`

Since this project does not implement global state management, the reducer is imported into `App.tsx` and passed down to child components via props. The `useReducer` hook initializes and provides the state and dispatch functions.

**Defined Actions:**

```ts
export type CartActions =
    { type: 'add-to-cart', payload: { item: Guitar }} |
    { type: 'remove-from-cart', payload: { id: Guitar['id'] }} |
    { type: 'decrease-quantity', payload: { id: Guitar['id'] }} |
    { type: 'increase-quantity', payload: { id: Guitar['id'] }} |
    { type: 'clear-cart' }
```

---
### useMemo

`useMemo` is a performance optimization hook that memoizes the result of an expensive calculation. The memoized value is recomputed only when one of its dependencies changes.

In this project, `useMemo` is used to efficiently calculate the total to pay.

**Location example:**  
`Header.tsx`

**Example:**

```ts
    // State Derivado
    const isEmpty = useMemo( () => cart.length === 0, [cart])
    const cartTotal = useMemo( () => cart.reduce( (total, item ) => total + (item.quantity * item.price), 0), [cart] )
```

## 🚀 Key Learning Outcomes

- Practical migration from *custom hook (useCart.ts)* to **`useReducer`** hook to manage complex state logic.
- Handling dynamic forms and state updates without relying on external state management libraries.
- Type-safe management of form events and actions using **TypeScript**.
- Application of `useMemo` to optimize performance in real-time calculations.

---
*ESPAÑOL*

# 🛒 Guitar LA Catalog - React.js  
🌐 *[guitar-la.4hmartin.com](https://guitar-la.4hmartin.com/)*  
---  

## Descripción

Este proyecto simula el comportamiento de un carrito de compras de un e-commerce, donde los productos del catálogo son guitarras eléctricas y el usuario puede **agregar, consultar, actualizar y eliminar** productos (guitarras) del carrito.

En el menú desplegable del carrito de compras, el usuario puede ver la lista de guitarras añadidas, actualizar su cantidad, revisar el **total a pagar** por todos los productos seleccionados, así como vaciar completamente el carrito.

---

## Funcionalidades

✅ **Refactorización:** La primera versión del proyecto fue desarrollada utilizando un *custom hook* y, con el objetivo de profundizar en nuevas formas de manejo del estado, toda la lógica fue migrada al uso de **`useReducer`**.

✅ Lista de guitarras del catálogo:
- **Elementos:** Lista de guitarras extraída desde un archivo con un arreglo de objetos tipados.
- **Botón 'Agregar al carrito':** Permite añadir el producto al carrito.

✅ Carrito de compras:
- **Productos seleccionados:** El producto añadido se muestra con su precio unitario, permitiendo al usuario incrementar la cantidad hasta un máximo de 5 unidades o eliminarlo del carrito.
- **Total:** Cálculo del total a pagar por los productos en el carrito utilizando **`useMemo`**.
- **Botón 'Vaciar carrito':** Permite reiniciar el estado del carrito eliminando todos los productos.

✅ **Persistencia de datos** usando **Local Storage**, garantizando que la información no se pierda al recargar la página.

---

## Tecnologías

- ⚛️ **React.js** + **TypeScript**
- 🛠️ **useReducer** para manejo avanzado del estado
- 💽 **useMemo** para optimización de rendimiento mediante memorización de cálculos
- 💾 **Local Storage** para persistencia de datos en el cliente

---

## 🛠️ Hooks de React utilizados

### useReducer

`useReducer` es un hook de React que ofrece una alternativa a `useState` para manejar lógica de estado más compleja. Es especialmente útil cuando:

- El nuevo estado depende del estado anterior.
- El estado contiene múltiples sub-valores.
- Se requiere lógica de transición de estado compleja o condicional.

En este proyecto, `useReducer` se utiliza para manejar toda la lógica relacionada con la gestión del carrito.

**Ubicación del reducer:**  
`cart-reducer.ts`

Como este proyecto no implementa gestión de estado global, el reducer se importa en `App.tsx` y se pasa a los componentes hijos mediante props. El hook `useReducer` inicializa y proporciona el estado y la función `dispatch`.

**Acciones definidas:**

```ts
export type CartActions =
    { type: 'add-to-cart', payload: { item: Guitar }} |
    { type: 'remove-from-cart', payload: { id: Guitar['id'] }} |
    { type: 'decrease-quantity', payload: { id: Guitar['id'] }} |
    { type: 'increase-quantity', payload: { id: Guitar['id'] }} |
    { type: 'clear-cart' }
```

---

### useMemo

`useMemo` es un hook de optimización de rendimiento que **memoriza el resultado de un cálculo costoso**. El valor memorizado solo se recalcula si alguna de sus dependencias cambia.

En este proyecto, `useMemo` se utiliza para calcular de manera eficiente el **total a pagar**.

**Ejemplo de ubicación:**  
`Header.tsx`

**Ejemplo:**

```ts
// Estado derivado
const isEmpty = useMemo(() => cart.length === 0, [cart])
const cartTotal = useMemo(() => cart.reduce((total, item) => total + (item.quantity * item.price), 0), [cart])
```

---

## 🚀 Principales aprendizajes

- Migración práctica desde un *custom hook (useCart.ts)* al hook **`useReducer`** para manejar lógica compleja de estado.
- Manejo de formularios dinámicos y actualizaciones de estado sin depender de bibliotecas externas de gestión de estado.
- Gestión de eventos y acciones de formularios de forma **type-safe** usando **TypeScript**.
- Aplicación de `useMemo` para optimizar el rendimiento en cálculos en tiempo real.