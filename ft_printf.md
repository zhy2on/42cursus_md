# FT_PRINTF
## 기본 개요
* printf를 구현한다.
* mandatory part는 specifier로 csdiupxX%만 구현하면 된다.

## 구현 개요
* 문자열 format과 가변인자를 받는다. printf("format", 변수) 꼴
* format 안에서 %를 만날 때까지 출력한다.
* %를 만나면 flag, precision, specifier에 대한 정보를 분석한다.
* specifier를 만날 때까지가 printf에서 지정한 서식의 영향이 유효한 범위이다.
* 

## 자료 정리
* printf
  * 인자: 문자열, 가변인자
  * printf는 첫 번째 인자로 출력하고자 하는 포맷 문자열을 전달한다.
  * 포맷 지정 문자열의 ``%``문자는 변환 사양 문자로 flags와 길이 수정자가 옵션으로 올 수 있다.
  * 포맷 지정자 문자인 ``diouxXaAeEfFgG%`` 중 하나를 사용한다. <https://ehpub.co.kr/24-printf-%ED%95%A8%EC%88%98/>
  * ``%[플래그(flag)][폭(width)][.정밀도(precision)][크기(length)]서식 문자(specifier)`` <https://modoocode.com/35>
* stdarg.h
  * C언어에서 ``stdarg.h`` 헤더를 사용하면 함수 선언 시 가변 인자(Variable arguments)를 가질 수 있다.
  * ``stdarg.h`` 헤더파일은 자료형으로 ``va_list``를 가지며, 함수로 ``va_start``, ``va_arg``, ``va_end`` 등의 함수를 포함하고 있다.
* 가변인자
  * 가변인자를 사용하기 위해선 최소 한 개 이상의 고정인수가 있어야 하며 ``...``은 파라미터 순서상 가장 마지막에 위치해야 한다.
* va_start
  * argument pointer를 고정인수 다음 위치로 초기화 시킨다. 
* mac os 환경과 wsl 환경에서 플래그 위치에 따른 차이
  * mac os에서는 서식 위치가 바뀌거나 0 flag가 c와 같이 오는 경우도 알아서 출력을 해준다. 여기에 맞춰서 ft_printf를 구현해야 한다.

  |mac os|wsl|
  |---|---|
  |![image](https://user-images.githubusercontent.com/52701529/125905615-0faaeb96-0ac8-46a9-98ae-4e381261c315.png)|![image](https://user-images.githubusercontent.com/52701529/125905514-54bf5c66-e88b-46dd-9bfc-d77508be7566.png)|
  |![image](https://user-images.githubusercontent.com/52701529/125905699-4952d24f-c732-44ad-94e9-c5796ee37f06.png)|![image](https://user-images.githubusercontent.com/52701529/125905803-f7750758-1137-40d5-bc1b-f94fbc59f8c3.png)|
  |![image](https://user-images.githubusercontent.com/52701529/126031506-9b0ad7a2-0f9a-4b84-b7da-9742e1117f6b.png)|![image](https://user-images.githubusercontent.com/52701529/126031524-f9c602d6-8cab-4dda-9e09-bc6837927734.png)


