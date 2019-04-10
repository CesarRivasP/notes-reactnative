# React Native
El componente View de react native funciona como un div mientras que el componente Text funciona como un párrafo.

Componentes en React Native

En react se arman componentes utilizando tags de html. En react native no tenemos un navegador, no son aplicaciones híbridas que corren en un pseudo navegador. React native crea aplicaciones nativas utilizando un bridge.

### Componentes principales de react native
En react se arman componentes utilizando tags de html. En react native no tenemos un navegador, no son aplicaciones híbridas que corren en un pseudo navegador. React native crea aplicaciones nativas utilizando un bridge.
Los componentes principales de react native son:

* View / ScrollView / SafeAreaView (Divs, scrolls)
  + View es el componente de RN que funciona como si fuera un <div> de html.
* Text / TextInput (Formulario)
  + Text es el componente de RN que funciona como si fuera un <p>.
* Image / ImageBackground (Imágenes)
  + El Componente Image tiene una propiedad **source** para setear el contenido del contenedor, en la cual tiene un key que es uri, para contenido externo.
* FlatList / SectionList (Listas de elementos)
* Touchable Higligth / Opacy / WithoutFeedback (Componentes para manejar los taps del teléfono)
* Animated (Sirve para animar la interfaces)
* fetch, async await, sockets (Funciones asíncronas)
* Platform (Permite identificar si es iOS o Android)
* AsyncStorage (Equivalente a localStorage)


Por ejemplo:
![enter image description here](https://static.platzi.com/media/user_upload/comp-1-46d1011b-b9ae-41a9-83d7-782eee36672a.jpg)

¿Cómo funciona?
React Bridge. “Convierte” el código js a código nativo.

Developer Experience

* Hot/live reloading
* Depuración de Javascript
* Network inspector
* Stack Trace

¿Quiénes usan react native?

* Uber eats
* Instagram
* Facebook
* Wix
* Skype
* Pinterest
* Platzi


- Si la imagen se encuentra en los archivos de la app se agrega como si fuera un componente:
```
  import Image from'./image.png';
  <Imagesource={Image} />
```
Si es un ruta de internet lo agregarias con el uri:
```
  <Image source={{uri:'la url'}}/>
```
Nota:
Para opciones avanzadas del emulador:
* adb shell input keyevent 82
* Ctrl + m


### Styles
Los estilos en React Native, se utilizan como en React, no es CSS convencional, las propiedades van con CamelCase, los valores de las propiedades pueden ser en números, si el valor es distinto como en el caso de porcentajes, rem o em, los valores van a ser strings y van entre comillas fontSize: ‘2.5rem’.
Tambien en el caso de que usemos colores en hexadecimales o un color como red o blue color: ‘#a1a1a1’.

### Implementacion de Redux
- El **Store** es donde almacenamos el estado actual de la aplicación.
- Los **Dispatch** se encargan de disparar las acciones que modificarán el state de la aplicación.
- Los **Actions** modifican el state de la aplicación dependiendo de la acción disparada.
Usamos los **mapStateToProps** junto a **connect** para avisar a nuestros componentes de que se han producido cambios en el state.
- En App.js al invocar el método dispatch del store, estamos simplemente enviando los datos recibidos de la API al nuevo “estado global” definido por el store, e indicando la “acción” de lo que queremos que se haga con estos datos. Luego a través del método connect se tienen disponibles estos datos en cualquier container sin necesidad de estarlos pasando explícitamente de props en props. Es lo que llamaríamos un nuevo estado global.

### Importación de archivos
Hay una técnica muy útil hasta este punto cuando tenemos muchos componentes en distintas carpetas y nos ocurre la siguiente situación:
```
import Component from '../../../component-folder/Component
```
Para evitarnos ese monton de **…/…/** podemos crear un archivo **package.json** en cada carpeta importante, la carpeta de las pantallas por ejemplo.

Dentro de ese package.json colocamos:
```
}
    "name": "@screens"
{
```
Ya con esto hecho, podemos estar en cualquier otra carpeta y llamar a cualquier componente que esté dentro de la carpeta screens de esta manera.
```
import HomeScreen from'@screens/HomeScreen'
```
Y así nos evitamos el …/…/…/Component

### React Native Debugger
Si no sale el debugger, primero habrán el navegador y vayan a **http://localhost:8081/debugger-ui/** (la app intenta abrir el 10.0.2.2:8081/debugger-ui/), esta dirección si que hace el debugger. Y ya en la app abren la ventana de dev (ctrl + m ó cmd + m) y seleccionen el debugger.
