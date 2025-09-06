# Q: Node와 Element의 차이에 대해 설명해주세요.

### Node
Node는 **DOM을 구성하는 가장 기본적인 구성 단위**입니다. Node에는 여러 가지 타입이 존재합니다. 
- `Document Node`는 HTML 문서 전체를 나타내는 루트 노드이며, `Element Node`는 HTML 태그를 나타내고,  
  `Text Node`는 텍스트 내용을, `Comment Node`는 주석을 나타냅니다.
- 이처럼 Node는 DOM 트리의 모든 구성 요소를 포함하는 포괄적인 개념입니다.

### Element
반면 Element는 Node의 특정 타입 중 하나로, **HTML이나 XML 태그로 표현되는 객체**를 의미합니다. 
- 쉽게 말해, 모든 Element는 Node이지만, 모든 Node가 Element인 것은 아닙니다.
- Element는 `id`, `class`, `style`과 같은 HTML 속성을 가질 수 있으며, `querySelector()`나 `getElementsByClassName()`과 같은 메서드를 사용할 수 있다는 특징이 있습니다.

예를 들어 `<div>Hello<!--주석-->World</div>`라는 HTML이 있다면, div 태그는 Element Node이면서 동시에 Node입니다.   
반면 'Hello'와 'World'라는 텍스트는 `Text Node`이며, 주석은 `Comment Node`입니다. 이들은 모두 Node이지만 Element는 아닙니다.

<br/>

# Q: Node와 Element의 차이와 관련된 구체적인 예시를 들어주세요. 

예를 들어, `textContent`라는 속성은 Node의 속성이므로 모든 종류의 Node에서 사용할 수 있지만, `innerHTML`은 Element의 속성이므로 Element에서만 사용할 수 있습니다.

또한, `childNodes`와 `children` 속성에도 중요한 차이가 있습니다. 

- **Node의 속성인 `childNodes`는 주어진 요소의 모든 자식 Node를 포함하는 `NodeList`를 반환합니다.** 
  - 여기에는 Element뿐만 아니라 모든 종류의 Node가 포함됩니다. 따라서 HTML 태그뿐 아니라 텍스트, 주석도 childNodes에 포함됩니다.

- **반면 Element의 속성인 `children`은, Element 타입의 자식 노드만을 포함하는 `HTMLCollection`을 반환합니다.**
  - 여기에는 텍스트 노드나 주석 노드는 제외되고 HTML 요소 노드만 포함됩니다.
