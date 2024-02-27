Node version: v20.11.1
Npm version: 10.2.4

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

ATTTENTICION:

- [x] Adicionar o componente `ActivityIndicator` nos imports do react native:
```js
import { StyleSheet, Text, View, ActivityIndicator } from 'react-native';
                              // componente do react native para spinner
```

-  [x] Verificar se as fontes carregaram ou não:
 > Dentro de View
```js
{/* se as fontes não foram carregadas */}
{fontsLoaded ? ( 
    <ActivityIndicator size={50} />  
) : (
    // se foi carregado
    <Text>Carregou</Text>
  )}
}
```