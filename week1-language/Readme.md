# Week1. DevOps RoadMap _Language_
#### ref. https://roadmap.sh/devops

## Subtitle 1. Programming Language
### Main Language : _[JAVA]_


### 1. 언어의 개발 배경 및 특이사항

  - 처음 개발 목적은 가전제품 내에 탑재해 동작하는 프로그램을 만들기 위해 개발
  - 타 컴파일 언어와 구분되는 가장 큰 특징 : 컴파일된 코드가 플랫폼 독립적이다.
    - 자바 컴파일러는 자바 언어로 작성된 프로그램을 바이트코드라는 특수한 바이너리 형태로 변환
    - 바이트 코드를 실행하기 위해 JVM(Java Virtual Machine)이라는 특수한 가상 머신 필요
    - JVM은 자바 바이트 코드를 어느 플랫폼에서나 동일한 형태로 실행
    - 자바 프로그램은 CPU나 운영체의 종류에 관계없이 JVM을 설치할 수 있는 시스템에서는 어디서나 실행할 수 있음
  - 자바 언어의 5가지 핵심 목표
    1. 객체 지향 방법론을 사용
    2. 같은 프로그램(바이트코드)이 여러 운영체제(마이크로 프로세서)에서 실행될 수 있어야 한다.
    3. 컴퓨터 네트워크 접근 기능이 기본적으로 탑재되어 있어야 한다.
    4. 원격 코드를 안전하게 실행할 수 있어야 한다.
    5. 다른 객체 지향 언어들의 좋은 부분만 가지고 와서 사용하기 편해야 한다.

### 2. 버전 히스토리
<details>
<summary> 히스토리 살펴보기 </summary>
  
  1. Java SE 8
      - `LTS`
      - 일반 지원은 2019년 1월 종료, 연장 지원은 2030년까지 오라클의 유료 지원
      - 주요 변경점 
        1. Lambda Expression
        2. 새로운 날짜와 시간 API(EX. JodaTime)
        3. Interface Default Method 추가
        4. PermGen 영역 삭제
        5. Stream API 추가 등

  2. Java SE 9
      - 주요 변경점
        - Java 바이트 코드를 기계어로 미리 번역하는 _선행 컴파일(Ahead-Of-Time Compilation) 실험 기능 추가

  3. Java SE 10
      - 주요 변경점
        - var 키워드를 이용한 지역 변수 타입 추론
        - 병렬처리 가비지 컬렉션, 개별 쓰레드로 분리된 Stop-The-World 등 추가
          - 기존에는 Stop-The-World가 발생하면 GC를 실행하는 쓰레드를 제외한 나머지 쓰레드는 모두 작업을 멈춤
          - GC 작업을 완료한 이후 중단 작업을 재시작
          - 개별 쓰레드로 분리되어 Stop-The-World 시간 개선
        - Enhanced for Loop를 위한 바이트 코드 생성
          - Loop에 대한 컴파일 접근 방식 개선
  4. Java SE 11
      - `LTS`
      - 주요 변경점
        - 라이선스의 변경
          - Oracle JDK의 독점 기능이 오픈소스 버전인 OpenJDK에 이식
            - Oracle JDK == Open JDK
          - 2019년 1월 부터 Oracle이 제공하는 모든 Oracle JDK는 유료화
            - OpenJDK를 기반으로 한 다른 서드파티 JDK가 대안으로 떠오름
              - Ex. Zula JDK, AdoptOpen JDK, Amazon cretto JDK
  5. Java SE 12
      - 주요 변경점
        - Switch문의 확장(Preview)
          ```
            # Java 11까지의 switch
            switch (day) {
              case MONDAY:
              case FRIDAY:
              case SUNDAY:
                System.out.println(6);
                break;
              case TUESDAY:
                System.out.println(7);
                break;
              case THURSDAY:
              case SATURDAY:
                System.out.println(8);
                break;
              case WEDNESDAY:
                System.out.println(9);
                break;
            }

            # Java 12에서 개선된 switch
            switch (day) {
              case MONDAY, FRIDAY, SUNDAY -> System.out.println(6);
              case THUESDAY               -> System.out.println(7);
              case THURSDAY, SATURDAY     -> System.out.println(8);
              case WEDNESDAY              -> System.out.println(9);
            }
          ```
  5. Java SE 13
      - 주요 변경점
        - Switch의 확장 (Preview)
          - `yield` 예약어의 추가
            ```
              switch (example) {
                case "returnOne":
                  yield "returnOne";
                case "returnTwo":
                  yield "returnTwo";
              }

              # 예시와 같이 break 키워드를 필요로 하지 않고 해당 yield에 매핑된 값을 return 하는 키워드
            ```
  6. Java SE 14
      - 주요 변경점
        - Switch의 확장(Standard)
          - JDK 12, 13에서 Preview를 통해 개발되던 내용을 Standard로 적용
        - `record` 오브젝트 선언 기능 추가
          - final class로 상속 불가능
          - 각 필드는 private final로 정의됨
        -  `instanceof` 패턴 매칭 추가
  7. Java SE 15
      - 주요 변경점
        - VCS가 `Mercurial`에서 `Github`으로 변경
          - 2021-03-30 jdk15u-dev repo open for 15.0.4 in Github
        - `sealed class` 추가(preview)
          - 상속(extends), 구현(implements)할 클래스를 지정하고 해당 클래스만 상속 또는 구현을 허용하도록 제한하는 키워드
          - 상속/ 구현 클래스는 `final`, `non-sealed`, `sealed` 중 하나로 선언되어야 함
          - Permitted Subclass들은 동일한 module에 속해야 하며 이름이 지정되지 않은 module에 선언 신에는 동일한 package내에 속해야 함
          - Permitted Subclass는 Sealed Class를 직접 확장해야 함
          - sealed class 예시
            - KHoeny님의 vlog, https://velog.io/@wwe221/Java-17-Sealed-Class
  8. Java SE 16
      - 주요 변경점
        - instanceof prview에서 standard로 추가
        - record prview에서 standard로 추가
  9. Java SE 17
      - `LTS`
      - 주요 변경점
        - 패턴매칭 >> `Preview`
        - sealed class >> standard
  10. Java SE 18 
      - 2022-03-22 출시
      - 주요 변경점
        - 기본 Charset이 `UTF-8`로 지정
        - 정적 파일을 서빙하는 기능만 있는 심플한 웹 서버 제공(커멘드라인 툴)
          - ref. https://openjdk.org/jeps/408
        - switch문의 instranceof 두번째 preview
        - try ~ catch ~ finally의 `finally` deprecate
          - try ~ with ~ resources 권장
  11. Java SE 19
      - 2022-09 출시
      - 주요 변경점
        - record 패턴매칭 preview
        - 가상 쓰레드 preview
        - switch pattern matching 3rd preview
  12. Java SE 20
      - 2023-03 출시
      - 주요 변경점
        - Scoped Values incubator
        - record pattern matching 2nd preview
        - virtual thread 2nd preview
  13. Java SE 21
      - `LTS`
        - 2023년 9월 출시 예정
        - LTS 여부와 지원 날짜는 변경될 수 있음
</details>

### 3. 언어의 트랜드
  - __개요__
    - Mahiplasinh Rana 작성글 참조
      - 누구세요..?
        - 엔터프라이즈 소프트웨어 개발 서비스를 제공하는 Inexture의 CTO
  - __2022년 기준 자바 최신 트렌드 Top 6__
    1. Java 17의 채택 증가
        - 2021년 출시된 가장 최근의 `LTS` 버전
        - 앞으로 몇 년 내에 가장 많이 사용하는 자바 버전이 될것으로 전망중
        - 현재 가장 많이 사용하는 버전은 8
        - 현재 배포된 버전 중 LTS는 8, 11, 17 버전
    2. VSCode의 채택
        - VSCode에 대한 사용자 증가
        - 다국어를 지원하는 통합 개발 도구이기 때문에
        - 개인적인 생각
          - Intellij의 경우 유료 idea인 반면 VSCode는 무료 idea 이기 때문에 많이 사용하는것 같음
          - spring 또는 spring boot를 사용할 경우 intellij가 최적화 되어있다고 생각중
            - intelij의 경우 project 생성하는 단계에서 부터 spring에 최적화되어 있는 반면 vscode의 경우 다양한 언어를 기본적으로 지원하다 보니 범용적으로 사용하기에는 편리하지만 전문성은 상대적으로 떨어지는것 같음
          - Java 언어에 국한된 트렌드이기보다는 개발 전체적인 상황에서의 트렌드라고 보아야 할 것
    3. Spring Framework
        - 가장 널리 사용되는 자바 프레임워크
    4. SpringBoot의 인기 상승
        - 스프링과 스프링부트는 자바가 지금까지 도입한 수많은 프레임워크 중 가장 인기있는 프레임워크
        - 스프링 프레임워크는 시간이 지남에 따라 입지가 불안할 가능성이 있지만, 부트의 경우 강력한 기능을 바탕으로 대체 불가능한 위치에 있음
    5. LTS 외 자바 버전의 채택률 감소
        - 자바 LTS외 버전의 채택률이 어느때보다 낮아짐
        - 향후 LTS 버전 출시가 예정되어 있다면 개발자들의 새로운 번을 활발하게 채택하지 않을 가능성
        - 개인적인 생각
          - LTS버전이 아니라도 개별 개발자가 생각하고 있는 특정 문법에서의 개혁 또는 문제점을 해결할 수 있는 새로운 키워드가 등장하게 된다면 LTS 버전이 아니라도 주목해볼 가치가 있을듯
          - realease note를 얼마나 잘 챙겨보고 관심있게 들여다 보는지가 중요할 것
    6. 원격 접근 솔루션
        - 리모트 근무의 확대에 따라 자바는 광범위한 원격 접근 서비스를 제공하는데 심혈을 기울임
        - 가상 사설망(VPN), 원격 작업 앱, 직원 업무 포털 등 개발 가능
        - 개인 생각
          - 이게 JAVA가 현재 어떠한 조치를 한것이라기 보다는 Java를 통해 개발될 가능성이 있는 것들에 대한 제안일 뿐 Java의 특정 부분이 어떻게 영향을 미쳤는지는 잘 모르겠음
          - Java SE 19의 가상 쓰레드(Preview)와 연관이 있을지도..?

### 4. 구동 방식
  1. 소스코드의 작성(.java)
  2. 컴파일러(javac.exe)가 바이트 코드로 변환(.class 확장자의 클래스 파일)
  3. 런처(java.exe)로 자바 가상 머신을 구동
  4. 자바 가상 머신(JVM)이 바이트 코드를 해석하여 자바 프로그램이 실행
  
  ![Clipboard_2023-03-12-16-17-12](https://user-images.githubusercontent.com/108737977/224591942-b796a1c7-f778-47fd-98f0-9262982eeee0.png)

  *자바 프로그램 구동 원리 Ref. <a href="https://dongjin94.tistory.com/177">https://dongjin94.tistory.com/177</a>*

### 5. 매력 포인트
  1. 플랫폼의 구애를 받지 않음
  2. 웹 기반 소프트웨어 개발에 있어 조건을 충족하고, 사용 편의서이과 내구성을 갖추고 있음
  3. 타 언어에 비해 비교적으로 시장의 풀이 넓음

### 6. Framework
  1. Spring Framework
  2. Spring Boot
  3. 스트럿츠 프레임워크(STRUS Framework)

<details>
<summary> 자바 기반의 JSP만을 위한 프레임워크 </summary>

- 자바 기반의 JSP만을 위한 프레임워크로 다양한 운영체에서 활용할 수 있으며, 오픈소스이기 때문에 개발에 필요한 부분을 수정하여 사용할 수 있다.
- MVC 패턴 기반의 프레임워크
- 웹 개발의 초기에는 스트럿츠 프레임워크 기반의 개발이 많이 이루어졌었다고 한다.

- ref. https://www.castingn.com/sourcing/kkultip_detail/110
</details>

---

#### Interested in Language : _[Python]_
### 1. 언어의 개발 배경 및 특이사항
  - 1991년 귀도 반 로섬이 발표한 프로그래밍 언어
  - 1898년 크리스마스 주에 연구실이 닫혀있어서 심심한 김에 만든 프로그램언어라고...
  - 특이사항
    - `가장 아름다운 하나의 답이 존재한다`를 기본 디자인 철학으로 함([PEP20](https://peps.python.org/pep-0020/))
    - 뚜렷한 권장 코드 스타일을 가지고 있다.
      - 블록 처리 규칙
        - 블록 단위를 중괄호 대신 들여쓰기를 사용하여 처리
      - 작명 규칙
        - 변수나 클래스 이름을 어떻게 짓든 잘 작동하지만 [PEP 8](https://peps.python.org/pep-0008/)에서는 이에 대한 권장 스타일을 명시함
        - 변수는 소문자로 시작하며, 내부 변수(internal)는 맨 앞에 밑줄 1개로 시작, 숨은 변수는 밑줄 2개로 시작
      - 문법 규칙
        - 한 줄은 79글자로 제한
        - import는 파일 맨 위에 적고 내장 모듈, 제3자 모듈, 직접 만든 모듈 순서로 불러들이기
        - 인스턴스 메서드의 첫 인자는 self로 쓰고, 클래스 메서드의 첫 인자는 cls로 쓰기
        - 할당 연산자의 앞 뒤로 공백 넣기
      - 작성한 코드가 PEP 8 스타일의 가이드를 지키는 지 확인해주는 Python 패키지도 존재
    - 순수 객체 지향 언어
      - 원시 타입이 존재하지 않고 모든것이 객체로 취급됨
      - 클래스, 함수 역시 객체로 취급할 수 있음
      - 상수 역시 상수가 저장된 객체라고 봄
    - 반복 가능한 객체(iterable) 기능 제공
      - 집합, 문자열, 리스트, 튜플, 딕셔너리, 그리고 함수까지 반복이 가능
        ```
          def f(n):
              x = 1
              while True:
                  yield n*x
                  x += 1

          ot = f(2)
          print(ot)
          print(next(ot))
          print(next(ot))
        ```

### 2. 언어의 트랜드
  - 2023년 주목 10가지 파이썬 개발 트렌드 
    1. 데이터 과학
    2. 프레임워크 업그레이드
    3. 웹/모바일 애플리케이션 개발
    4. 클라우드 컴퓨팅
    5. 인공지능/머신러닝 애플리케이션
    6. 학계 내 중요서 ㅇ강화
    7. 자동화와 로봇화
    8. 웹 스크래핑 애플레이션 활용도 증가
    9. 게임 개발
    10. 다른 프로그래밍 언어와 통합

### 3. 구동 방식
  - 소스코드의 작성
  - 파이썬 컴파일러
  - 바이트코드(.pyc)
  - 파이썬 인터프리터(가상 머신)
  - 저급 기계어
  - CPU

### 4. 매력 포인트
  - 빠른 개발 속도
    - 인터프리터 언어이면서 우수한 자료형과 다양한 모듈 등을 제공하여 개발 기간이 단축
    - C언어로 2년동안 완성하지 못한 프로젝트를 Python을 이용해 한달만에 해냈다 라는 극적인 경험담이 있을 정도
  - 피드백의 용이성
    - 디자인 철학 자체가 가장 완벽한 하나의 아름다운 해답을 찾는 Python 특유의 철학으로 문법 자체가 딱 떨어지게 표현된다.
    - 문법의 통일로 인해 가독성이 좋음
    - `Write Once, Read Infinitely`
  - 과학 및 공학 친화성
    - 64비트가 넘는 매우 큰 정수 지원, 허수 지원, 소수점과 유리수를 정밀하게 사용 가능
    - 함호학과 통계 분야에서 유용하게 사용할 수 있음
  - 거대한 생태계
    - 다양한 패키지의 지원
      - web : Djongo, Flask
      - 알고리즘 : scikit-learn, TensorFlow, PyTorch
      - 안면인식 : OpenCV
      - GUI : tkinter
      - 게임 : Pygame
      - 비쥬얼 노벨 : 렌파이
      - ...
  - 교육의 편의성
    - 교육을 목적으로 만들어진 언어
  - GPGPU 기반의 병렬 연산
    - GPU 기반 병렬 연산에 용이
      - 머신러닝에서 파이썬이 대세가 된 주요 이유

### 5. 단점
  - 국한된 범용성
    - 거대한 생태계로 여러 분야에서 각광을 받고있는 언어이지만 모바일 웹 등 일부 기능은 지원되지 않는 한계가 있음
  - 교육의 편의성?
    - 프로그래밍에 입문하며 기초 문법을 익히기에는 용이하지만, 딥러닝 할 경우 파이썬 특유의 파이썬 스러운 코딩을 하려면 생각보다 신경 쓸 것이 많고 동적 언어에 익숙해져야 한다.
  - 느린 실행 속도
    - [논문](https://dl.acm.org/doi/abs/10.1145/3136014.3136031)에 따르면 10개의 벤치마킹을 구동해본 결과 Python은 C에 비해 `71.90배의 시간`, `2.80배의 메모리`, `75,88배의 에너지`를 더 소모한다고 함
  - 일반 사용자에게 배포의 어려움
    - 프로그래머가 곧 자기가 만든 프로그램의 이용자를 가정하기 때문에 배포 과정이 덜 발달 되어 있음

### 5. Framework
  - Django
    - 풀스택 웹 프레임워크로 정식 비동기 프로그래밍이 가능한것은 아니지만, ASGI서버와도 부분적으로 호환이 된다.
  - Flast
    - 마이크로 웹 프레임워크로 가볍고 간단한 서비스를 만들기는 좋으나, 복잡한 기능은 모두 플러그인을 설치해야 한다.
