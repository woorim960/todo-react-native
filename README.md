# 💻 todo-react-native
### 리액트 네이티브로 개발된 투두리스트 저장소

<br />

## 🎥 App View
<p align='center'>
    <img src='https://user-images.githubusercontent.com/64779472/113882665-76751400-97f8-11eb-8878-21d088c49af8.PNG' width="400" height="730">
</p>

<br />

## 👨🏻‍💻 기술 스텍
1. React-Native
2. Styled-Components - styling
3. AsyncStorage
4. Google Material Design - icon

<br />
 
## 👨🏻‍💻 SafeAreaView, StatusBar Component
- SafeAreaView는 아이폰11과 같은 노치 디자인때문에 가려지는 문제를 해결해 주는 컴포넌트이다.
- StatusBar는 안드로이드 Title 컴포넌트가 상태 바(Status Bar)에 가려지는 문제를 해결해주는 컴포넌트이다.
- StatusBar에서 barStyle을 통해 상태 바의 내용의 색을 수정할 수 있습니다.
- StatusBar에서 backgroundColor는 안드로이드에서만 적용되는 속성이며 상태 바의 바탕색을 수정할 수 있습니다.

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

## 👨🏻‍💻 Dimensions, useWindowDimensions
- Dimensions, useWindowDimensions 모두 현재 기기의 화면 크기를 알 수 있고, 이를 이용해 다양한 크기의 기기에 동일한 모습으로 적용될 수 있도록 코드를 작성할 수 있다.
- Dimensions는 처음 값을 받아왔을 때의 크기로 고정되기 때문에 기기를 회전해서 화면이 전환되면 변화된 화면의 크기가 일치하지 않는 문제가 있다.
- useWindowDimensions는 리액트 네이티브에서 제공하는 Hooks중 하나로, 화면의 크기가 변경되면 화면의 크기, 너비 ,높이를 자동으로 업데이트한다.

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

## 👨🏻‍💻 TextInput 속성
- autoCapitalize: 자동으로 대문자 전환(iOS)
- autoCorrect: 자동 수정 기능(iOS)
- returnKeyType: 키보드의 완료 버튼 설정(iOS)
- keyboardApperance: 키보드 색 설정(iOS)

```javascript
    <StyledInput 
        width={width} 
        placeholder={placeholder} 
        maxLength={50}
        autoCapitalize='none' //자동 대문자 변환 동작X
        autoCorrect={false} //자동 수정 기능 동작X
        returnKeyType='done' //키보드의 완료 버튼 'done'
        keyboardApperance='dark' //키보드의 색
    />
```
<br />

## 👨🏻‍💻 Google Material Design
🔖 https://material.io/resources/icons/?style=baseline

![2](https://user-images.githubusercontent.com/64779472/113828270-2b8ada80-97bf-11eb-8341-724f9b55296f.PNG)

- 프로젝트에 사용할 아이콘 이미지를 다운받을 수 있습니다.
- iOS로 다운받으면 x2, x3 사이지의 아이콘이 함께 있습니다.
- 파일명을 동일한 이름을 사용하면서 @2x, @3x를 붙이면 리액트 네이티브에서 화면 사이즈에 알맞은 크기의 이미지를 자동으로 불러와 사용할 수 있습니다.

<br />

## 👨🏻‍💻 Image, IconButton Component
- Image Component는 리액트 네이티브에서 제공하는 컴포넌트이며, 프로젝트에 있는 이미지 파일의 경로나 URL을 이용하여 원격에 있는 이미지를 렌더링할 수 있습니다.
- tint-color를 통해 아이콘에 색깔을 줄 수 있다.

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
        // PropTypes.oneOf: 열거형(enum)으로 처리하여 prop가 특정 값들로 제한되도록 할 수 있습니다.
        type: PropTypes.oneOf(Object.values(images)).isRequired,
        onPressOut: PropTypes.func,
    }
```

<br />

## 👨🏻‍💻 ThemeProvider
- 모든 컴포넌트를 감싸는 최상위 컴포넌트로 ThemeProvider 컴포넌트를 사용하며, ThemeProvider 컴포넌트의 theme 속성에 앞에서 정의한 색을 설정하면, ThemeProvider 컴포넌트의 자식 컴포넌트에서는 스타일드 컴포넌트를 이용할 때, props로 theme를 전달받아 이용할 수 있다.

```javascript
    <ThemeProvider theme={theme}>
        <Container>
            (...)
        </Container>
    </ThemeProvider>
```

<br />

## 👨🏻‍💻 CRUD 메서드 구현
### 🏃 _addTask
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

### 🏃 _deleteTask
```javascript
    const _deleteTask = id => {
        // Object.assign 메소드는 열거할 수 있는 하나 이상의 출처 객체로부터 대상 객체로 속성을 복사할 때 사용
        const currentTasks = Object.assign({}, tasks);
        delete currentTasks[id];
        setTasks(currentTasks);
    };
```

<br />

### 🏃 _toggleTask
```javascript
    const _toggleTask = id => {
        const currentTasks = Object.assign({}, tasks); 
        currentTasks[id]['completed'] = !currentTasks[id]['completed'];
        setTasks(currentTasks);
    };
```

<br />

### 🏃 _updateTask
```javascript
    const _updateTask = item => {
        const currentTasks = Object.assign({}, tasks);
        currentTasks[item.id] = item;
        setTasks(currentTasks);
    }
```

<br />

## 👨🏻‍💻 부가 기능
### 🏃 AsyncStorage
- 리액트 네이티브에서는 AsyncStorage를 이용해 로컬에 데이터를 저장하고 불러오는 기능을 구현할 수 있다.
- AsyncStorage는 비동기로 동작하며 문자열로 된 키-값(Key-Value) 형태의 데이터를 기기에 저장하고 불러올 수 있는 기능을 제공한다.
- expo install은 npm install과 거의 동일한 역할을 한다. 차이점은 사용중인 Expo SDK 버전과 호환되는 버전이 있는지 확인하고, 해당 버전의 라이브러리를 설치하는 과정이 추가되었다.

```javascript
    //intall 수정 전
    expo install @react-native-community/async-storage

    //install 수정 후
    expo install @react-native-async-storage/async-storage

    //import
    import AsyncStorage from '@react-native-async-storage/async-storage';

    //데이터 담기
    const _saveTasks = async tasks => {
        try {
            await AsyncStorage.setItem('tasks', JSON.stringify(tasks));
            setTasks(tasks);
        } catch (e) {
            console.error(e);
        }
    }

    //데이터 불러오기
    const _loadTasks = async () => {
        const loadedTasks = await AsyncStorage.getItem('tasks');
        setTasks(JSON.parse(loadedTasks || {}));
    };
```

<br />

### 🏃 AppLoading
- AppLoading 컴포넌트는 특정 조건에서 로딩 화면이 유지되도록 하는 기능으로, 렌더링 하기 전에 처리해야 하는 작업을 수행하는 데 유용하게 사용된다.
    1. startAsync: AppLoading 컴포넌트가 동작하는 동안 실행 될 함수
    2. onFinish: startAsync가 완료되면 실행할 함수
    3. onError: startAsync에서 오류가 발생하면 실행할 함수

```javascript
    //install
    expo install expo-app-loading

    //import
    import AppLoading from 'expo-app-loading';

    //AppLoading 예시
    <AppLoading 
        startAsync={_loadTasks}
        onFinish={() => setIsReady(true)}
        onError={console.error}
    />
```

<br />

### 🏃 app.json
- 로딩 화면, 아이콘을 app.json에서 바꿀 수 있다.
- 로딩 화면으로 사용 될 이미지의 크기는 다양한 기기에 대응하기 위해 1242 x 2436으로 준비하는 것이 좋다.
- 로딩 화면에서 기기의 크기에 따라 공백이 생기는 경우, resizeMode의 값을 cover로 변경하거나, backgroundColor의 값을 변경하면 된다.
- 아이콘으로 사용 될 이미지는 iOS의 경우 1024 x 1024 크기가 필요하고 안드로이드의 경우 512 x 512크기의 이미지가 필요하므로, 웬만하면 1024 x 1024 크기의 이미지를 사용하는게 좋다.

```json
{
    "expo": {
        //(...생략)
        "icon": "./assets/splash.png",
        "splash": {
            "image": "./assets/splash.png",
            "resizeMode": "contain",
            "backgroundColor": "#ffffff"
        },
        //(...생략)
        "android": {
            "adaptiveIcon": {
                "foregroundImage": "./assets/splash.png",
                "backgroundColor": "#FFFFFF"
            }
        },
        //(...생략)
    }
}
```


### 💪🏻 내가 추가한 기능

* 수정 아이콘 클릭시 수정 상태로 진입하나 수정 인풋으로 바로 포커싱 되지 않는 문제 발견.

   -> useEffect와 useRef를 사용하여 수정 아이콘 클릭시 수정 인풋창으로 바로 포커싱 되도록 기능 추가


* src/components/Input.js 파일 수정
```js
const refInput = useRef(null); // 참조할 레퍼런스 선언

// Input 컴포넌트 실행시 value가 있다면 포커싱을 Input 컴포넌트에 둔다.
// 즉, 수정 인풋일 경우 바로 포커싱되어 키보드 자판이 등장한다.
useEffect(() => {
  if (value.length > 0) refInput.current.focus();
}, []);

return (
  <StyledInput
    ref={refInput} // 참조할 레퍼런스 지정
  />
);
```

<br>


### ✍🏻 공부한 책

* 처음 배우는 리액트 네이티브 : 크로스 플랫폼 앱 개발을 위한 실전 입문서

