# 🛒 Guitar LA Catalog - React.js
🌐 *[guitar-la.4hmartin.com](https://guitar-la.4hmartin.com/)*
---
## Description

El proyecto simula el comportamiento del carrito de compra de un comercio electrónico donde los productos del catálogo son guitarras eléctricas y el usuario puede agregar, consultar, actualizar y eliminar productos (guitarras) del carrito.

En el desplegable del carrito, el usuario puede ver el listado de guitarras agregadas, actualizar su cantidad y revisar el total a pagar de todos los productos seleccionados así como vaciar el carrito por completo.

## Features

✅ **Refactoring:** El proyecto en su primera versión estaba desarrollado utilizando *custom hook* y para profundizar en la práctica de nuevas formas de manejar el estado, se migra toda la lógica al uso de **`useReducer`**.

✅ Listado de guitarras de la colección:
- **Items:** Listado de guitarras extraidas desde fichero con array de objetos tipados.
- **'Agregar al carrito' Button:** Permite agregar el item al carrito.

✅ Item's Cart:
- **Selected products:** Se muestra el item/producto seleccionado con su precio unitario, dando al usuario la posibilidad de aumentar la cantidad hasta un máximo de 5 items o eliminarlo del carrito.
- **Total:** Calculo del monto total a pagar de los productos del carrito de compra utilizando **`useMemo`**. 
- **'Vaciar carrito' Button:** Permite restablecer el estado del carrito de compra descartando todos los productos.

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