
# React Native
![enter image description here](https://cdn-images-1.medium.com/max/2400/1*dIocy2HvI_BIpziOypf8ig.jpeg)
React Native te permite crear aplicaciones móviles usando solo JavaScript. Utiliza el mismo diseño que React, lo que le permite componer una interfaz de usuario móvil utilizando componentes declarativos

## ¿Cómo funciona?
Mediante React Bridge, que “Convierte” el código javascript a código nativo.
![enter image description here](https://uploads.toptal.io/blog/post_image/90209/cold-dive-into-react-native-a-beginners-tutorial-922a625efe84a4c2d782343b333b0bdb.png)

### Developer Experience

* Hot/live reloading
* Depuración de Javascript
* Network inspector
* Stack Trace

### ¿Quiénes usan react native?

* Uber eats
* Instagram
* Facebook
* Wix
* Skype
* Pinterest
* Platzi

## Componentes en React Native
![enter image description here](https://instabug.com/blog/wp-content/uploads/2018/03/Featured.jpg)

En react se arman componentes utilizando tags de html. En react native no tenemos un navegador, no son aplicaciones híbridas que corren en un pseudo navegador. React native crea aplicaciones nativas utilizando un bridge.

## Componentes principales de react native
En react se arman componentes utilizando tags de html. En react native no tenemos un navegador, no son aplicaciones híbridas que corren en un pseudo navegador. React native crea aplicaciones nativas utilizando un bridge.
Los componentes principales de react native son:

* View / ScrollView / SafeAreaView (Divs, scrolls)
  + View es el componente de RN que funciona como si fuera un <div> de html.
* Text / TextInput (Formulario)
  + Text es el componente de RN que funciona como si fuera un <p>
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

### Listas
 React Native tiene dos tipos de Listas para usar:
> -   FlatList
> -   SectionList

#### FlatList

Puede ser utilizada para listas sencillas. Las propiedades que tiene son:
>
> -   **data**: Recibe un array de obj o un json. Este vendría a ser el listado
> -   **renderItem**: Es una prop que recibe un componente a renderizar, hace algo similar a un “.map()” sobre la lista pasada a Data, por lo tanto recibimos al listado como propiedad, al cual podemos hacerle un “destructuring” pasandole mediante llaves al elemento.
El componente convierte la data y nos deja un key “item” que podemos utilizar en renderItem para pasarle datos a nuestro componente, por eso siempre debemos llamarlo así.

```js
<FlatList
      data={list} //Se le pasa una lista o un array.
      renderItem={ //Va a recibir una func y puede renderizar un componente
        ({item}) => <Text> {item.title} </Text>
      }
    />
```
#### SectionList

Puede ser utilizada para listas más complejas.

### Platform
**Platform**  nos ayuda a mostrar elementos de la aplicación dependiendo de si es  **iOS**  o  **android**, en este caso mostramos el color de background del contenedor (rojo si es iOS o azul si es android):
```
container: {
  flex: 1,
  justifyContent: 'center',
  alignItems: 'center',
  backgroundColor: Platform.select({
     ios: 'red',
     android: 'blue'
  }),
},
```
## Organización del proyecto
**Como se ve. Dumb Component. Presentational Component**

-   Puede contener smart componentes u otros componentes presentacionales.
-   Permite composición {props.children}
-   Son independientes del resto de la aplicación.
-   No especifica como se cargan los datos. Eg. this.props.title
-   Recibe datos y callbacks mediante propiedades.
-   Generalmente no tienen su propio estado, es raro que tenga un ciclo de vida.
-   Se escriben como componentes funcionales al menos que necesiten mejoras de performance (PureComponents)

**Que hace. Smart. Container Component**

-   Se centra en como funciona la app. Tienen ciclo de vida y states. Controlan como funciona la aplicación.
-   Contiene componentes de UI y otros smart.
-   No tienen estilos.
-   Proveen datos y callbacks a otros componentes (UI o smart)
-   Normalmente tienen estado.
-   Llaman a acciones
-   Se pueden generar por higher order components

**¿Por qué dividir los componentes en smart y dumbs?**

-   Separación de responsabilidades (Se parece a MVC, V para dumbs y C para smarts)
-   Mejorar la capacidad de reutilizar componentes


## Styles
Los estilos en React Native, se utilizan como en React, no es CSS convencional, las propiedades van con CamelCase, los valores de las propiedades pueden ser en números, si el valor es distinto como en el caso de porcentajes, rem o em, los valores van a ser strings y van entre comillas fontSize: ‘2.5rem’.
Tambien en el caso de que usemos colores en hexadecimales o un color como red o blue color: ‘#a1a1a1’.

### StyleSheet
El componente de API **StyleSheet** se usa para crear hojas de estilo, esta crea un **objeto javascript** con **estilos javascript** para poderlos agregar a nuestros componentes gracias al atributo **style** con el que cuentan la mayoría de los componentes.
Objeto de StyleSheet:

```
const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  }
});
```
Atributo style en componentes:
```
<View style={styles.container}>
  ...
</View>
```
**Nota**: la propiedad background es  **backgroundColor**, hay un componente dedicado a imágenes de fondo llamado  **ImageBackground**.

### Uso de estilos
Diferencia entre:
```
const styles = StyleSheet.create({ separator: { flex: 1, marginHorizontal: 5, } })
```
**Nota**: aquí se creo un objeto de estilos, el **flex: 1** hace que el elemento tome todo el ancho y alto y el **marginHorizontal: 5** hace que las categorias se separen entre ellas con un margen a la derecha e izquierda de 5px
La realidad es que ambos hacen lo mismo y ambos casos en cuanto a  **calidad de código**  están limpios a diferencia de cuando insertamos estilos inline.

y
```
const styles = { separator: { flex: 1, marginHorizontal: 5, } }
```

La respuesta simple en cuanto a la diferencia entre esas maneras de estilizar los componentes es  **Performance**.

La respuesta compleja de sus diferencias esta en  **como lo hacen**, y es que si bien realizar operaciones al enviar datos al  **Bridge**  es costoso en cuanto a performance usar  **StyleSheet.create()**  reduce ese esfuerzo.

Esto es debido a que  **StyleSheet.create()**  hace que sea posible hacer referencia al objeto que crea con los estilos por  **ID**  en lugar de crear un nuevo objeto de estilo cada vez (lo que ocurre cuando mandamos un objeto simple con los estilos en JS).

Entonces  **StyleSheet.create()**  permite enviar estilos solo una vez a través del  **Bridge**. Todos los usos posteriores (de estos estilos) van a referir un  **ID**.

### Flexbox
La direccion por defecto de los estilos de flexbox en react-native (propiedad `flexDirection`) esta seteada en columna, es decir, `flexDirection: 'column'`

### Otros apuntes
Para proyectos que no requieran de estilos totalmente personalizados podemos utilizar algunos de estos paquetes para potenciar la velocidad de nuestro desarrollo cuanto estilos:

-   [Native Base](https://www.npmjs.com/package/native-base)  en lo personal mi favorita ya que trae una gran variedad de componentes que pueden ver  [aquí](http://docs.nativebase.io/Components.html)
-   [React Native Material UI](https://www.npmjs.com/package/react-native-material-ui), basada en el estándar Material de Google, pueden ver los componentes que trae  [aquí](https://github.com/xotahal/react-native-material-ui/tree/master/docs)
-   [React Native Easy Grid](https://www.npmjs.com/package/react-native-easy-grid)  Este es un paquete desarrollado por los autores de Native Base, y sirve para hacer layouts bastante complejos de una manera bastante intuitiva.

Aunque es bastante recomendado que practiquemos antes desarollando nuestros estilos de una forma más vanilla, sin el uso de paquetes de terceros.

-   SafeAreaView - renderiza el contenido en un area segura para que el contenido se vea bien en todos los dispositivos principalmente los que tienen un notch

-   Estilos para imagenes dentro de RN, se llama resizeMode que sería similar a background-size de css.  
    **_resizeMode _**por Default esta en  _cover_, otras opciones son  _**contain**_,  **_stretch_**,  **_repeat_**,  **_center_**.

-   El padding en RN funciona un poco diferente ya que se le puede dar un padding general (top, right, bottom, left), pero si se quiere hacer solamente para right & left se tiene que hacer a mano. Para estos casos se agregan 2 opciones para utilizar:

1.  **_paddingVertical_**: esto sería lo equivalente a utilizar (_paddingTop _y  _paddingBottom_)

2.  **_paddingHorizontal_**: esto sería lo equivalente a utilizar (_paddingRight _y  _paddingLeft_)
3.  **paddingTop**: value
4.  **paddingBottom**: value
5.  **paddingRigth**: value
6.  **paddingLeft**: value

**resizeMode**  
Cambiar el tamaño de la imagen cuando el marco no coincide con las dimensiones de la imagen.  
default (cover), otras opciones:

-   `contain`
-   `stretch`
-   `repeat`
-   `center`

**Nota**: SafeAreaView en iPhone solo funciona desde iOS 11 en adelante, para teléfonos sin actualizar como un iPhone 5 hay que usar `Platform`para ajustar el texto debajo del staturBar y un `parseInt` para convertir la version en número debido a que iOS 10.3.3 no podria ser comparado

**TouchableHighlight**, al mantener presionado el componente cambia de color.

**TouchableOpacity**, al mantener presionado, el componente se hace un poco transparente (baja su opacidad).

**TouchableWithoutFeedback**, No tiene efectos visuales al mantener presionado el botón.

#### Otras propiedades
* La propiedad  **onPress**  para realizar eventos en ReactNative solo funciona con los componentes  **Touchable**.

* La propiedad  **underlayColor**  cambia el color que se va a cambiar al mantener presionado el componente  **TouchableHighlight**.

## Implementacion de Redux
- El **Store** es donde almacenamos el estado actual de la aplicación.
- Los **Dispatch** se encargan de disparar las acciones que modificarán el state de la aplicación.
- Los **Actions** modifican el state de la aplicación dependiendo de la acción disparada.
Usamos los **mapStateToProps** junto a **connect** para avisar a nuestros componentes de que se han producido cambios en el state.
- En App.js al invocar el método dispatch del store, estamos simplemente enviando los datos recibidos de la API al nuevo “estado global” definido por el store, e indicando la “acción” de lo que queremos que se haga con estos datos. Luego a través del método connect se tienen disponibles estos datos en cualquier container sin necesidad de estarlos pasando explícitamente de props en props. Es lo que llamaríamos un nuevo estado global.

## Importación de archivos
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

### Importación de Imágenes
Si la imagen se encuentra en los archivos de la app lo agregarias como si fuera un componente:
```
import Image from'./image.png'; <Imagesource={Image} />
```
Si es un ruta de internet lo agregarias con el uri:
```
<Image source={{uri:'la url'}}/>
```
Si nuestra imagen la tenemos localmente la podemos importar con require():
```
<Image source={require('./assets/logo.png')}/>
```

## React Native Debugger

Para opciones avanzadas del emulador:
* adb shell input keyevent 82
* Para acceder al menú de  **herramientas de desarrollador**  en emulador de Android hay que usar la siguiente combinación de teclas:  
>**CMD + M**  (MacOS) o  **CTRL + M**  (Windows o Linux).

En emulador de iOS en MacOS la combinación de teclas es la siguiente:  
>**CMD + CTRL + Z**

En caso de que al debuggear les abra una pestaña con la url:  **[http://10.0.2.2:8081/debugger-ui](http://10.0.2.2:8081/debugger-ui)** con el error de que no es posible conectarse hay que hacer lo siguiente:
1.  Activar el menú de herramientas en el emulador  **CMD+M**  o  **CTRL+M**
2.  Ir a  **Dev Settings**
3.  Ir a  **Debugging**  en  **Debug Server Host & Port for Device**
4.  Escribir  **localhost:8081**
5.  Ahora donde van a debuggear será en  **localhost:8081/debugger-ui**
-  Para que abra el localhost automático se puede cambiar la opción en “Dev Settings > Debug server host & port for device” y se coloca localhost:8081.
- Si tienes consoles.warn molestos en el emulador, los puedes ocultar con la siguiente linea:  
**console.disableYellowBox = true**

Si no sale el debugger, primero habrán el navegador y vayan a **http://localhost:8081/debugger-ui/** (la app intenta abrir el 10.0.2.2:8081/debugger-ui/), esta dirección si que hace el debugger. Y ya en la app abren la ventana de dev (ctrl + m ó cmd + m) y seleccionen el debugger.

### En linux
Para habilitar el debugging en chrome / linux … hay que estar pendiente de activar las opciones de Pausa que indica el mensaje del navegador
También es necesario asegurarse de correr el comando:

```bash
adb reverse tcp:8081 tcp:8081

```

Antes de correr la app … puedes usar:

```bash
adb reverse tcp:8081 tcp:8081 && react-native run-android
```
- Antes de habilitar la depuraci[on desde el emulador / dispositivo … es mejor acceder manualmente a  
**localhost:8081/debugger-ui**  … ya que 10.0.2.2:8081/debugger-ui … genera un TIMEOUT …  
ya luego de haber abierto esta url, si se puede activar la depuración en el emulador / dispositivo.


## Plugins
### Plugin para reproducir video
Si iniciaste tu proyecto con  **create-react-native-app** el plugin **react-native-video**  no te va a servir. Por otro lado, **Expo** tiene un reproductor bastante customisable. Pero basta con el siguiente código para verlo.

```
import { Video } from 'expo';
import VideoPlayer from '@expo/videoplayer';

<VideoPlayer
  videoProps={{
    shouldPlay: true,
    resizeMode: Video.RESIZE_MODE_CONTAIN,
    source: {
      uri: 'https://bitdash-a.akamaihd.net/content/sintel/hls/playlist.m3u8',
    },
  }}
  isPortrait={true}
  playFromPositionMillis={0}
/>
```

### react-native-video
1.  Abrir en Android Studio el archivo  **“build.gradle”**(app), lo encuentran dentro del panel izquierdo bajo la sección “Gradle Scripts” , en este archivo deben agregar dentro de las siguientes llaves

```
android {
	... // otro codigo se encuentra arriba
	compileOptions {
        	sourceCompatibility 1.8
        	targetCompatibility 1.8
    	}
}
```
1.  Guardar el archivo modificado y buscar el botón “Sync Project with Gradle Files” que se encuentra al lado del “AVD Manager”
2.  Esperar que termine de sincronizar nuevamente el proyecto y ejecutar el comando “react-native run-android”

Estos pasos fueron los únicos que me funcionaron para poder correr sin problemas la app junto a react-native-video instalada.

## Animaciones
Animated.timing recibe dos parámetros, el que vamos a cambiar y como vamos a cambiar
```
Animated.timing(
    this.state.opacy,
    {
        toValue: 1,
        duration: 1000,
    }
).start()
```

## Otras notas
### link
 Se utiliza el comando  `react-native link` para hacer el vínculo con android y iOS

### State
Solo para referencia, en la parte donde tienes la funcion  **playPause**, por lo que la documentacion de React dice, no deberias hacer un hacer referencia a una propiedad del state, dentro de un setState de esa manera:
```
playPause = () => {
	this.setState({
		paused: !this.state.paused
	})
}

```
`setState`  es asíncrono, y eso puede dar resultado raros, la manera correcta es pasando una funcion y retornando un objeto con el nuevo state:

```
playPause = () => {
	this.setState((oldState, oldProps) => {
		return {
			paused: !oldState.paused
		}
	})
}
```

### Realizacion de un separador
Se puede utilizar el mismo separador, solo pasandole por parametro horizontal, en caso de que se pase true, le agregas un marginHorizontal, de lo contrario, marginHorizontal: 0

```
...
<Separator horizontal />
...

Separator.js
<View
   style={[s.container,
   { borderColor: (props.color) ? props.color : '#EAEAEA',
     marginLeft: (props.horizontal) ? 10 : 0 }
   ]}
/>
```
