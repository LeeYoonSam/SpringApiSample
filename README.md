# Spring 참고 사항

# 패키지 구조
```bash
domain
    └── feed
        ├── controller
        ├── domain
        ├── exception
        ├── repository
        └── service
global
    └── exception
        ├── CommonException.kt
        └── InvalidRequestException.kt
```

## domain
> 도메인 단위로 패키지를 구조화

### controller
> API Route

### domain
> 도메인 모델 생성

### exception
> 도메인에서 사용될 exception 구현

### repository

### service
> 도메인 로직 처리

### 

## global
> 전체 공통으로 사용할 패키지

# RestController 구현 후 실행시 오류 발생

Error
```
Failed to configure a DataSource: 'url' attribute is not specified and no embedded datasource could be configured.
Reason: Failed to determine a suitable driver class

Action:
Consider the following:
	If you want an embedded database (H2, HSQL or Derby), please put it on the classpath.
	If you have database settings to be loaded from a particular profile you may need to activate it (no profiles are currently active).
```

- Dependencies로 데이터베이스를 쓰겠다고 추가해줬지만 정의를 해주지 않아서 뜨는 에러이기 떄문에 아래에 있는 코드를 추가해주면 됩니다.

```kotlin
@EnableAutoConfiguration(exclude = [DataSourceAutoConfiguration::class])
```

# Port 변경
- resources > application.properties 에 포트 변경
```
server.port= 8081
```