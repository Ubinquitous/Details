## 명령어들

```js
toBe(a) // 예상한 값이 매개변수와 같은 값일 것인지 확인합니다.
toEqual(obj) // 매개변수(객체)와 같은 값일 것이라 예상합니다. 객체가 가진 값의 비교가 가능합니다.
not.toBe(a) // 뒤의 결과를 부정하는 값과 비교합니다.

toBeNull() // 예상한 값이 null 인지 확인합니다.
toBeUndefined() // 예상한 값이 undefined 인지 확인합니다.
toBeDefined() // 예상한 값이 undefined 가 아닌지 확인합니다.
toBeTruthy() // 예상한 값이 truthy 한 값인지 확인합니다.
toBeFalsy() // 예상한 값이 falsy 한 값인지 확인합니다.

toBeGreaterThan(number) // number보다 큰 값인지 확인합니다.
toBeGreaterThanOrEqual(number) // number보다 크거나 같은 값인지 확인합니다.
toBeLessThan(number) // number보다 작은 값인지 확인합니다.
toBeLessThanOrEqual(number) // number보다 작거나 같은 값인지 확인합니다.
toBeCloseTo(float) // float인 매개변수와 같은 값인지 확인합니다. 부동소수점 에러를 해결하기 위해 고안되었습니다.

toMatch(string) // string을 포함하는 문자열인지 확인합니다.
toContain('item') // item을 포함하는 배열(iterator)인지 확인합니다.

toThrow() // 예외를 발생시키는지 확인합니다.
```

자세한 명령어 (매처)들은 Jest의 공식문서에 잘 설명되어있다.  
<a href="https://jestjs.io/docs/using-matchers" target="_blank">https://jestjs.io/docs/using-matchers</a>
