# Tarefandoo - TODO List
Descrição... API

## 1. Criando:
**No terminal:**
- [x] Criando o app: `npx create-expo-app todolist`
- [x] Abrindo o diretório do arquivo: `cd todolist`
- [x] Instalando dependências pro Expo: `npx expo install react-dom react-native-web @expo/webpack-config`
- [x] Instalando o Axios: `npm install axios`
- [x] Rodando: `npx expo start` ou `npx expo start --tunnel`

## 2. Assets e fonte:

### 1.2. Adicionando os assets

**Dentro do diretório do app:**
-  [x] Criar a pasta `src` 
-  [x] Criar a pasta `assets` em `/src` 
-  [x] Colocar as imagens do projeto em `/assets` 

### 2.2. Adicionando a fonte

**No terminal:**
- [x] Instalando a fonte Inter: `npx expo install expo-font @expo-google-fonts/inter`

**Dentro do diretório do app em `App.js`:**
- [x] Importar a fonte no arquivo: 
```js
import {
  useFonts, 
  Inter_400Regular
} from '@expo-google-fonts/inter'
```

- [x] Carregando a fonte no início da função `App`: 
```js
  const  [fontsLoaded] = useFonts({
    Inter_400Regular
  })
```

- [x] Adicionar o componente `ActivityIndicator` nos imports do react native:
```js
import { StyleSheet, Text, View, ActivityIndicator } from 'react-native';
                              // componente do react native para spinner
```

-  [x] Verificar se as fontes carregaram ou não:
 > Dentro de View
```js
{/* se as fontes foram carregadas */}
{fontsLoaded ? ( 
  <Text>Carregou!</Text>
) : (
  // se não foi carregado
  <ActivityIndicator size={50} />
)}
```

## 3. Tema, Home e Loading

### 3.1. Definindo o tema
**Dentro do diretório do app:**
- [x] Criar a pasta `theme` em `/src` 
- [x] Criar o arquivo `index.js` em `/theme`
- [x] Adicionar as cores, tamanhos e fonte do tema no `styles.js`:
```js
export const theme = {
    colors: {
        base: {
            ghost_white: '#F3F1F9',
            dark_blue_black: '#0C1B33',
            alice_blue: '#DFE8F7',
            white: '#ffffff'
        },
        brand: {
            purple_yam: '#8E7CC3',
            naples_yellow: '#F9DD62',
            byzantium: '#7A0064',
        }
    },
    font_family: {
        regular: 'Inter_400Regular'
    },
    font_size: {
        xl: 25,
        lg: 22,
        md: 20,
        sm: 18,
        xs: 16
    }
}
```

- [x]  Importando o `theme` no `App.js`:
```js
import { theme } from './src/theme'
```

- [x] Mudando o `backgroundColor` para a cor `ghost_white`:
```js
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: theme.colors.base.ghost_white,
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

### 3.2. Criando a tela Home
**Dentro do diretório do app:**
- [x] Criar a pasta `screens` em `/src`
- [x] Criar o arquivo `index.js` e `styles.js` em `/screens`
- [x] Importar o componente `StyleSheet` do react native no `styles.js`:
```js
import { StyleSheet } from 'react-native'
```
- [x] Importar o tema:
```js
import { theme } from '../theme'
```
- [x] Para estilizar:
```js
// criando  a estilização do componente de acordo com as informações passadas por parâmetro.
export const styles = StyleSheet.create({
    container: {
        flex: 1,
        backgroundColor: theme.colors.base.ghost_white,
        alignItems: 'center', // centralizar os itens do container
        justifyContent: 'center' // distribuir os itens do container
    },
    // titulo
    title: {
        color: theme.colors.base.dark_blue_black, // cor da fonte
        fontFamily: theme.font_family.regular, // fonte
        fontSize: theme.font_size.lg // tamanho da fonte
    }
})
```

- [x] Importar o `View` e o `Text` do react native no `index.js`:
```js
import { View, Text } from 'react-native'
```

- [x] Importar a estilização:
```js
import { styles } from './styles'
```

- [x]  Criando a tela Home:
```js
export function HomeScreen() {
   // criar uma view que será a "container" principal
               // estilos da tela home
   return (
      <View style={styles.container}>
         <Text style={styles.title}>Home</Text> 
   </View>
   )
}
```

- [x] Alterar o `Text` para a `HomeScreen` dentro de `App.js`
```js
  return (
    <View style={styles.container}>
      {/* se as fontes foram carregadas */}
      {fontsLoaded ? ( 
        <HomeScreen />
      ) : (
        // se não foi carregado
        <ActivityIndicator size={50} />  // spinner 
      )}
      <StatusBar style="auto" />
    </View>
  )
```

### 3.3. Criando o componente loading
- [x] Criar a pasta `components` em `/src` 
- [x] Criar a pasta `Loading` em `/components` 
- [x] Criar o arquivo `index.js` e `styles.js` em `/Loading`

- [x] Estilizar o loading em `styles.js`:
```js
import { StyleSheet } from 'react-native'
import { theme } from '../../theme'

// criando  a estilização do componente de acordo com as informações passadas por parâmetro.
export const styles = StyleSheet.create({
    container: {
        flex: 1,
        backgroundColor: theme.colors.base.ghost_white,
        alignItems: 'center', // centralizar os itens do container
        justifyContent: 'center' //  distribuir os itens do container
    },
})
```

- [x]  Adicionar o ActivityIndicator ao Loading em `index.js`:
```js
import { View, ActivityIndicator } from 'react-native'
import { styles } from './styles'
import { theme } from '../../theme'

// criando o loading
export function Loading() {
    return (
        <View style={styles.container}>
            <ActivityIndicator size={50} color={theme.colors.brand.purple_yam}/>
            {/* spinner */}              {/* cor do tema */}
        </View>
    )
}
```

- [x] Importar o `Loading` em `App.js`:
```js
// Spinner
import { Loading } from './src/components/Loading'
```

- [x] Substituir o `ActivityIndicator` da função `App` pelo `Loading`:
```js
  return (
    <View style={styles.container}>
      {/* se as fontes foram carregadas */}
      {fontsLoaded ? ( 
        <HomeScreen />
      ) : (
        // se não foi carregado
        <Loading />  // spinner
      )}
      <StatusBar style="auto" />
    </View>
  )
```
- [x] Apagar o `styles`
- [x] Remover a `View`:
```js
  return (
    <>
      {/* ? -> se as fontes foram carregadas | : -> se não foram*/}
      {fontsLoaded ? <HomeScreen /> : <Loading />}
      <StatusBar style="auto" />
    </>
  )
```

## 4. Header

### 4.1. Desenvolvendo o Header
**Dentro do diretório do app:**
- [x] Criar a pasta `Header` em `/components` 
- [x] Criar o arquivo `index.js` e `styles.js` em `/Header`

- [x] Estilizar o header em `styles.js`:
```js
import { StyleSheet } from 'react-native'
import { theme } from '../../theme'

// criando  a estilização do componente de acordo com as informações passadas por parâmetro.
export const styles = StyleSheet.create({
    headerContainer: {
        backgroundColor: theme.colors.brand.purple_yam,
        alignItems: 'center', // centralizar os itens do container
        justifyContent: 'center', //  distribuir os itens do container
        width: '100%', // largura
        height: 173, // altura
    },
})
```

- [x] Criar o componente Header em `index.js`:
```js
import { View } from 'react-native'
import { styles } from './styles'

// criando o header
export function Header() {
    return (
        <View style={styles.headerContainer}/>
    )
}
```

- [x] Importar o `Header` e substituir o `Text` em `/screens`:
```js
import { Header } from '../components/Header'

// criando a tela Home
export function HomeScreen() {
   // criar uma view que será a "container" principal
   return (       // estilos da tela home
      <View style={styles.container}>
         <Header />
      </View>
   )
}
```

- [x] Alterar o objeto `container` do `styles.js` em `/screens`:
```js 
    container: {
        flex: 1,
        backgroundColor: theme.colors.base.ghost_white,
    },
```

### 4.2. Adiconando imagens estáticas

- [x] Importar o logo no `index.js` em `/Header`:
```js
import TAREFANDOO from '../../assets/TAREFANDOO.png'
```

- [x] Adicionar a imagem do logo na `View` dentro da função `Header`:
```js
<Image source={TAREFANDOO} style={{height: '5rem', width: '23.875rem'}}/>
                                {/* definindo os tamanhos do logo */}
```



##
**Google Drive**
- The file 
	> Before starting to sync files, you must link an account in the **Synchronize** sub-menu.

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```


|                |ASCII                          |HTML                         |
|----------------|-------------------------------|-----------------------------|
|Single backticks|`'Isn't this fun?'`            |'Isn't this fun?'            |


