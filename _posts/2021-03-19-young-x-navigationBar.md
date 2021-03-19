---
layout: post
title: "[청춘서] 탭 내비게이션 만들기(1)"
subtitle : BottomNavigation 오류 발생
tags: [청춘서, React Native]
author: Saerom Kwon
comments : True
---

{% highlight python %}
import React from 'react';
import styled from 'styled-components/native';

const Container = styled.View`
    flex: 1;
    justify-content: center;
    align-items: center;
`;
const StyledText = styled.Text`
    font-size: 30px;
`;

export const Home = () => {
    return (
        <Container>
            <StyledText>Home</StyledText>
            <StyledText>Calendar</StyledText>
        </Container>
    );
};
{% endhighlight %}

<br>

위의 코드와 같이 탭화면을 구성한다. export하여 Tab.js 파일에서 사용할 수 있도록 해준다.

<br>
탭 화면을 하나의 파일이 아닌 각각의 파일로 작성해도 상관이 없다. 별도의 작업이 필요없는 경우에는 위와 같이 하나의 파일로 만들어도 괜찮다. 하지만 별도의 작업이 필요한 경우에는 각각의 파일로 만드는 것이 관리가 편리할 것이다.

<br>

{% highlight python %}
import React from 'react';
import { createBottomTabNavigator } from '@react-navigation/botom-tab';
import { Home, Calendar } from '../screens/TabScreens';

const Tab = createBottomTabNavigator();

const TabNavigation = () => {
    return (
        <Tab.Navigator>
            <Tab.Screen name="Home" component={Home} />
            <Tab.Screen name="Calendar" component={Calendar} />
        </Tab.Navigator>
    );
};

export default TabNavigation;
{% endhighlight %}

<br>

<h2>[첫 번째 오류 발생]</h2>
{% highlight html %}
Invariant Violation: Tried to register two views with the same name RNCSafeAreaProvider
{% endhighlight %}

<br>

expo를 통해 테스트를 하는 도중  다음과 같은 오류가 발생했다. web과 android에서는 정상적인 화면이 출력되는데 iOS에서만 다음과 같은 오류가 발생한다. 그래서 열심히 구글링한 결과 expo의 업데이트가 제대로 되지 않은 경우 이런 오류가 발생한다는 글을 보고 expo를 업데이트 했더니 정상적으로 화면이 출력되었다. 

<br>

> npm install -g expo-cli
>
> expo update

<br><br>

[예제 참고 : 처음 배우는 리액트 네이티브]<br>
[참고 사이트 :  [https://pythonq.com/so/react-native/578026](https://pythonq.com/so/react-native/578026) ]
