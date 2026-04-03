## JS Web API 학습 기록 (Timer, Storage, Fetch, To-Do)
학습 목표: 브라우저 API(Timer, LocalStorage, Fetch, To-Do)를 활용해 실무에서 쓰이는 동적 기능 구현하기

# 1. Timer API (timer.html)
setInterval을 이용해 10초부터 0초까지 줄어드는 카운트다운 타이머를 만들었습니다.

핵심 로직: setInterval로 1초마다 숫자를 줄이고, 0이 되면 clearInterval로 멈추는 게 포인트입니다.
주의할 점: 타이머가 이미 돌아가고 있는데 버튼을 또 누르면 타이머가 중복으로 생성되어 숫자가 엄청 빨리 줄어듭니다.
해결: timerId가 없을 때만 실행하게 조건을 걸거나, 버튼을 disabled 처리해서 중복 클릭을 막았습니다.

# 2. LocalStorage 활용 (storage.html)
브라우저를 새로고침하거나 꺼도 데이터가 사라지지 않게 저장하는 방법을 배웠습니다.

기억해야 할 특징
문자열만 저장 가능: 숫자나 객체를 넣어도 문자열로 바뀌어 버립니다.
데이터 유지: localStorage.setItem('key', 'value')로 저장하면 직접 지우기 전까지 남습니다.

# 3. Fetch API (fetch.html)
외부 서버(API)에서 데이터를 가져오거나(GET), 내가 쓴 데이터를 보내는(POST) 연습을 했습니다.

GET: fetch(URL)로 데이터를 요청하고 .json()으로 변환해서 화면에 뿌려줍니다.
POST: 데이터를 보낼 때는 method: "POST", body: JSON.stringify(...) 처럼 형식을 맞춰야 합니다.
팁: JSON.stringify(data, null, 2)를 쓰면 콘솔이나 화면에 JSON이 예쁘게 정렬되어 나와서 보기 편합니다.

# 4. To-Do 리스트 (todo.html)
LocalStorage와 배열을 조합해서 실제 서비스 같은 할 일 목록을 구현했습니다.

배열 저장법 (핵심 로직)
단순히 문자열 하나만 저장하면 기존 데이터가 덮어씌워지는 문제가 있었습니다. 여러 개를 저장하기 위해 배열을 사용했습니다.

데이터 추가: todos.push(text)로 배열에 값을 담은 뒤, JSON.stringify()를 써서 배열 통째로 문자열로 만들어 저장합니다.
데이터 로드: 페이지를 켜자마자 localStorage에서 데이터를 가져와 JSON.parse()로 다시 배열로 바꾼 뒤 화면에 그려줍니다.
방어 코드: input.value.trim()을 사용해 의미 없는 공백이 저장되지 않도록 처리했습니다.


오늘 한 줄 평
"데이터를 다룰 때는 **'타입'**이 정말 중요하다는 걸 느꼈다. 특히 화면에 보이는 것과 실제 저장소(Storage)의 데이터를 동기화하는 감을 잡은 게 큰 수확이다!"
