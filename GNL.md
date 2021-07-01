# get_next_line
## 기본 개요
* fd에 있는 내용 read로 BUFFER_SIZE만큼 읽어오면서 static 변수에 저장하고, 해당 변수에서 '\n' 찾고 만약에 있다면, 그 위치까지만 다시 strdup 해서 line에 갱신해준다.
* 파일을 읽는 중 오류가 있었을 경우 -1, 라인을 올바로 읽어들인 경우 1, 파일을 모두 읽었을 경우 0을 반환한다.

## 함수 개요
```c
int	get_next_line(int fd, char **line);
```
  * 메인 함수. fd의 내용을 read를 이용해 BUFFER_SIZE만큼 buf에 담으며 읽는다. rsize가 0보다 큰 경우 while문을 돌며 static char* 변수인 backup에 buf를 계속 붙여간다.
  * buf에 개행이 있으면 탈출한다.
  * return_case 함수를 리턴값으로 갖는다.  
```c
int	return_case(char **backup, char **line, int rsize);
```
  * get_next_line에서 받은 backup과 rsize를 가지고 line에 어떤 값을 넣어야 하는지, 어떤 값을 리턴해야 하는지 결정한다.
  * rsize < 0 인 경우 -1을 리턴한다.
  * backup이 존재하는 경우
  * 개행이 존재한다면, update_line 함수를 이용해 line에 개행 전까지의 내용을 할당해주고 1을 리턴한다.
  * 개행이 존재하지 않는다면, backup을 그대로 line에 할당해주고 0을 리턴한다.
  * backup이 존재하지 않는 경우 "\0" 문자열을 line에 할당해주고 0을 리턴한다.
```c
int	update_line(char **backup, char **line, char *pcut);
```
  * 개행 전까지 line에 할당해주고 기존의 bakcup을 free한 후 개행 다음부터의 내용을 다시 backup에 할당한 후 1을 리턴한다.

## 비고
* 동적할당을 한 경우 메모리 해제를 확인 또 확인하자. free 위치를 잘 확인해두고, 그 전에 리턴이 되었거나 하진 않는지 확인하기.
* 처음엔 어차피 동적할당이니까 파일을 무조건 끝까지 읽고, backup에서 개행을 처리하는 게 낫다고 생각하였는데 파일이 여러 줄로 구성된 큰 용량일 때, 개행을 만날 때마다 적절히 처리해주면서 진행하는 것이 속도가 훨씬 빨랐다. backup의 크기도 훨씬 커질 수밖에 없고.. 
* 디버깅 할 때 출력문 위주로 판단해 보기.
