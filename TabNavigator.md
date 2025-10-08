# 📱 React Native + Expo + JavaScript: Базовая документация

# Глава: 2.

## 📚 1. Установка библиотек.

Для работы с навигационной панелью нам потребуется установить несколько библиотек:

```bash
npx expo install @react-navigation/native
```

```bash
npx expo install @react-navigation/bottom-tabs
```

```bash
npx expo install react-native-screens react-native-safe-area-context
```

> 💡 Эти команды добавят всё необходимое для работы навигации.

## 📑 2. Создание навигационной панели.

Сначала создадим новый файл под названием `_layout` - будет отвечать за расположение элементов (вкладок).
`_layout.js` или `index.js` - это обязательные названия файлов, Expo Router ищет именно их!

**Импортируем библиотеки:**

```JavaScript
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import { Text, View, StyleSheet } from 'react-native';
```

Пояснение:

- `createBottomTabNavigator` - функция, создающая навигатор с нижними вкладками.
- `Text, View, StyleSheet` - базовые компоненты React Native для отображения текста, контейнеров и стилей.

**Создадим саму навигационную панель:**

```JavaScript
const Tab = createBottomTabNavigator();
```

Создаётся объект `Tab`, содержащий два компонента:
- `Tab.Navigator` - общий контейнер.
- `Tab.Screen` - описание отдельного экрана.

**Преступаем к настройке:**

Создадим 1 вкладку для начала:

```JavaScript
export default function TabsLayout(){
    return(
        <tab.Navigator>
            <tab.Screen
                name = 'main'
                component={HomeScreen}
            />
        </tab.Navigator>
    );
}
```

Пояснение:

- `<tab.Navigator>` - общий контейнер, то - куда мы будем добавлять вкладки и что можно настраивать.
- `<tab.Screen/>` - описание самой вкладки (имя, иконка, размеры).
- `name` - Уникальное имя экрана. Должно соответствовать имени файла в папке `app/` (например, `main.js`).
- `component` - это свойство, которое указывает, какой React-компонент(экран или другими словами страницу) отображать при выборе этой вкладки.

### Сейчас код не работает, так как для `component` нужно видеть экран. React Navigation не знает, где лежат твои экраны — **ты должен явно указать, какой компонент показывать при выборе вкладки.** Это не Expo Router в чистом виде, а кастомная навигация, где ты сам управляешь экранами.

Поэтому укажем:

```JavaScript
import HomeScreen from './main';
```

Где:

- `HomeScreen` - моё название (вместо `main`) функции `expo default`.
- `./main` - название импортируемого файла через `./`.

Теперь можем придать вид вкладке с помощью `options = {{}}`:

```JavaScript
options={{
    title: "Главная",
    tabBarIcon: () => (
        <Text style = {{fontSize: 20}}>🏠</Text>
    ),
}}
```

> Это добавит название и иконку(размером: 20).

На данный момент у нас имеются 2 файла: `main.js` и `_layout.js`.
Теперь можем добавить остальные вкладки на любой вкус и цвет, для этого создадим ещё 4 файла: `schedule.js`, `theory.js`, `chat.js` и `profile.js`.
Они в себе будут располагать расписание, теорию, чат и профиль соответственно.
Загрузим в них тот же код, что и в `main.js`, только поменяем название функций `expo default` и текст в центре экрана.

**Расширим панель:**

> не забудь импортировать остальные экраны!

```JavaScript
export default function TabsLayout() {
    return (
        <Tab.Navigator>
            <Tab.Screen
                name='main'
                component={HomeScreen}
                options={{
                    title: "Главная",
                    tabBarIcon: () => (
                        <Text style={{ fontSize: 20 }}>🏠</Text>
                    ),
                }}
            />
            <Tab.Screen
                name="schedule"
                component={ScheduleScreen}
                options={{
                    title: "Расписание",
                    tabBarIcon: () => (
                        <Text style={{ fontSize: 20 }}>📅</Text>
                    ),
                }}
            />
            <Tab.Screen
                name="theory"
                component={TheoryScreen}
                options={{
                    title: "Теория",
                    tabBarIcon: () => (
                        <Text style={{ fontSize: 20 }}>📚</Text>
                    ),
                }}
            />
            <Tab.Screen
                name="chat"
                component={ChatScreen}
                options={{
                    title: "Чаты",
                    tabBarIcon: () => (
                        <Text style={{ fontSize: 20 }}>💬</Text>
                    ),
                }}
            />
            <Tab.Screen
                name="profile"
                component={ProfileScreen}
                options={{
                    title: "Профиль",
                    tabBarIcon: () => (
                        <Text style={{ fontSize: 20 }}>👤</Text>
                    ),
                }}
            />


        </Tab.Navigator>
    );
}
```

**Важно сопоставить правильный `name` и `component`!**

