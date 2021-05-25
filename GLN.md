# get_next_line
## 기본 개요
* fd에 있는 내용 read로 BUFFER_SIZE만큼 읽어오면서 static 변수에 저장하고, 해당 변수에서 '\n' 찾고 만약에 있다면, 그 위치까지만 다시 strdup 해서 line에 갱신해준다.
* 
