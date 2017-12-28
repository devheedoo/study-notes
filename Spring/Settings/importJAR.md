### 문제
lib 폴더에 jar를 추가해줘도 에러가 발생했다.

### 해결 시도

- http://denodo1.tistory.com/282

pom.xml 파일에 다음과 같이 dependency를 추가해준다.

```xml
<!-- simplecaptcha 1.2.1 -->
<dependency>
  <groupId>nl.captcha</groupId>
  <artifactId>simplecaptcha</artifactId>
  <version>1.2.1</version>
  <scope>system</scope>
  <systemPath>${project.basedir}/webapps/WEB-INF/lib/simplecaptcha-1.2.1.jar</systemPath>
</dependency>
```

실패했다. 빌드 로그에 프로젝트 내부 경로를 systemPath로 사용하지 말라는 Warning이 나타난다.

### 해결

- https://mvnrepository.com/artifact/oracle/ojdbc/1.4

원래 형태대로 pom.xml 파일에 적어준 후 레포지토리 사이트에 접속해서 변경된 원격지 주소를 상단에 적어준다.

```xml
<!-- ojdbc 1.4 -->
<repository>
  <id>repo.adobe.com</id>
  <url>https://repo.adobe.com/nexus/content/repositories/public/</url>
</repository>
...
<!-- https://mvnrepository.com/artifact/oracle/ojdbc -->
<dependency>
  <groupId>oracle</groupId>
  <artifactId>ojdbc</artifactId>
  <version>1.4</version>
</dependency>
```

잘 해결되었다.
