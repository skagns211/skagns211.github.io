---
layout: single
title: "TIL-74, Expo Location API"
---
Expo에 Location이라는 아주 재밌는, 아주 흥미로운 API가 있다!

내 장치에 위치 정보 권한을 요청한 뒤, 위치 정보를 위도와 경도로 받아온 뒤,

해당 위도와 경도로 주소를 얻어내는 것이다!

([https://docs.expo.dev/versions/v44.0.0/sdk/location/](https://docs.expo.dev/versions/v44.0.0/sdk/location/))

아주 많은 Methods가 있는데, 위의 Expo 공식 문서에서 확인하도록 하고,

어떻게 주소를 얻어내는지 알아보도록 하자.

우선 공식문서대로

```jsx
$ expo install expo-location
```

expo-location을 install 해준다.

```jsx
import React, { useState, useEffect } from "react";
import * as Location from "expo-location";
...

export default function App() {
  const [location, setLocation] = useState();
  const [isOk, setIsOk] = useState(true);
  
  const ask = async () => {
    // 최초 실행때 위치 정보 권한을 허락 후 삭제. await Location.requestPermissionsAsync();
    const { granted } = await Location.requestForegroundPermissionsAsync();
    // 앱이 실행 중(foreground)일 때만 위치 추적 허용. (허용시 granted -> true)
    if (!granted) {
      setIsOk(false);
    // granted가 false일 때 (위치 추적 미허용) isOk값을 false로.
    }
    const {
      coords: { latitude, logitude },
    } = await Location.getCurrentPositionAsync({ accuracy: 5});
    // 나의 latitude와 logitude를 구한다.
    const location = await Location.reverseGeocodeAsync(
      { latitude, logitude },
      { useGoogleMaps: false },
    );
    // 구한 latitude와 logitude를 이용해 주소를 구한다.
    console.log(location);
    // Array[Object {"city": "", "country": "" ...}] 의 형식으로 주소 출력
  };
  useEffect(() => {
    ask();
  }, []);
}
```

Expo에 Location이라는 아주 재밌는, 아주 흥미로운 API가 있다!

내 장치에 위치 정보 권한을 요청한 뒤, 위치 정보를 위도와 경도로 받아온 뒤,

해당 위도와 경도로 주소를 얻어내는 것이다!

([https://docs.expo.dev/versions/v44.0.0/sdk/location/](https://docs.expo.dev/versions/v44.0.0/sdk/location/))

아주 많은 Methods가 있는데, 위의 Expo 공식 문서에서 확인하도록 하고,

어떻게 주소를 얻어내는지 알아보도록 하자.

우선 공식문서대로

```jsx
$ expo install expo-location
```

expo-location을 install 해준다.

```jsx
import React, { useState, useEffect } from "react";
import * as Location from "expo-location";
...

export default function App() {
  const [location, setLocation] = useState();
  const [isOk, setIsOk] = useState(true);
  
  const ask = async () => {
    // 최초 실행때 위치 정보 권한을 허락 후 삭제. await Location.requestPermissionsAsync();
    const { granted } = await Location.requestForegroundPermissionsAsync();
    // 앱이 실행 중(foreground)일 때만 위치 추적 허용. (허용시 granted -> true)
    if (!granted) {
      setIsOk(false);
    // granted가 false일 때 (위치 추적 미허용) isOk값을 false로.
    }
    const {
      coords: { latitude, logitude },
    } = await Location.getCurrentPositionAsync({ accuracy: 5});
    // 나의 latitude와 logitude를 구한다.
    const location = await Location.reverseGeocodeAsync(
      { latitude, logitude },
      { useGoogleMaps: false },
    );
    // 구한 latitude와 logitude를 이용해 주소를 구한다.
    console.log(location);
    // Array[Object {"city": "", "country": "" ...}] 의 형식으로 주소 출력
  };
  useEffect(() => {
    ask();
  }, []);
}
```