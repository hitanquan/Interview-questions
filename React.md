##### 1.什么是 Hooks，有啥作用？举例说明。

Hooks 是 React 中的一种**特殊函数**（相比于我们自己写的函数，Hooks有自己特别的作用，是 React 开发者专门设计的），它们可以让你在函数组件中使用状态和其他 React 特性。React 提供了一些内置的 Hooks，例如 useState、useEffect、useContext 等，你也可以自定义 Hooks 来封装可重用的逻辑。

useState 用于在函数组件中定义状态，它接受一个初始值，并返回一个数组，数组的第一个元素是当前状态的值，第二个元素是一个更新状态的函数。例如：

```react
import { useState } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

在这个例子中，我们使用 useState 来定义一个状态 count，并使用 setCount 函数来更新这个状态。每次点击按钮时，count 的值会增加 1。

useEffect 用于在函数组件中执行副作用操作，例如数据获取、订阅事件、手动操作 DOM 等。它接受一个函数和一个依赖数组作为参数，函数会在组件渲染后执行，依赖数组用于指定在哪些情况下需要重新执行这个函数。例如：

```react
import { useState, useEffect } from 'react';

function MyComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []);

  if (!data) {
    return <div>Loading...</div>;
  }

  return <div>{data}</div>;
}
```

在这个例子中，我们使用 useState 来定义一个状态 data，并使用 useEffect 来获取数据并更新这个状态。useEffect 的第一个参数是一个函数，这个函数使用 fetch 方法获取数据，并使用 setData 方法更新状态。useEffect 的第二个参数是一个空数组，这意味着这个函数只会在组件渲染后执行一次。

总之，Hooks 是 React 中非常有用的一种特性，它们可以让你更方便地管理状态和执行副作用操作。

##### 2.说说对 State 和 Props 的理解，有什么区别？

State 和 Props 是 React 中两个重要的概念。它们都是用于管理组件数据的机制，但它们之间有一些区别。

Props 是组件的属性，可以从父组件传递给子组件。它们是只读的，子组件不能修改它们。Props 通常用于将数据从父组件传递到子组件，以便子组件可以根据这些数据渲染自己。例如，如果您有一个名为"User"的组件，您可以将用户数据作为 Props 传递给该组件，以便它可以显示用户的姓名、头像等信息。

State 是组件的状态，用于管理组件内部的数据。与 Props 不同，State 是可变的，组件可以在运行时修改它们。State 通常用于存储组件的内部状态，例如用户输入、组件的可见性等。例如，如果您有一个名为"Counter"的组件，您可以使用 State 来存储计数器的当前值，并在用户单击按钮时递增该值。

在 React 中，Props 和 State 都可以触发组件的重新渲染。当 Props 或 State 发生变化时，React 会重新渲染组件以反映这些变化。但是，Props 和 State 的更新方式不同。**Props 是从父组件传递给子组件的，因此只能由父组件进行更新。State 是组件的内部状态，因此只能由组件自身进行更新**。

总的来说，Props 和 State 都是用于管理组件数据的机制，但它们之间有一些区别。Props 是只读的，用于从父组件传递数据到子组件。State 是可变的，用于管理组件的内部状态。理解这些概念对于编写高质量的 React 组件至关重要。

##### 3.什么是虚拟 dom ? 为啥使用虚拟 dom ？操作虚拟 dom 和操作真实 dom 哪一个更快？

虚拟 dom 是一个普通的 js 对象，用来描述页面中的元素（或者说页面结构），相对于真实 dom，虚拟 dom 的属性较少，比较轻量级。操作虚拟 dom 不会导致页面的直接变化，操作真实 dom 会导致页面直接发生变化。

使用虚拟 dom 的原因，可以减少操作真实 dom 的次数，从而减少页面重新渲染的次数，提高页面的性能。具体的做法就是在一个事件循环中，React 在内部会开始一个队列，将当前事件循环的所有数据变更缓存起来，对于同一个数据的多次变更，只会将最后一次变更放入到队列中，在当前事件循环的末尾执行所有的数据变更，形成新的虚拟 dom 树，对比新旧虚拟 dom 树，找出发生变化的节点，然后将这些变化的节点应用到真实的 dom 上，从而刷新页面，通过这样的一个操作就减少了操作 dom 的次数，避免了页面的频繁重新渲染，提高了页面性能。

操作虚拟 dom 和操作真实 dom 哪一个更快，实际上如果只是单单讲操作这两个对象的话，应该没什么区别，因为他们都是一个 js 对象，可是由于操作真实 dom 会导致页面更新，所以有时说操作虚拟 dom 比操作真实 dom 快，是因为没有考虑全面，把操作真实 dom时页面更新的时间也算进去了，所以才导致说操作真实 dom 慢。

