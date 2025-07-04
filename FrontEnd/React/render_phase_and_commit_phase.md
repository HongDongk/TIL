# Q: 리액트의 render phase와 commit phase에 대해서 설명해주세요.
> 리액트의 렌더링 과정은 크게 두 가지 단계로 나눌 수 있습니다. `render phase`와 `commit phase`입니다.

#### render phase
  - **리액트가 변화된 상태나 props에 따라 어떤 UI가 변경되어야 할지를 결정하는 단계입니다.**
  - 이 과정에서는 실제로 DOM을 업데이트하지 않고, 변경사항을 가상 DOM에서 계산하여 비교합니다.
  - 이 단계는 순수하게 계산과정이기 때문에 성능에 영향을 주지 않도록 중단되거나 다시 실행될 수 있으며,
  - `React 18`에서 도입된 `Concurrent Mode`를 통해 비동기적으로 처리될 수도 있습니다.

#### commit phase
  - **실제로 변화된 UI를 DOM에 반영하는 단계입니다.**
  - 이때 리액트는 가상 DOM에서 계산된 결과를 실제 DOM에 적용하고, 변화된 UI를 브라우저에 렌더링합니다.  
  - DOM 업데이트 이후에는 `useEffect`와 같은 사이드 이펙트를 발생시키는 훅들이 실행됩니다.

![image](https://github.com/user-attachments/assets/8ef72458-bb40-4d3d-be2c-32466b80b2ca)

요약하면 `render phase`는 변화된 UI를 결정하는 계산 과정이고, `commit phase`는 그 계산된 결과를 실제로 반영하는 단계입니다.

<br />

# Q: 그럼 render phase와 commit phase가 동기화될 때의 특징이 있을까요? 
> 크게 두 가지로 말씀드릴 수 있습니다. **단계적 진행**과 **병목 관리**입니다.

첫번째로 `render phase`가 완료되면 리액트는 즉시 `commit phase`를 실행하지 않고, **다른 높은 우선순위 작업이 있다면 먼저 처리한 후 나중에 `commit phase`를 실행**합니다.   
이러한 단계적 진행을 통해 React는 동기화가 필요한 작업을 효율적으로 관리하여 사용자 경험을 개선합니다.

두번째로 병목 관리입니다. `render phase`에서 모든 변경 사항이 `Fiber Tree`에 준비된 상태에서 `commit phase`로 넘어가므로, render와 commit 단계의 일관성이 유지됩니다.  
이렇게 **두 단계는 순차적으로 작동하여, UI가 정확하게 동기화되고 불필요한 재렌더링을 방지**합니다.


