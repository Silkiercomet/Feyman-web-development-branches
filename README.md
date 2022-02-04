# React - Feyman technique tree

El proposito de este README es documentar mi aplicacion de la tecnica de Feyman a los conceptos del framework React 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Links](#links)
- [React Fundamentals 101](#react-fundamentals)
  - [create-react-app](#built-with)
  - [basics of JSX](#what-i-learned)
  - [concept of components in react](#continued-development)
  - [difference between a component and an element](#useful-resources)
  - [how to render an element/component consiationally](#built-with)
  - [function and class componets](#what-i-learned)
  - [how to display a list of elements and components](#continued-development)
  - [how to think in terms of components](#useful-resources)
- [React Fundamentals 2.0](#my-process)
  - [props](#built-with)
  - [state](#what-i-learned)
  - [difference between props and state](#continued-development)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

## Overview

Este Readme contiene una recopilacion de los principales temas que conforman el framework react, tambien se incluye mi interpretacion de estos y sus prosibles usos en un projecto, para desarrollar este documento se aplico la tecnica Feyman


### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

## React Fundamentals 101

### create-react-app

Esta herramienta evita que el usuario tenga que configurar react en su computadora y se concentre en desarrollar la aplicacion facilitandole el uso de las ultimas caracteristicas de JavaScript y la configuracion de paquetes importantes como webpack, babel y ESlint, tambien brinda las herramientas necesarias para desplegar la aplicacion a produccion de una menera mas sencilla

para usarla es necesario contar con un terminal con node.js/yarn y npm para acceder a los paquetes de esta, y luego invocar los comandos necesarios en este casos eran npx-create-react-app (app-name) luego el mismo terminal manejara la instalacion de todas las dependencias necesarias para crear una aplicacion react.

esta herramienta crea el ambiente propicio para que los desarrolladores puedan enfocarse en la creacion de aplicaciones, asi como un parque infantil es creado para que los niños puedan jugar y divertirse dandoles todas las opciones desde el principio que tiene para ofrecer, de la misma manera create-react-app le da la libertad de usar la herramientas dada a su antojo

### JSX

JSX es la sintaxis que utilizamos en react para facilitar el desarrollo de interfaces y la logica de estas, ya que las combina en un solo ambiente en lugar de separarlas como seria el caso de si se usara HTML y vanilla JS donde el maquetado seria un documento HTML y la logica estaria en un archivo JS, facilita el renderizado de elementos dinamicos ya que los Elementos JSX son tratados como expresiones de JavaScript y como tal pueden ser concatenadas a otras expresiones por ejemplo:

```JSX
<h1>Hello, {formatName(user)}!</h1>;
```

JSX es basicamente azucar sintatico y nos permite accerder a la funcion "React.createElement(component, props, ...children)" de una manera mas intuitiva, babel se encarga de traducir el componente jsx a una funcion que react pueda copilar y mostrar en pantalla, todos los parametros del metodo createElement estan disponibles para el desarrollador los "props" y "children"

JSX nos facilita la creacion y la lectura de los elementos que pertenecen a nuestra interfaz permitiendonos crear una estructura mas familiar y entendible como las que podemos crear en HTML, aunque React.createElement es lo que sigue ejecuntadose para renderizar a nuestros componentes la sintaxis de JSX es con lo que el desarrollador interactua, nos permite ver las cosas de una manera mas clara y estructurada, como un par de lentes

#### Notas extras:


### concept of components in react

los componentes son una caracteristica fundamental de react, ya que permite crear una aplicacion donde sus piezas son independientes entre si y cada una tiene su propio ambiente en el que pueden recibir a otros componentes dejandonos una estructura con piezas reutilizables en cualquier otra parte , los componentes son funciones tratadas de manera especial por react, para definir a uno se debe iniciar por nombrarlo con una Mayuscula al principio de lo contrario sera tratado como una etiqueta del DOM, son por lo general un conjunto de elementos que son manejados por la logica definida en el componente

puede verse el concepto de componentes en react como si una aplicacion se tratase de un set de LEGO, donde cada pieza puede ser re-utilizada en distintas partes del mismo para distintos propositos, asi mismo los componentes de react pueden repetirse en cualquier lugar de la aplicacion y pueden ser utilziados todas las veces que sean necesarios 

#### Notas extras:

- los componentes son anidables, puede haber referencias a otro componente en la salida de un componente

- nombrar los props desde el punto de vista del componente, no del uso que se le dara

- los componentes una vez renderizados no son mutables, se deben renderizar para cambiar su contenido

### Difference between a component and an element

un componente esta formado por elementos (tiene que devolver un elemento) y junto con todo esos conforman un todo

un elemento es un objeto de react que describe un node del DOM recibiendo los siguientes atributos: un type (que define que tipo de elemento se quiere mostrar por ejemplo un <button>), props (las propiedades ya tributos de dicho elemento) y un children (que son los elementos que existen dentro de el) 

si los componentes son las piezas de un set de LEGO los elementos son las particulas de plastico que forman a esta pieza


### How to render an element/component conditionally

Con el uso de operadores logicos podemos definir las condiciones a cumplirse para que un componente se renderice, al igual que con vanilla JS tenemos todas los operadores a nuestra disposicion si se quiere usar el operador "if()" podemos asignar el elemento/componente a una variable si y solo si la condicion necesaria se cumple por ejemplo

```js
let button;
    if (isLoggedIn) {
      button = <LogoutButton onClick={this.handleLogoutClick} />;
    } else {
      button = <LoginButton onClick={this.handleLoginClick} />;
    }
```

ya que JSX permite el uso de expresiones de javascript podemos dar uso de esto durante el renderizado para definir si un componente es leido y renderizado o no con el operador logico '&&', si la condicion es true el siguiente elemento sera leido de lo contrario no sera ignorado

react nos permite decidir bajo que condiciones cierto elemento debe renderizarse, esto lo logramos usando la sintaxis de JS adaptada a JSX 

```js
{unreadMessages.length > 0 &&
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
```
tambien podemos dar uso al operador ternario para evaluar la condicion y el elemento a renderizarse

```js
      {isLoggedIn
        ? <LogoutButton onClick={this.handleLogoutClick} />
        : <LoginButton onClick={this.handleLoginClick} />
      }
```


### how to display a list of elements and components

Comunmente nos encontraremos con la necesidad de mostrar una lista elementos que si bien son iguales entre si la data que contienen es distinta, podemos utilizar los metodos map() filter() para manejar esta tarea de manera mas dinamica, podemos tanto recorres arreglos y psar los datos de este como props a un componente o podemos hacer directamente en un componente que acepte un array items por ej:

```js
const people = [
  'Creola Katherine Johnson: mathematician',
  'Mario José Molina-Pasquel Henríquez: chemist',
];

export default function List() {
  const listItems = people.map(person =>
    <li>{person}</li>
  );
  return <ul>{listItems}</ul>;
}
```

esta es una herramiente sumamante util a la hora de renderizar cualquier componente que se repita pero con distinta data , imagenes de una galleria, listas de comentarios o en caso de que necesitemos encontrar elementos que cumplan ciertos para metros podemos usar filter(para solo mostrar los resultados que sean una march) es una manera genial de automotizar el trabajo del developer.

Asi como react se puede comportar como un niño a la hora de renderizar elementos que queire saber hasta el masminimo detalle de ellos, tambien podemos decirle a ese niño que quiero que muestre este conjunto de elementos y el armara cada uno que le pidas hasta el ultimo detalle de estos

### How to think in react

- empezar con un mock: una interfaz sencilla sin estilos que desarrolle la funcionalidad requerida

- visualiza los componentes que necesitaras, para esto debes dividir cada componente y procurar que cada uno ejerza una sola funcion, luego podemos crear la jerarquia de los componete cosa que podemos lograr definiendo los componentes que estan dentro de otro

- crear una version estatica de la aplicacion, esto seria una interfaz sin nada de interactividad la UI ya que tenemos la jerarquia de nuestra app podemos decidir si la creamos de arriba hacia abajo o al revez, en aplicaciones sencillas es recomendable la primera y la segundas en aplicaciones mas grandes, ya que desde los hijos podemos ir creando componentes que seran reutilziables a lo largo de la app 

- defini el set minimo de estados mutables que tu app necesita para funcionar y procura mantenerlo lo mas simple posible

- define donde tu estado DEBERIA vivir para esto nos haremos las siguientes preguntas:

* idetifica cada componente que renderiza algo basado en un estado
* encuentra un componte padre que compartan
* el componente padre o otro componente mas alto en la heraquia deberia contener el estado
* si no puedes encontrar un componente en el que tenga sentido tener el estado, crea un componente con el unico proposito de contenerlo arriba en la herarquia del padre compartido

- interactua con la data con el use del setState() 

se puede pensar de los componentes como si de una receta de cocina se tratase, si no se agregan ingredientes distintos a la preparacion y se sigue los pasos apropiados el platillo, siempre sera el mismo 

### Keeping Components Pure

Una funcion pura es una que cumple un calculo y nada mas, hacer que cada componente en tu aplicacion sea una funcion pura te asegura evitarte un monton de bugs y los que tengas sera localizados con mayor facilidad

una funcion pura debe cumplir dos conceptos

- no se mete en los asuntos de nadie, ninguna variable debe cambiar mientras esta funcion se ejecuta

- si se le da el mismo valor como un input siempre devolvera el mismo output, sin importar cuantas veces se ejecute

como si de las matematicas se tratase , 2 + 2 es siempre 4 lo quieras o no, los componetes puros son iguales, siempre daran el mismo resultado si se usa el mismo input 

sin embargo es totalmente aceptable manipular variables que hayan sido declaradas dentro del scope de la funcion ya que estas se reiniciaran al inicio de la invocacion y siempre devolveran el mismo resultado sin manipular las variables exteriores

## React Fundamentals 102

### understand the concept of props in react (props, default props, prop types)

Props (propiedades) es la manera en la que los componentes de react se comunican de uno al otro, cada componente padre puede enviar a un componente hijo una pieza de informacion en forma de props, su sintaxis es igual a los atributos de los HTML tags pero puedes pasar cualquier valor JS atraves de estos

default props: durante la destructuracion de los props recibidos por un componente, podemos establecer un valor predeterminado en caso de que no se reciba dicho valor del componente padre o que se reciba como "undefined" EJ:

```js
function Avatar({ person, size = 100 }) {
  // ...
}
```
el valor de size dentro del componente Avatar sera 100 si durante la invocacion de este en el componente padre ocurre alguno de los siguientes casos

```jsx
<Avatar perso={person} />

<Avatar perso={person} size={undefined} />

<Avatar perso={person} size={person?.size} />
```

**Note: si se llegara a dar el caso de que se envia un prop que pertenece a un objeto mediante la notacion "." es una buena practica definirlo con el signo "?" en caso de que sea undefined no devolvera un error .**

los props de un componenete no son estaticos, su datos se evaluan y pueden cambiar en cada renderizacion, los props reflejan el valor de los datos en cualquier momento en lugar de solo al principio como seria el caso con hard-coded HTML, sin embargo son inmutables para cambiar un prop dado el componente padre debe enviarle un valor distinto

los props son el conocimiento compartido de todo la aplicacion asi como nosotros vamos de boca en boca dando y recibiendo informacion, los props hacen esta tarea en el ambiente de react pasando informacion desde los padres hasta los hijos.

### understand the concept of state in react

Normalmente para añadir intereactividad a un sitio es necesario que ciertos valores cambien dentro de un componente, los componentes necesitan recordar estos valores y una variable normal sera suficiente porque estas se re-inicializan en cada render, para solucionar esto react hace uso de uno de State.

State es la memoria de un componente atraves de todas las renderizaciones, cada componente puede tener su propio state ya que los state son individuales estos no tendran ninguna incidencia fuera del componente en el que son declarados 

asi como nosotros recordamos cosas que nos paracen importantes y si estas cambian de alguna forma en nuestra mente las actualizamos, react nos permite hacer lo mismo con states 

### state vs props

los props son la forma de comunicacion que tienen los componentes con sus hijos mientras que los state son piezas de informacion redordadas y que solo puden cambiar dentro del mismo ambiente del componente  que pueden ser enviadas mediante props hacia el componente/elemento hijo

los componetes son internos y solo manejados por el componente mismo, props son externos y son manejados por el componente padre que los envia (aunque tambien gozan de cierta autonomia si se define un default dentro del componente que lo recibe, esto solo aplica a casos es los que no se pase el props o se pase como undefined)

una manera de visualizar este predicamento es ver al state como una entidad autonoma que su mutacion y valor se administra dentro del componente en que es inicializado, mientras que props son como los argumentos de una funcion, son una fuente externa y no dependen del componente mismo

## React fundamentals 3.0: basic hooks

### what are hooks

los hooks nos permiten enganchar a componentes funcionales con caracteristicas especiales de react sin la necesidad de crear una clase 

### what are the rules of hooks

- Solo llamar Hooks en el nivel superior. No llames Hooks dentro de loops, condiciones o funciones anidadas.

- Solo llamar Hooks desde componentes de función de React. No llames Hooks desde las funciones regulares de JavaScript. (Solo hay otro lugar válido para llamar Hooks: tus propios Hooks personalizados. En un momento aprenderemos sobre estos).

### useState Hook

este hook nos permite agregar un estado a un componete funcional, esto significa que ahora podremos asignar valores a una variable que se mantendran durante cada redenrizacion del componente a diferencia de las variables que se inicializaran en cada una, esta es inmutable porque el componenete la memoriza.

un useState se vera de la siguiente manera:

```jsx
import { useState } from "react"

function ejemplo(){

  const [estado, setEstado] = useState(0)

}
```
el use estate hook una vez llamado devuelve un array con dos valores, el valor en la posicion [0] siempre sera el valor actual del estado, el segundo [1] sera la "funcion Setter" que nos permite actualizar el valor del estado, cuando se llama la funcion de useState tambien podemos darle un parametro inicial que se le asignara en primera instancia al estado en el caso del ejemplo es el valor "0".

este hook es como un espacio de nuestra memoria donde guardamos una informacion esencial que no nos podemos permitir olvidar porque una tarea que tendremos que realizar en el futuro depende de ella, esta pueda cambiar pero aun asi la recordaremos 

### useEffect Hook

este hook nos permite manejar efectos secundarios en nuestro componente, por efectos secundarios se entiende como actualizaciones manuales del DOM, peticiones de datos (API), establecimiento de suscripciones (datos especificos de una base de datos ej: el estado de otro usuario de la DB), este se ejecuta siempre luego de una renderizacion pero podemos limitar este comportamiento asignadole dependencias de tal forma que solo se ejecute cuando el valor de alguna de ellas cambie.

si una useEffect devuelve una funcion esta se le llama "funcion de saneamiento" esta termina el efecto cerrando el procedimiento, por ejemplo si se hace una solicitud con al status de un usuario especificado con su id y no se realiza un saneamiento la siguiente solicitud sera por el usuario anterior y el nuevo creando un "memory leak"

```jsx
function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Especifica cómo sanear este efecto:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  },[isOnline]);

  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}
```
todo lo que no este relacionado con la renderizacion de JSX (osea lo que un componente funcional retorna) es considerado un side effect, en el ejemplo anterior se interactua con un servidor externo para conocer el estado de un usuario esto es un side effect

use effect nos permite realizar de una manera mas efectiva en react lo que conseguiamos en JS vanilla con los querySelector y los eventListeners, ya sea remplazando elementos jsx de nuestro componente o haciendo llamadas a API's y manejando los datos devueltos, es el medio por el que nuestra pagina interactua con el mundo exterior.

### useCallback Hook

este hook evita que una funcion se ejecute de nuevo devolviendo el resultado de la funcion memorizado si sus argumentos siguen siendo los mismos que en la ultima ejecucion, esta conclusion la saca el hook al compara los valores anterior "===" con los nuevos dados ej 

```jsx
/*a huge list of items*/
import useSearch from './fetch-items';
function MyBigList({ term, onItemClick }) {
  const items = useSearch(term);
  const map = item => <div onClick={onItemClick}>{item}</div>;
  return <div>{items.map(map)}</div>;
}
export default React.memo(MyBigList);
/*if term === term se devolvera el mismo resultado anterior*/
import { useCallback } from 'react';
export function MyParent({ term }) {
  const onItemClick = useCallback(event => {
    console.log('You clicked ', event.currentTarget);
  }, [term]);
  return (
    <MyBigList
      term={term}
      onItemClick={onItemClick}
    />
  );
}
```

esta funcion debe utilizarse en ocaciones especificas en las que se puede evitar que un procedimiento grande y pesado se vuelva e ejecutar, ya que sigue renderizandose en cada ejecucion y habra casos en los que sera mejor ejecutar la funcion que realizar la comparacion, este hook es una malla de contencion que evita que realicemos la misma tarea pesada dos veces recordandonos que no es necesario porque ya lo hicimos una vez y ya tenemos el resultado

### useRef hook

este hook nos permite recordar cierta informacion que no queremos que dispare una renderizacion cuando es actualizada como si de un bolsillo secreto se tratara, tambien es util para hacer referencia a un elemento especifico del DOM mediante su propiedad ".current" tendremos acceso al nodo completo del elemento referenciado y podremos manipularlo a nuestro antojo 

cuando usar useRef:

- cuando se quiere guardar la id de un interval para limpiarlo despues

- cuando se quiere manipular el DOM de un nodo en especifico

- guardando variables que no son necesarias para calcular el JSX (ya que useRef no dispara una renderizacion si se hace referencia e este valor en el JSX este no se actualizara)

mientras que state funciona como un fotografia ref funciona como un video que sigue de cerca los cambios que surgen 

para usar un ref se utiliza la suiguiente syntaxis:

```jsx
import {useRef} from "react"
function App() {
  let ref = useRef(0)
  function plus(){
    ref.current++
  }
  return(
    <h1 ref={ref} onClick={()=> plus}></h1>
  )
}

```

### useMemo hook

este hook es muy parecido a useCallback hook con la ligera diferencia que este devuelve un valor y callback ejecuta una funcion, lo cual es de gran utilidad cuando se tiene que optimizar a un componente que realiza una tarea pesada, esto no es deseado porque se puede ejecutar de nuevo en cada renderizacion del componente si la tarea es lo suficientemente larga esto puede traer problemas de rendimiento, por eso se crear una nueva variable donde la tarea ejecuda es envuelta en un useMemo()

```jsx
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

useCallback(fn, deps) es igual a useMemo(() => fn, deps)
```

antes de ejecutar la funcion y retornar su valor useMemo evalua si las dependencias han cambiado de valor esto lo hara mediante un "===" asi que se debe ser cuidadoso de no usar arreglos o objetos de dependencia ya que estos se reinician en una instancia nueva en cada render, si los valores coinciden se retornara el valor guardado en la cache que fue el resultado de estas dependencias y no se ejecuta de nuevo la tarea esta solo se ejecutara si una de las dependencias cambia

react por naturaleza se renderiza constantemente, esto puede ser un problema cuando manejamos funciones con procedimientos pesados useMemo y useCallback nos permiten negar ese comportamiento para mejorar el rendimiento de nuestro componente 

### useReducer hook

este hook es una version mas avanzada del useState, ya que nos permite crear un state (una variable que sera almacenada en la memoria del componente y otra que contiene un objeto de funciones que pueden interactuar con el estado, siendo de mucha utilidad para ocaciones en las que se interactua repetidamente con un estado

```jsx
function yourReducer(state, action) {
  // return next state for React to set
  action //accedera a los valores enviados mediante el dispatch en este caso type
}

function Counter() {
  const [state, dispatch] = useReducer(yourReducer, initialState);
  ...
  <button onClick={() => dispatch({type: 'decrement'})}>-</button>
  ..
}
```

este hook nos permite juntar el estado de un componente y su logica en el mismo sitio, pero si es invocado en otro componente se inicializara de nuevo en una dependencia distinta a la de la invocacion original, para ese caso se utiliza

## Context API

este hook nos permite abstraer la logica y los states de nuestra aplicacion en un solo archivo al que podran acceder todos los componentes, se accede a este archivo mediante el hook "useContext" junto con los datos que se desean dentro de parentesis, para poder acceder al context se debe definir un tag llamado " <Context.Provider data={}>{...}</Context.Provider>" que envuelva a los componentes para que estos puedan acceder al contenido del context, en data enviamos la informacion que nos interesa que los componentes compartan 

cuando la aplicacion se hace muy extensa o hay partes que necesitan acceder al mismo state pero que estan separadas en el tree podemos utilizar este hook para asi evitar pasar nuestro state por componentes hijos que no tienen ningun uso para el, ya que con Context podremos acceder al este de este en toda nuestra aplicacion 

pasos a seguir apra crear un Context primero creamos una carpeta llamada "Context" y ahi creamos el componente que contendra nuestro contexto (por conveniencia el nombre de este componenete termina en Context)

- 1 se importa el createContext hook
- 2 se crea el contexto asignandole una variable a nuestro hook :
```jsx
const MoviesContext = createContext()
```
- 3 se crea un provider este sera el tag que contendra la data a ser enviada a los hijos seleccionados 
```jsx
const MoviesProvider = ({ children }) => {
  const data = { movies: initialMovies };

  return (
    <MoviesContext.Provider value={data}>{children}</MoviesContext.Provider>
  );
};
```
- 4 se exporta el contexto por default y se exporta al provedor
```jsx
export { MoviesProvider };
export default MoviesContext;
```
- 5 se envuelve a los componentes que le daran uso al contexto con el provedor 
```jsx
<MoviesProvider>
        <Navbar />
          <MovieList />
</MoviesProvider>
```
- 6 se importa el useContext hook y el contexto 
```jsx
import React, { useContext } from "react";
import MoviesContenxt from "./Context/MoviesContenxt";
```
- 7 se accede al valor definiendo una variable (o destructurando las variables que devuelve el context) con el useContext 
```jsx
const data = useContext(MoviesContenxt);
```
con esto se puede interactuar con la logica del contexto desde cualquiera de los componentes que esten envueltos en el provedor

### Custom hooks, when and why to use then

es una funcion cuyo nombre empieza con "use" y pude llamar otros hooks dentro de ella, podemos definir las variables que se reciben y las que se devuelven (retornando un objeto que sera destructurado o un array con los resultados si se devuelve mas de un valor). 

esta caracteristica de react nos permite separar la logica de los hooks de nuestro componente en una sola funcion, a diferencia de useReducer que nos permite extraer la logica del state de nuestro componente, custom hooks nos deja combinar useEffect con useState y cualquier otro hook con las props que queramos en un procedimiento separado que sera tratado por react como un hook en nuestro componente

lo bueno de esto es que nos permite reutilizar el hook en cualquier parte de nuestra aplicacion que utilicen la misma logica implementada en el hook 

un custom hook es como un diccionario al cual podemos hacer referencia a una palabra cualquier cantidad de veces, en cualquier otra parte y esta tendra el mismo significado en todas las ocasiones, sin embargo la logica de este hook se reiniciara cada vez que sea invocada, si es invocado en dos componentes distintos estos seran independientes el uno del otro

## react perfomance optimizations

### code spliting

conforme una aplicacion crece el tamaño de sus archivos CSS/JS se puede volver lo suficientemente pesados como para afectar a la experiencia del usuario, code-spliting evita esto al separar en distintos modulos que seran cargados al ser solicitados o tambien en paralelo, en react podemos conseguir esto a traves de React.lazy y suspense

```jsx
import React, { Suspense, lazy } from 'react';

const OtherComponent = lazy(() => import('./OtherComponent'));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```
los componentes importados con lazy loading solo se renderizan despues de que los que esten fuera del suspense (que son los criticos por decirlo de una forma con urgencia) se hayan renderizado de esta forma dandoles prioridad, el tamaño del bundle es dividio a la mitad (los no importantes dentro del Suspense y los importantes fuera de este)

## Acknowledgments

This is where you can give a hat tip to anyone who helped you out on this project. Perhaps you worked in a team or got some inspiration from someone else's solution. This is the perfect place to give them some credit.

**Note: Delete this note and edit this section's content as necessary. If you completed this challenge by yourself, feel free to delete this section entirely.**
