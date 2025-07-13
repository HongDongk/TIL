# Q: useEffect와 useLayoutEffect의 차이점에 대해서 설명해주세요.
> `useEffect`와 `useLayoutEffect`는 모두 렌더링된 후에 특정 작업을 수행하기 위해 사용됩니다. 하지만 실행되는 타이밍과 용도가 다릅니다.

### useEffect
`useEffect`는 **렌더링이 완료되는 시점에 비동기적으로 실행**됩니다.
   - 즉, **화면이 실제로 사용자에게 그려진 후** `useEffect`가 실행되는 방식입니다.
   - `useEffect`는 보통 데이터를 가져오는 작업이나 이벤트 리스너 추가 등 렌더링 후에 화면에 직접적인 영향을 주지 않는 작업에 주로 사용됩니다.
   - 즉, 렌더링 후 실행되는 비동기 작업에는 `useEffect`가 적합합니다.
   - 예를 들면, `useEffect`는 사용자 데이터를 API로부터 가져오는 상황에 자주 사용합니다. 데이터가 렌더링 후에 설정되면 화면이 자연스럽게 업데이트되는 것입니다.

 ```javascript
 useEffect(() => {
   fetchData().then(data => setData(data));
 }, []);
 ```
     
### useLayoutEffect
`useLayoutEffect`는 **렌더링 후 DOM이 업데이트되기 직전의 시점에 동기적**으로 실행됩니다. 
   - 즉, **화면이 실제로 사용자에게 그려지기 전에** `useLayoutEffect`가 실행되는 방식입니다.
   - 예를 들어, DOM의 크기를 측정하거나 위치를 조정해야 할 때 `useLayoutEffect`를 사용하면 즉각적으로 그 변경사항이 반영되어 화면 깜빡임이나 불필요한 재렌더링을 방지할 수 있습니다.
   - 레이아웃 작업이나 DOM 조작과 같이 화면이 그려지기 전에 완료되어야 하는 작업에는 `useLayoutEffect`가 적합합니다.
   - DOM의 크기를 측정해서, 다른 요소의 위치를 조정해야 할 때 유용합니다. 예를 들어, 어떤 요소의 높이를 측정해 그 높이에 맞춰 레이아웃을 맞추고 싶을 때 사용합니다.

```javascript
 useLayoutEffect(() => {
   const height = ref.current.offsetHeight;
   setHeight(height);
 }, []);
 ```
<br />

단, `useLayoutEffect` 사용 시 성능 면에서 주의할 점이 있습니다. `useLayoutEffect`는 동기적으로 실행되기 때문에 너무 많은 작업이 실행되면 렌더링이 느려질 수 있습니다.

따라서 보통은 `useEffect`를 기본적으로 사용하고, 화면에 영향을 주는 작업만 `useLayoutEffect`로 처리하는 것이 좋습니다.


