# ๐ป todo-react-native
### ๋ฆฌ์กํธ ๋ค์ดํฐ๋ธ๋ก ๊ฐ๋ฐ๋ ํฌ๋๋ฆฌ์คํธ ์ ์ฅ์

<br />

## ๐ฅ App View
<p align='center'>
    <img src='https://user-images.githubusercontent.com/64779472/113882665-76751400-97f8-11eb-8878-21d088c49af8.PNG' width="400" height="730">
</p>

<br />

## ๐จ๐ปโ๐ป ๊ธฐ์  ์คํ
1. React-Native
2. Styled-Components - styling
3. AsyncStorage
4. Google Material Design - icon

<br />
 
## ๐จ๐ปโ๐ป SafeAreaView, StatusBar Component
- SafeAreaView๋ ์์ดํฐ11๊ณผ ๊ฐ์ ๋ธ์น ๋์์ธ๋๋ฌธ์ ๊ฐ๋ ค์ง๋ ๋ฌธ์ ๋ฅผ ํด๊ฒฐํด ์ฃผ๋ ์ปดํฌ๋ํธ์ด๋ค.
- StatusBar๋ ์๋๋ก์ด๋ Title ์ปดํฌ๋ํธ๊ฐ ์ํ ๋ฐ(Status Bar)์ ๊ฐ๋ ค์ง๋ ๋ฌธ์ ๋ฅผ ํด๊ฒฐํด์ฃผ๋ ์ปดํฌ๋ํธ์ด๋ค.
- StatusBar์์ barStyle์ ํตํด ์ํ ๋ฐ์ ๋ด์ฉ์ ์์ ์์ ํ  ์ ์์ต๋๋ค.
- StatusBar์์ backgroundColor๋ ์๋๋ก์ด๋์์๋ง ์ ์ฉ๋๋ ์์ฑ์ด๋ฉฐ ์ํ ๋ฐ์ ๋ฐํ์์ ์์ ํ  ์ ์์ต๋๋ค.

```javascript
    //SageAreaView
    const Container = styled.SafeAreaView`
        (...)
    `;
```

```javascript
    //StatusBar
    import { StatusBar } from 'react-native';

    <StatusBar
        barStyle="light-content"
        backgroundColor={theme.background}
    />

```

<br />

## ๐จ๐ปโ๐ป Dimensions, useWindowDimensions
- Dimensions, useWindowDimensions ๋ชจ๋ ํ์ฌ ๊ธฐ๊ธฐ์ ํ๋ฉด ํฌ๊ธฐ๋ฅผ ์ ์ ์๊ณ , ์ด๋ฅผ ์ด์ฉํด ๋ค์ํ ํฌ๊ธฐ์ ๊ธฐ๊ธฐ์ ๋์ผํ ๋ชจ์ต์ผ๋ก ์ ์ฉ๋  ์ ์๋๋ก ์ฝ๋๋ฅผ ์์ฑํ  ์ ์๋ค.
- Dimensions๋ ์ฒ์ ๊ฐ์ ๋ฐ์์์ ๋์ ํฌ๊ธฐ๋ก ๊ณ ์ ๋๊ธฐ ๋๋ฌธ์ ๊ธฐ๊ธฐ๋ฅผ ํ์ ํด์ ํ๋ฉด์ด ์ ํ๋๋ฉด ๋ณํ๋ ํ๋ฉด์ ํฌ๊ธฐ๊ฐ ์ผ์นํ์ง ์๋ ๋ฌธ์ ๊ฐ ์๋ค.
- useWindowDimensions๋ ๋ฆฌ์กํธ ๋ค์ดํฐ๋ธ์์ ์ ๊ณตํ๋ Hooks์ค ํ๋๋ก, ํ๋ฉด์ ํฌ๊ธฐ๊ฐ ๋ณ๊ฒฝ๋๋ฉด ํ๋ฉด์ ํฌ๊ธฐ, ๋๋น ,๋์ด๋ฅผ ์๋์ผ๋ก ์๋ฐ์ดํธํ๋ค.

![1](https://user-images.githubusercontent.com/64779472/113824104-5888be80-97ba-11eb-88dc-2b4f1c41bd9f.PNG)

```javascript
    //Dimensions
    import { Dimensions } from 'react-native';

    const Input = () => {
        const width = Dimensions.get('window').width;

        return <StyledInput width={width} />
    }
```

```javascript
    //useWindowDimensions
    import { useWindowDimensions } from 'react-native';

    const Input = () => {
        const width = useWindowDimensions().width;

        return <StyledInput width={width} />
    }
```

<br />

## ๐จ๐ปโ๐ป TextInput ์์ฑ
- autoCapitalize: ์๋์ผ๋ก ๋๋ฌธ์ ์ ํ(iOS)
- autoCorrect: ์๋ ์์  ๊ธฐ๋ฅ(iOS)
- returnKeyType: ํค๋ณด๋์ ์๋ฃ ๋ฒํผ ์ค์ (iOS)
- keyboardApperance: ํค๋ณด๋ ์ ์ค์ (iOS)

```javascript
    <StyledInput 
        width={width} 
        placeholder={placeholder} 
        maxLength={50}
        autoCapitalize='none' //์๋ ๋๋ฌธ์ ๋ณํ ๋์X
        autoCorrect={false} //์๋ ์์  ๊ธฐ๋ฅ ๋์X
        returnKeyType='done' //ํค๋ณด๋์ ์๋ฃ ๋ฒํผ 'done'
        keyboardApperance='dark' //ํค๋ณด๋์ ์
    />
```
<br />

## ๐จ๐ปโ๐ป Google Material Design
๐ https://material.io/resources/icons/?style=baseline

![2](https://user-images.githubusercontent.com/64779472/113828270-2b8ada80-97bf-11eb-8341-724f9b55296f.PNG)

- ํ๋ก์ ํธ์ ์ฌ์ฉํ  ์์ด์ฝ ์ด๋ฏธ์ง๋ฅผ ๋ค์ด๋ฐ์ ์ ์์ต๋๋ค.
- iOS๋ก ๋ค์ด๋ฐ์ผ๋ฉด x2, x3 ์ฌ์ด์ง์ ์์ด์ฝ์ด ํจ๊ป ์์ต๋๋ค.
- ํ์ผ๋ช์ ๋์ผํ ์ด๋ฆ์ ์ฌ์ฉํ๋ฉด์ @2x, @3x๋ฅผ ๋ถ์ด๋ฉด ๋ฆฌ์กํธ ๋ค์ดํฐ๋ธ์์ ํ๋ฉด ์ฌ์ด์ฆ์ ์๋ง์ ํฌ๊ธฐ์ ์ด๋ฏธ์ง๋ฅผ ์๋์ผ๋ก ๋ถ๋ฌ์ ์ฌ์ฉํ  ์ ์์ต๋๋ค.

<br />

## ๐จ๐ปโ๐ป Image, IconButton Component
- Image Component๋ ๋ฆฌ์กํธ ๋ค์ดํฐ๋ธ์์ ์ ๊ณตํ๋ ์ปดํฌ๋ํธ์ด๋ฉฐ, ํ๋ก์ ํธ์ ์๋ ์ด๋ฏธ์ง ํ์ผ์ ๊ฒฝ๋ก๋ URL์ ์ด์ฉํ์ฌ ์๊ฒฉ์ ์๋ ์ด๋ฏธ์ง๋ฅผ ๋ ๋๋งํ  ์ ์์ต๋๋ค.
- tint-color๋ฅผ ํตํด ์์ด์ฝ์ ์๊น์ ์ค ์ ์๋ค.

```javascript
    const Icon = styled.Image`
        tint-color: ${({theme}) => theme.text};
        width: 30px;
        height: 30px;
        margin: 10px;
    `;

    const IconButton = ({ type, onPressOut }) => {
        return (
            <TouchableOpacity onPressOut={onPressOut}>
                <Icon source={type} />
            </TouchableOpacity>
        );
    };

    IconButton.propTypes = {
        // PropTypes.oneOf: ์ด๊ฑฐํ(enum)์ผ๋ก ์ฒ๋ฆฌํ์ฌ prop๊ฐ ํน์  ๊ฐ๋ค๋ก ์ ํ๋๋๋ก ํ  ์ ์์ต๋๋ค.
        type: PropTypes.oneOf(Object.values(images)).isRequired,
        onPressOut: PropTypes.func,
    }
```

<br />

## ๐จ๐ปโ๐ป ThemeProvider
- ๋ชจ๋  ์ปดํฌ๋ํธ๋ฅผ ๊ฐ์ธ๋ ์ต์์ ์ปดํฌ๋ํธ๋ก ThemeProvider ์ปดํฌ๋ํธ๋ฅผ ์ฌ์ฉํ๋ฉฐ, ThemeProvider ์ปดํฌ๋ํธ์ theme ์์ฑ์ ์์์ ์ ์ํ ์์ ์ค์ ํ๋ฉด, ThemeProvider ์ปดํฌ๋ํธ์ ์์ ์ปดํฌ๋ํธ์์๋ ์คํ์ผ๋ ์ปดํฌ๋ํธ๋ฅผ ์ด์ฉํ  ๋, props๋ก theme๋ฅผ ์ ๋ฌ๋ฐ์ ์ด์ฉํ  ์ ์๋ค.

```javascript
    <ThemeProvider theme={theme}>
        <Container>
            (...)
        </Container>
    </ThemeProvider>
```

<br />

## ๐จ๐ปโ๐ป CRUD ๋ฉ์๋ ๊ตฌํ
### ๐ _addTask
```javascript
    const _addTask = () => {
        const ID = Date.now().toString();
        const newTaskObject = {
            [ID]: { id: ID, text: newTask, completed: false},
        }
        alert(`Add: ${newTask}`);
        setNewTask('');
        setTasks({...tasks, ...newTaskObject});
    };
```

<br />

### ๐ _deleteTask
```javascript
    const _deleteTask = id => {
        // Object.assign ๋ฉ์๋๋ ์ด๊ฑฐํ  ์ ์๋ ํ๋ ์ด์์ ์ถ์ฒ ๊ฐ์ฒด๋ก๋ถํฐ ๋์ ๊ฐ์ฒด๋ก ์์ฑ์ ๋ณต์ฌํ  ๋ ์ฌ์ฉ
        const currentTasks = Object.assign({}, tasks);
        delete currentTasks[id];
        setTasks(currentTasks);
    };
```

<br />

### ๐ _toggleTask
```javascript
    const _toggleTask = id => {
        const currentTasks = Object.assign({}, tasks); 
        currentTasks[id]['completed'] = !currentTasks[id]['completed'];
        setTasks(currentTasks);
    };
```

<br />

### ๐ _updateTask
```javascript
    const _updateTask = item => {
        const currentTasks = Object.assign({}, tasks);
        currentTasks[item.id] = item;
        setTasks(currentTasks);
    }
```

<br />

## ๐จ๐ปโ๐ป ๋ถ๊ฐ ๊ธฐ๋ฅ
### ๐ AsyncStorage
- ๋ฆฌ์กํธ ๋ค์ดํฐ๋ธ์์๋ AsyncStorage๋ฅผ ์ด์ฉํด ๋ก์ปฌ์ ๋ฐ์ดํฐ๋ฅผ ์ ์ฅํ๊ณ  ๋ถ๋ฌ์ค๋ ๊ธฐ๋ฅ์ ๊ตฌํํ  ์ ์๋ค.
- AsyncStorage๋ ๋น๋๊ธฐ๋ก ๋์ํ๋ฉฐ ๋ฌธ์์ด๋ก ๋ ํค-๊ฐ(Key-Value) ํํ์ ๋ฐ์ดํฐ๋ฅผ ๊ธฐ๊ธฐ์ ์ ์ฅํ๊ณ  ๋ถ๋ฌ์ฌ ์ ์๋ ๊ธฐ๋ฅ์ ์ ๊ณตํ๋ค.
- expo install์ npm install๊ณผ ๊ฑฐ์ ๋์ผํ ์ญํ ์ ํ๋ค. ์ฐจ์ด์ ์ ์ฌ์ฉ์ค์ธ Expo SDK ๋ฒ์ ๊ณผ ํธํ๋๋ ๋ฒ์ ์ด ์๋์ง ํ์ธํ๊ณ , ํด๋น ๋ฒ์ ์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ฅผ ์ค์นํ๋ ๊ณผ์ ์ด ์ถ๊ฐ๋์๋ค.

```javascript
    //intall ์์  ์ 
    expo install @react-native-community/async-storage

    //install ์์  ํ
    expo install @react-native-async-storage/async-storage

    //import
    import AsyncStorage from '@react-native-async-storage/async-storage';

    //๋ฐ์ดํฐ ๋ด๊ธฐ
    const _saveTasks = async tasks => {
        try {
            await AsyncStorage.setItem('tasks', JSON.stringify(tasks));
            setTasks(tasks);
        } catch (e) {
            console.error(e);
        }
    }

    //๋ฐ์ดํฐ ๋ถ๋ฌ์ค๊ธฐ
    const _loadTasks = async () => {
        const loadedTasks = await AsyncStorage.getItem('tasks');
        setTasks(JSON.parse(loadedTasks || {}));
    };
```

<br />

### ๐ AppLoading
- AppLoading ์ปดํฌ๋ํธ๋ ํน์  ์กฐ๊ฑด์์ ๋ก๋ฉ ํ๋ฉด์ด ์ ์ง๋๋๋ก ํ๋ ๊ธฐ๋ฅ์ผ๋ก, ๋ ๋๋ง ํ๊ธฐ ์ ์ ์ฒ๋ฆฌํด์ผ ํ๋ ์์์ ์ํํ๋ ๋ฐ ์ ์ฉํ๊ฒ ์ฌ์ฉ๋๋ค.
    1. startAsync: AppLoading ์ปดํฌ๋ํธ๊ฐ ๋์ํ๋ ๋์ ์คํ ๋  ํจ์
    2. onFinish: startAsync๊ฐ ์๋ฃ๋๋ฉด ์คํํ  ํจ์
    3. onError: startAsync์์ ์ค๋ฅ๊ฐ ๋ฐ์ํ๋ฉด ์คํํ  ํจ์

```javascript
    //install
    expo install expo-app-loading

    //import
    import AppLoading from 'expo-app-loading';

    //AppLoading ์์
    <AppLoading 
        startAsync={_loadTasks}
        onFinish={() => setIsReady(true)}
        onError={console.error}
    />
```

<br />

### ๐ app.json
- ๋ก๋ฉ ํ๋ฉด, ์์ด์ฝ์ app.json์์ ๋ฐ๊ฟ ์ ์๋ค.
- ๋ก๋ฉ ํ๋ฉด์ผ๋ก ์ฌ์ฉ ๋  ์ด๋ฏธ์ง์ ํฌ๊ธฐ๋ ๋ค์ํ ๊ธฐ๊ธฐ์ ๋์ํ๊ธฐ ์ํด 1242 x 2436์ผ๋ก ์ค๋นํ๋ ๊ฒ์ด ์ข๋ค.
- ๋ก๋ฉ ํ๋ฉด์์ ๊ธฐ๊ธฐ์ ํฌ๊ธฐ์ ๋ฐ๋ผ ๊ณต๋ฐฑ์ด ์๊ธฐ๋ ๊ฒฝ์ฐ, resizeMode์ ๊ฐ์ cover๋ก ๋ณ๊ฒฝํ๊ฑฐ๋, backgroundColor์ ๊ฐ์ ๋ณ๊ฒฝํ๋ฉด ๋๋ค.
- ์์ด์ฝ์ผ๋ก ์ฌ์ฉ ๋  ์ด๋ฏธ์ง๋ iOS์ ๊ฒฝ์ฐ 1024 x 1024 ํฌ๊ธฐ๊ฐ ํ์ํ๊ณ  ์๋๋ก์ด๋์ ๊ฒฝ์ฐ 512 x 512ํฌ๊ธฐ์ ์ด๋ฏธ์ง๊ฐ ํ์ํ๋ฏ๋ก, ์ฌ๋งํ๋ฉด 1024 x 1024 ํฌ๊ธฐ์ ์ด๋ฏธ์ง๋ฅผ ์ฌ์ฉํ๋๊ฒ ์ข๋ค.

```json
{
    "expo": {
        //(...์๋ต)
        "icon": "./assets/splash.png",
        "splash": {
            "image": "./assets/splash.png",
            "resizeMode": "contain",
            "backgroundColor": "#ffffff"
        },
        //(...์๋ต)
        "android": {
            "adaptiveIcon": {
                "foregroundImage": "./assets/splash.png",
                "backgroundColor": "#FFFFFF"
            }
        },
        //(...์๋ต)
    }
}
```

<br>

### ๐ช๐ป ๋ด๊ฐ ์ถ๊ฐํ ๊ธฐ๋ฅ

* ์์  ์์ด์ฝ ํด๋ฆญ์ ์์  ์ํ๋ก ์ง์ํ๋ ์์  ์ธํ์ผ๋ก ๋ฐ๋ก ํฌ์ปค์ฑ ๋์ง ์๋ ๋ฌธ์  ๋ฐ๊ฒฌ.

   -> useEffect์ useRef๋ฅผ ์ฌ์ฉํ์ฌ ์์  ์์ด์ฝ ํด๋ฆญ์ ์์  ์ธํ์ฐฝ์ผ๋ก ๋ฐ๋ก ํฌ์ปค์ฑ ๋๋๋ก ๊ธฐ๋ฅ ์ถ๊ฐ


* src/components/Input.js ํ์ผ ์์ 
```js
const refInput = useRef(null); // ์ฐธ์กฐํ  ๋ ํผ๋ฐ์ค ์ ์ธ

// Input ์ปดํฌ๋ํธ ์คํ์ value๊ฐ ์๋ค๋ฉด ํฌ์ปค์ฑ์ Input ์ปดํฌ๋ํธ์ ๋๋ค.
// ์ฆ, ์์  ์ธํ์ผ ๊ฒฝ์ฐ ๋ฐ๋ก ํฌ์ปค์ฑ๋์ด ํค๋ณด๋ ์ํ์ด ๋ฑ์ฅํ๋ค.
useEffect(() => {
  if (value.length > 0) refInput.current.focus();
}, []);

return (
  <StyledInput
    ref={refInput} // ์ฐธ์กฐํ  ๋ ํผ๋ฐ์ค ์ง์ 
  />
);
```

<br>


### โ๐ป ๊ณต๋ถํ ์ฑ

* ์ฒ์ ๋ฐฐ์ฐ๋ ๋ฆฌ์กํธ ๋ค์ดํฐ๋ธ : ํฌ๋ก์ค ํ๋ซํผ ์ฑ ๊ฐ๋ฐ์ ์ํ ์ค์  ์๋ฌธ์

