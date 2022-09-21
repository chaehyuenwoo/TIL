# Maven vs Gradle


#### 이번에는 Java 빌드 도구인 Maven과 Gradle의 차이점에 대해 정리할 것이다.

> \[ 목적 \]  
> 최근까지 빌드 도구를 Maven만 사용하였고, 최근에 Gradle을 사용하게 되었다.  
> 단순히 Gradle이 더 최신 빌드 도구라는 것만 알고 자세한 차이점을 몰라서 이 2개의 빌드 도구의 정의와  
> 차이점을 알기 위해 정리하게 되었다.


## **빌드 도구(Build Tool) 이란?**

Maven과 Gradle를 설명하기 전에 `빌드 도구(Build Tool)`에 대해 간단하게 정리할 것이다.

빌드 도구(Build Tool)이란 소프트웨어 개발에 있어서 **소스 코드를 실행 가능한 애플리케이션으로 만들어주는**

**도구**를 뜻한다. 빌드 과정을 자동화하여 관리하는 기능을 하기에 빌드 관리 도구 (Build Management Tool) 또는

빌드 자동화 도구 (Build Automation Tool)라고 불리기도 한다.

## **Maven vs Gradle**

우선 **Maven, Gradle에 차이점**을 간략하게 알아볼 것이다.

메이븐(Maven)은 보통 스프링에서 pom.xml이란 이름으로 쓰고,

그래들 (Gradle)은 스프링 부트, 안드로이드에서 사용하는 것으로 알고 있다.

필자는 국비과정을 들으며 Maven을 사용하였고, Maven Repository에서 라이브러리를 받아오기

위한 도구로 알고 있었다. 하지만 그 외에도 다른 기능들이 많다.

## **Maven 이란?**

스프링 프로젝트를 개발하게 되면 내가 작성한 코드만으로 개발하는 것이 아니고 많은 라이브러리들을 활용해서

개발을 하게 된다. 수많은 라이브러리들을 사용하게 되면 관리하는 것이 힘들어지는데 Maven은 이러한 문제를

해결해 줄 수 있는 도구이다. Maven은 내가 사용할 라이브러리뿐만 아니라 해당 라이브러리가 작동하는데

필요한 다른 라이브러리들까지 관리하여 자동으로 다운로드하여 준다.

**메이븐(Maven)**은 Ant라는 빌드 도구 이후에 나온 Java 빌드 도구로 자동으로 라이브러리와 의존성(dependency)을

관리하는 기능이 있다. Maven은 XML 스크립트를 기반으로 하며, pom.xml이라는 파일로 의존성을 관리한다.

Maven에서는 라이프 사이클(Life Cycle) 개념이 도입되어 빌드 순서 등을 정의할 수 있다.

## **POM (Project Object Model)**

pom.xml의 pom은 Project Object Model의 약자로 이름 그대로 Project Object Model의 정보를 담고 있는 파일이다.

pom.xml에서 주로 다루는 기능들을 다음과 같다.

-   **프로젝트 정보** : 프로젝트 이름, 개발자 목록, 라이선스 등등
-   **빌드 설정** : 소스 코드, 리소스, Life Cycle별 실행한 플러그인 등 빌드와 관련된 설정
-   **빌드 환경** : 사용자 환경 별로 달라질 수 있는 프로파일 정보
-   **POM 연관 정보** : 의존 프로젝트, 상위 프로젝트 등을 포함하고 있는 하위 모듈 등

POM은 pom.xml 파일을 말하며 Maven의 기능을 이용하기 위해 POM이 사용되는 것이다.

## **Maven의 Life Cycle**

메이븐(Maven)에서는 미리 정의하고 있는 빌드 순서가 있는데 이 순서를 **라이프사이클(Life Cycle)**라고 한다.

라이프 사이클의 빌드 단계를 Phase라고 하는데 Phase들은 의존 관계를 가지고 있어 해당 Phase가 수행되려면 이전 단계의 Phase가 모두 수행되어야 한다.

※ Maven에서 제공되는 모든 기능은 플러그인 기반으로 동작하는데 Phase 또한 플러그인을 통해 실질적인 작업이 수행된다.

> Phase : Maven의 Build Life Cycle의 각각의 단계를 의미

-   **Clean** : 이전 빌드에서 생성된 파일들을 삭제하는 단계
-   **Validate** : 프로젝트가 올바른지 확인하고 필요한 모든 정보를 사용할 수 있는지 확인하는 단계
-   **Compile** : 프로젝트의 소스 코드를 컴파일하는 단계
-   **Test** : 유닛(단위) 테스트를 수행하는 단계 - (테스트 실패 시 빌드 실패로 처리한다. 스킵 가능)
-   **Package** : 실제 컴파일된 소스 코드와 리소스들을 jar 등의 배포를 위한 패키지로 만드는 단계
-   **Verify** : 통합 테스트 결과에 대한 검사를 실행하여 품질 기준을 충족하는지 확인하는 단계
-   **Install** : 패키지를 로컬 저장소에 설치하는 단계
-   **Site** : 프로젝트 문서를 생성하는 단계
-   **Deploy** : 만들어진 패키지(Package)를 원격 저장소에 release 하는 단계

위의 라이프 사이클(Life Cycle) 외에도 더 많은 라이프 사이클이 존재한다.

이를 크게 Clean, Build, Site 3가지 라이프 사이클로 나누고 있고, 각 단계를 모두 수행하는 것이 아니라

원하는 단계까지만 수행할 수 있다.

---

## **Gradle 이란?**

**그래들(Gradle)**은 Maven 이후에 나온 최신 Java 빌드 도구로 '**그루비(Groovy)' 문법**을 사용해서 작성한다.

**Build.gradl**e에 스크립트를 작성하며, 대규모 프로젝트에서 복잡해지는 경향이 있는 XML 기반 스크립트에 비해 관리가 

편하다는 장점이 있다. 현재 안드로이드(Android) 프로젝트의 표준 빌드 도구로 채택되어 있기도 하다.

**\[ Gradle의 장점 \]**

**(1) - 간결한 스크립트**

Gradle 이전의 빌드 도구인 Ant와 Maven은 XML 문법으로 스크립트를 작성하였다.

XML은 여는 태그와 닫는 태그를 넣어야 하기에 복잡한 빌드 스크립트를 작성하기가 어려우며 가독성이 떨어진다.

반면, Gradle은 Groovy 문법으로 간결한 스크립트를 작성할 수 있다.

**(2) - 빌드 속도**

프로젝트 규모가 커지게 되면 빌드 속도 차이가 개발 생산성에 큰 영향을 미치게 된다.

Gradle은 캐싱(caching)을 하기 때문에 이전 빌드 도구보다 빌드 속도가 빠르다.

※ 하단 링크 페이지에 빌드 캐시(Build cache)를 이용할 경우 Gradle이 Maven의 빌드 속도가

    최대 100배까지 벌어질 수 있다고 적혀 있다.

[https://gradle.org/maven-vs-gradle/](https://gradle.org/maven-vs-gradle/)

 [Gradle | Gradle vs Maven Comparison

High-level performance and feature comparison between Gradle and Maven

gradle.org](https://gradle.org/maven-vs-gradle/)

**(3) - 멀티 프로젝트 빌드**

대규모 Java 프로젝트는 대부분 다중 모듈로 구성된다.

즉, 하나의 프로젝트 안에 여러 모듈이 동시에 개발되며, 각 모듈이 공통으로 사용하는 모듈도 만들어지게 되는데 이렇게 동시에

여러 모듈을 개발하게 되는 경우 각각 따로 빌드 작업을 하면 번거로울 뿐만 아니라 실수가 생기기도 쉽다.

Gradle의 멀티 프로젝트 빌드 기능을 이용하면 이런 번거로움과 실수를 획기적으로 줄일 수 있다.

---

**\[출처 및 참고 문헌\]**

[https://hyojun123.github.io/2019/04/18/gradleAndMaven/](https://hyojun123.github.io/2019/04/18/gradleAndMaven/)

 [Maven과 Gradle의 차이

Maven vs Gradle 우선 둘의 차이를 알기위해 각각 알아보았다. Maven같은경우는 스프링프로젝트에서 pom.xml이란 이름으로 쓰고, Gradle은 스프링부트, 안드로이드에서 쓰는걸로 알고있다. 처음에 단순히

hyojun123.github.io](https://hyojun123.github.io/2019/04/18/gradleAndMaven/)
