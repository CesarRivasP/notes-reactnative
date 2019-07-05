React Navigation
React Navigation es una librería que nos ayuda a hacer navegación en nuestras aplicaciones móviles.


## Otros Apuntes
### Dimensions
react-native maneja un componente interno llamado Dimensions el cual te permite ajustar tu contenido a diferentes dispositivos, por ejemplo ;

Importamos los componentes necesarios.
`import { View,  Dimensions,  StlyleSheet } from 'react-native'`

Usamos el componente Dimensions y lo asignamos a las variables de ancho y alto

`let { height, width } = Dimensions.get('screen')`

Y aplicamos estos cambios sobre nuestros estilos
```
class IndexScreen extends Component{

    render(){
        return(
            <Viewstyle={styles.container}>
		<Viewstyle={subContainer}></View>
            </View>
        )
    }
}
const styles = StyleSheet.create({
    container:{
        flex:1,
        backgroundColor:'#0D5F99',
        alignItems: 'flex-start',
        justifyContent:'flex-start',
   	 },
			subContainer:{
				height:height,
				width:width,
				backgroundColor:'deeppink'
		 }
})
export default IndexScreen
```
De esta forma puedes garantizar que el objeto que vas a renderizar sea una image, view, text se ajuste a las pantallas de los dispositivos.

### Uso de botones
* Se puede usar el componente button o toachableOpacity



El metodo navigate() de navigation nos lleva a otra pantalla dada la ruta que le especificamos
```
handlePress = () => {
  this.props.navigation.navigate('Home')
}
```
La prop navigation se manda a cada ruta/componente/pantalla que definimos en el StackNavigator


### Resolucion de errores
Para cuando aun borrando la cache, no hay cambios en el problema con watchman
`watchman watch-del-all`

### Ante el error 'Unable to load script from assets 'index.android.bundle'
- Primero, en la carpeta android ejecuta: `./gradlew clean`
- Crear la carpeta assets en `android/app/src/main/`
- Ingresa en la terminal
`react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res`
- Ya puedes correr la aplicación
`react-native run-android`
**Nota**:
- Si al correr la aplicación, ésta no se mantiene en ejecución, ingresa: `watchman watch-del-all && watchman shutdown-server`
