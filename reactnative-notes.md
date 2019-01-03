# React Native
El componente View de react native funciona como un div mientras que el componente Text funciona como un párrafo.

Componentes en React Native

En react se arman componentes utilizando tags de html. En react native no tenemos un navegador, no son aplicaciones híbridas que corren en un pseudo navegador. React native crea aplicaciones nativas utilizando un bridge.

Componentes principales de react native

* View / ScrollView / SafeAreaView (Divs, scrolls)
* Text / TextInput (Formulario)
* Image / ImageBackground (Imágenes)
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

  import Image from'./image.png';
  <Imagesource={Image} />

Si es un ruta de internet lo agregarias con el uri:
  <Image source={{uri:'la url'}}/>

Nota:
Para opciones avanzadas del emulador:
adb shell input keyevent 82

Styles
Los estilos en React Native, se utilizan como en React, no es CSS convencional, las propiedades van con CamelCase, los valores de las propiedades pueden ser en números, si el valor es distinto como en el caso de porcentajes, rem o em, los valores van a ser strings y van entre comillas fontSize: ‘2.5rem’.
Tambien en el caso de que usemos colores en hexadecimales o un color como red o blue color: ‘#a1a1a1’.
