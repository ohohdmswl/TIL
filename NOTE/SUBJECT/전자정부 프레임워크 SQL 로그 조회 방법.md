## 전자정부 프레임워크 SQL 로그 조회 방법
#eGOV/log #전자정부프레임워크 #SQL로그조회
- 참고 url
	- https://web-obj.tistory.com/499


```xml
## log4jdbc
## -> JDBC 호출을 감시하고 SQL 쿼리를 로깅하는 데 사용되는 라이브러리
##
## log4jdbc.spylogdelegator.name
## -> 로그를 기록할 때 어떤 로깅 프레임워크를 사용할지 지정
## -> log4jdbc가 SLF4J를 통해 로그를 기록하도록 지정
## -> SLF4J를 사용하는 로깅 프레임워크 (예: Logback, Log4j 2)와 통합

## log4jdbc.dump.sql.maxlinelength
## -> SQL 쿼리를 로깅할 때 한 줄로 출력할 최대 길이를 지정
## -> 쿼리가 너무 길어질 경우 이를 줄여서 출력할 수 있도록
## -> 0 => 최대 길이를 제한하지 않음을 의미
## ->   => SQL 쿼리를 로그에 출력할 때 길이 제한 없이 전체 쿼리를 한 줄로 출력

log4jdbc.spylogdelegator.name=net.sf.log4jdbc.log.slf4j.Slf4jSpyLogDelegator

log4jdbc.dump.sql.maxlinelength=0
```
