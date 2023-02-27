# CSR과 SSR의 차이

웹 페이지를 렌더링하는 방식

CSR(Client Side Rendering)

- 클라이언트 쪽에서 렌더링이 된다. 즉, 서버는 요청을 받으면 클라이언트에 html와 js를 보내준다. 클라이언트는 그것을 받아 렌더링을 시작한다. 유저는 자바스크립트가 모두 다운로드 되고 실행이 끝나기전까지 사이트를 볼 수 없다.

- CSR 동작 단계

  1. 사용자가 웹 페이지를 방문하면(request)

  2. CDN이 HTML 파일과 JS로 접근할 수 있는 링크를 클라이언트로 보낸다.

     CDN : 사용자에게 웹 콘텐츠를 효율적으로 제공할 수 있는 서버의 분산 네트워크

  3. 클라이언트는 HTML과 JS를 다운로드 받는다. 이때, SSR과 달리 유저는 아무것도 볼 수 없다.

  4. 다운이 완료된 JS가 실행되고 데이터를 위한 API가 호출된다. 이때, 유저들은 placeholder를 보게 된다.

  5. 서버가 API로부터의 요청에 응답한다.

  6. API 요청을 수행하여 동적 컨텐츠를 가져오고 파싱하여 최종 컨텐츠를 렌더링한다.

SSR(Server Side Rendering)

- 서버쪽에서 렌더링 준비를 끝마친 상태로 클라이언트에 전달하는 방식
- SSR 동작 단계
  1. USER가 웹사이트에 방문을 ㅎ면
  2. 서버는 ‘Ready to Render’ 즉, 즉시 렌더링 가능한 html파일을 만든다.
  3. 컴파일된 html은 추가 렌더링 및 표시를 위해 클라이언트에 전달된다.
  4. 클라이언트가 html을 다운로드하고 사용자가 사이트를 볼 수 있도록한다. (사이트 조작은 불가능, 이때 사용자의 조작을 기억하고 있는다.)
  5. 클라이언트가 자바스크립트를 다운로드하고 실행한다.
  6. 자바스크립트가 성공적으로 컴파일되었기 때문에 지금까지 기억하고 있던 사용자 조작이 실행되고 이제 웹 페이지는 상호작용이 가능해진다.

CSR과 SSR 차이점

1. 웹페이지를 로딩하는 시간
   - CSR : CSR의 경우 첫 페이지 로딩 시, HTML과 CSS, 스크립트들을 한 번에 불러와야해서 SSR보다는 느리지만 첫 페이지를 로딩한 후, 사이트의 다른 페이지로 이동을 할 때 CSR은 이미 나머지 부분을 구성하는 코드를 받아왔으므로 SSR 보다 빠르다.
   - SSR : SSR은 첫 페이지 로딩 시, 필요한 부분의 HTML과 스크립트만 불러오기 때문에 CSR보다 빠르지만 다른 페이지로 이동시에 다시 처음부터 렌더링해야하기 때문에 CSR보다 오래걸린다.
2. SEO
   - CSR : SEO(검색 엔진 최적화)에 친화적이지 않는다. 검색 엔진 크롤러가 해당 페이지에 처음 방문했을 때는 빈 페이지이기 때문이다.
   - SSR: SEO에 친화적이다. 이미 다 만들어진 페이지를 검색 엔진 크롤러가 요청에 대한 응답으로 받기 때문이다.