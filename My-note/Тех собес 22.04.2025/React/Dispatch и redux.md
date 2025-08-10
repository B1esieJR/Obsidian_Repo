
## **Вывод:**

- **Reducer** — это функция, которая обрабатывает действия и возвращает новое состояние.
    
- **Dispatch** — это механизм отправки действий в редюсер для обновления состояния.
    
- Вместе они позволяют управлять состоянием предсказуемо и централизованно.
    

Если используется **Redux**, то `dispatch` является методом хранилища (`store.dispatch`).  
В **React** с `useReducer` — это возвращаемая функция из хука.

### **Структура редюсера:**

function reducer(state, action) {
  switch (action.type) {
    case 'ACTION_TYPE_1':
      return { ...state, key: action.payload };
    case 'ACTION_TYPE_2':
      return { ...state, anotherKey: state.anotherKey + 1 };
    default:
      return state; // Возвращает текущее состояние, если action не распознан
  }
}
### **Пример работы:**
const initialState = { count: 0 };

function counterReducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

const newState = counterReducer(initialState, { type: 'INCREMENT' });
console.log(newState); // { count: 1 }

Восприятие и понимание когда использования useState() и useReducer().
useState лучше использовать в функциональном компоненте для простого хранения состояний. useReducer это React аналог Redux, он нужен для сложного обращения и контролирования состояния, к тому же он не привязывает нас к иерархии компонентов, мы можем обратиться из любого компонента к нашему "store" и условно запросить по определенному action необходимые нам данные.
