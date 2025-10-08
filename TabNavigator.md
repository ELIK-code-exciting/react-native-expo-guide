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

Сначала создадим новый файл, у меня он называется `_layout` - будет отвечать за расположение элементов (вкладок).

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

