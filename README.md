# opensource

## 1) **getopt**
* 옵션을 나타냄
* 예상되는 플래그와 인수를 지정하는 형식을 사용하여 토큰 리스트를 구문 분석함
* 여기서 플래그는 단일 ASCII 문자이며 뒤에 콜론(:)이 올 경우 하나 이상의 탭 또는 공백으로 분리하거나 분리할 수 없는 인수가 필요함
* 인수에는 복수 바이트를 포함시킬 수 있지만 플래그 문자로는 포함시킬 수 없음
* 모든 토큰을 읽은 후 또는 특수 토큰 -(더블 하이픈)이 발생하는 경우 처리를 완료함
* 처리된 플래그, -(더블 하이픈)과 남아 있는 토큰을 출력
* 토큰이 플래그와 일치하지 않을 경우 메시지를 표준 오류에 기록함

##### 예제
```shell
#!/bin/bash
set -- $(getopt -q abc:d "$@")

while [ -n "$1" ]
do
  case "$1" in
     -a) echo "-a option";;
     -b) echo "-b option";;
     -c) echo "-c option";;
     --) shift
     break ;;
     *) echo "$1 not option";;
   esac
   shift
done

cnt=1
for arg in "$@"
do
  echo "argument #$cnt: $arg"
  cnt=$[ $cnt + 1 ]
done
```
  

##### 파일 위치
/usr/bin/getopt

