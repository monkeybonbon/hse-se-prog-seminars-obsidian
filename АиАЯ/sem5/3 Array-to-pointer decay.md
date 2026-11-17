
При использовании в выражении имя массива почти всегда превращается в указатель на первый элемент этого массива. Но есть несколько исключений:

## sizeof
```c
#include <stdio.h>

int main(void) {
	int a[5];
	int* p = &a[0];
	int* p2 = a;
	
	printf("%lld %lld %lld", sizeof(a), sizeof(p), sizeof(p2));
	
	return 0;
} 
```

## Взятие адреса
```c
#include <stdio.h>

#define IS_TYPE(x, type) \
    __builtin_types_compatible_p(__typeof__(x), type)

int main(void) {
    int a[5];
    int *p = a;

    printf("a is int[5]: %d\n", IS_TYPE(a, int[5]));
    printf("&a is int (*)[5]: %d\n", IS_TYPE(&a, int (*)[5]));
    printf("p is int*: %d\n", IS_TYPE(p, int*));

    return 0;
}
```

**GDB:**
```gdb
break main
run
ptype a
ptype &a
ptype &a[0]
ptype p
```


## Изменение строк

```c
#include <stdio.h>

int main(void) {
	char str[6] = "Hello";
	char *p = "Hello";
	str[0] = 'h'; // OK
	// p[0] = 'h'; // Error
	
	printf("%s %s", str, p);
	return 0;
}
```

# Различие между указателем и массивом

> Массив – имя области памяти фиксированного размера. 
> Указатель – переменная, которая располагается в памяти и хранит адрес определённого типа. 
> Имя массива навсегда ассоциировано с конкретным адресом в памяти, указатель можно переприсвоить.

