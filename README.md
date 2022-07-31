# styled-components
## `ThemeProvider`
é utlizado para criar temas artisticas para nossos componenetes
- palette: define a paleta de cores
A baixo exemplo para aplica no mesmo projeto 
```js
import * as React from 'react';
import { Button } from '@material-ui/core';
import { ThemeProvider, createTheme } from '@material-ui/core';

function App() {
  const tema = createTheme({
    palette: {
      primary:{ // define uma cor primaria 
        main: '#f44336',
      },
      secondary:{ // defina uma cor secundaria
        main: '#00796b',
      }
    },
  });

  return (
    <ThemeProvider theme={tema}>
      {/**variant = ele é o tipo de botão  */}
      <Button variant='contained' color='secondary'> Olá Mundo</Button>
    </ThemeProvider>
  );
}
export default App;

```
## `ThemeProvider`
Podemos importa um estilo para todo os componentes que estiver dentro do *ThemeProvider*

- Precisamos ter o importe e a TAG ThemeProvider
- Depois é só colocar os componentes dentro dele que ira herda esse estilo
- Podemos definir o estilo para todos componentes atraves do atributo *theme* no arquivo index.js
```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';

import Home from './templates/App/Index';
import { GlobalStyles } from './styles/global-styles';
import { ThemeProvider } from 'styled-components'
import { theme } from './styles/theme';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <ThemeProvider  theme={theme}>
      <GlobalStyles/>
    </ThemeProvider>
  </React.StrictMode>
);
```
- Aqui esta o estilo que todos componentes estão recebendo do arquivo theme.js:

```jsx
export const theme = {
    colors: {
        mainBg: 'red',
        secondaryBg: 'pink',

    },
    fonts:{},
    spacings:{},
};
```
- E depois é só chamar o estilo nos arquivos que estão dentro da TAG no arquivo global-styles.js
```jsx
import { createGlobalStyle, css } from "styled-components";

export const GlobalStyles = createGlobalStyle`

    body{
        ${({theme}) => css`
            background:${theme.colors.mainBg} ;
        ` }
    }
`;
```

