# Libft
## Part1

### memset
* 메모리를 채운다. b에 c를 len만큼 채운다.
* size_t --> 부호 없는 정수형. 32비트 운영체제에선 부호 없는 32비트 정수, 64비트 운영체제에선 부호 없는 64비트 정수.
```c
void  *(void *b, int c, size_t len)
```

### bzero
* memset이랑 비슷한데 이건 따로 채울 데이터를 정해 주는 게 아니라 무조건 0으로 채운다.
* memset을 만들었으니, memset에 채울 데이터 c를 0으로 해서 전달해주면 된다.
```c
void  (void *s, size_t n)
```

### memcpy
* 말 그대로 메모리 카피함수.
```c
void  *(void *dst, const void *src, size_t n)
```

### memccpy
* n개 복사하는데 도중에 c만나면 c다음 주소 리턴.(복사 쉽게 하기 위해서)
* 못 만나면 리턴 널
```c
void	*ft_memccpy(void *dst, const void *src, int c, size_t n)
```

### memmove
* dst < src면 dst 처음부터 복사. overlapped 방지 위해.
* dst > src면 그냥 뒤에서부터 복사. memcpy가 뒤에서부터 복사하게 구현했기 때문에 이 때 memcpy 사용.
```c
void	*memmove(void *dst, const void *src, sieze_t len)
```

### memchr
* 문자열 s에서 unsigned char c를 n범위 안에서 조사.
* c 형변환 필요.
* const void 포인터로는 값을 비교할 수 없다. 변환한 뒤 역참조 하는 식으로 진행해야 한다.
```c
void	*ft_memchr(const void *s, int c, size_t n)
```

### memcmp
* strcmp랑 비슷하다. 대신 이것도 const void가 아니라 const unsigned char로 변환한 뒤 사용해야 한다.
```c
int	ft_memcmp(const void *s1, const void *s2, size_t n)
```

### strlen
* 문자열 길이 구하는 함수
```c
size_t	ft_strlen(const char *s);
```

### strlcpy
* c02-10. 크기 제한 문자열 복사 함수. NULL 종료를 보장해야 한다.
* size - 1 만큼 복사하고 마지막 문자를 널로 채운다.
* strlcpy, strlcat은 생성하려고 한 문자열 전체 길이를 반환한다. strlcpy에서는 src의 길이가 반환된다.
```c
size_t	strlcpy(char *dst, const char *src, size_t dstsize)
```

### strlcat
* c03-05
* <https://whatdocumentary.tistory.com/45>
*  strcat 함수와 동일하다. 보안 목적을 위해 strcat 대신 사용한다.
* 복사될 문자열의 길이는 size - dst_len - 1(\0)이다. 끝에 널문자를 삽입한다.
*  반환값은 dst와 복사된 src의 길이의 총합이다. 여기에는 NULL 값은 제외되어 계산된다.
    - 여기서 예외 처리를 size가 dst길이 보다 작으면 그냥 리턴 0 되게 했었는데 그렇게 하면 안 됐었다.
    - <https://m.blog.naver.com/PostView.nhn?blogId=01191879872&logNo=221111654384&proxyReferer=https:%2F%2Fwww.google.com%2F>
    - 여기서 보면 strlen(src)는 고정이고, dest가 size보다 작으면 srclen + size, dest가 size보다 크면 srclen + dstlen이 되어야 한다.
* size가 아무리 커도 src_len만큼 복사되고 끝난다.

* j < src_len 은 src범위를 벗어나는 곳을 접근하는 것을 방지해준다. (dest_len + j) + 1 < size 는 dest_len을 제외한 size - 1만큼만 복사가 될 수
 있도록 한다. 마지막 널문자를 추가해주기 위함이다.
```c
size_t	ft_strlcat(char *dst, char *src, size_t dstsize);
```

### strchr
* 문자열 s에서 char형 c가 "처음" 나타나는 위치 반환.
* 문자열 끝을 나타내는 널문자까지 포함하여 검색해야 한다. 
```c
char	*ft_strchr(const char *s, int c);
```

### strrchr
* 문자열 s에서 char형 c가 "마지막으로" 나타나는 위치 반환.
* 문자열 끝을 나타내는 널문자까지 포함하여 검색해야 한다.
* size_t는 unsigned int!! while (i >= 0) 이렇게 하면 안 되고 while (i > 0) 이렇게 사용하기.
```c
char	*ft_strrchr(const char *s, int c);
```

### strnstr
* 문자열 haystack에서 문자열 needle이 "처음" 나타나는 위치 반환.
* 대신 n길이 내에서 검색.
* 이 때 haystack 앞에서부터 n 길이만큼의 범위 사이에서만 검색한다는 거.
```c
char	*ft_strnstr(const char *haystack, const char *needle, size_t len);
```

### strncmp
* n개만큼 문자열 비교 함수.
```c
int	ft_strncmp(const char *s1, const char *s2, size_t n);
```



