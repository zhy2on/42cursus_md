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
* 이전 코드에서 strlen을 사용해서 구현했을 때 war machine에서 bus error 났었음. 원인이 뭘까?
```c
size_t	ft_strlcat(char *dst, const char *src, size_t dstsize)
{
	size_t i;
	size_t j;

	i = 0;
	j = 0;
	while (dst[i] && i < dstsize)
		i++;
	while (src[j] && (i + j + 1) < dstsize)
	{
		dst[i + j] = src[j];
		j++;
	}
	if (i < dstsize)
		dst[i + j] = '\0';
	return (i + ft_strlen(src));
}
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

### atoi
* C04 - 03문제에서 int형 범위 말고 unsigned long long까지 고려해야 함.
* 문자열을 정수로 바꾸는 함수.
* 문자열 길이가 20넘어가면 양수일 때 -1, 음수일 때 0으로 값이 고정됨.
* 피신에서는 +, -가 여러 번 반복 돼도 됐었는데, 원래 atoi함수에서는 두 개 이상 넘어가면 안 됨. while문을 if문으로 바꾸어 부호 검사하고, 그 다음부턴 while문으로 숫자 검사하면 올바르게 고쳐진다.
```c
int		ft_atoi(const char *str)
```

### isalpha
* 알파벳이면 1 아니면 0

### isdigit
* 숫자면 1 아니면 0

### isalnum
* 알파벳 또는 숫자면 1 아니면 0

### isascii
* 아스키범위 내 값이면 1 아니면 0

### isprint
* printable이면 1 아니면 0
* 0~31, 127

### toupper
* 소문자를 대문자로

### tolower
* 대문자를 소문자로

### calloc
* malloc과 같은데, 대신 할당된 공간을 0으로 채워줌.
* 앞에서 구현했던 bzero를 사용하여 메모리를 0으로 채워주면 된다.
* size에 자료형 크기가 들어가는 거고, count에 size 크기 자료형 몇 개만큼의 공간 할당할 건지 적어주면 된다. 최종적으로 count * size크기만큼의 공간이 할당 되는 것이다.
```c
void	*ft_calloc(size_t count, size_t size);
```

### strdup
* 공간을 malloc으로 할당해주고, 해당 공간에 복사하고 주소 리턴해주는 함수.
* C07 - 00문제
* strdup
  - strdup() 함수는 문자 s 를 복사하고 복사된 문자열을 가리키는 포인터를 반환한다. 문자를 복사할 공간을 확보하기 위해서 내부적으로 malloc(3)이 호출된다.
  - 복사된 문자열의 주소를 가리키는 포인터를 반환한다. 에러발생시에는 NULL 을 되돌려준다.

* malloc
  - memory allocation
  - 동적할당이라는 것은 프로그램 실행중에 동적으로 메모리를 할당하는 것을 말한다.
  - 함수 원형은 void* malloc(size_t size) 로, 동적할당 후 해당 데이터 타입으로 형변환을 해줘야 한다. 또한 메모리 크기는 자료형마다 다르기 때문에 sizeof()을 사용하여 자료형의 크기에 원하는 할당 크기를 곱해준다.

```c
char	*ft_strdup(const char *src);
```

### ft_substr
* s에서 start부터 len까지 substring 만들어서 반환.
* s가 빈 문자열이거나, start위치가 s의 길이를 넘어가는 경우 예외처리.
* 마지막에 널문자 붙여서 반환해준다.
```c
char	*ft_substr(char const *s, unsigned int start, size_t len)
```

### ft_strjoin
* s1에 s2를 붙인다.
* s1이나 s2가 널이면 예외처리 한다.
```c
char	*ft_strjoin(char const *s1, char const *s2)
```

### ft_strtrim
