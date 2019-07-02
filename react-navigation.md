React Navigation
React Navigation es una librería que nos ayuda a hacer navegación en nuestras aplicaciones móviles.



Dimensions
react-native maneja un componente interno llamado Dimensions el cual te permite ajustar tu contenido a diferentes dispositivos, por ejemplo ;

Importamos los componentes necesarios.
`import { View,  Dimensions,  StlyleSheet } from 'react-native'`

Usamos el componente Dimensions y lo asignamos a las variables de ancho y alto

`let { height, width } = Dimensions.get('screen')`

Y aplicamos estos cambios sobre nuestros estilos
`
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
`
de esta forma puedes garantizar que el objeto que vas a renderizar sea una image, view, text se ajuste a las pantallas de los dispositivos.


watchman wtach-del-all para cuando aun borrando la cache no funciona
