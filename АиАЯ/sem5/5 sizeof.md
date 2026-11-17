> `sizeof(a)` возвращает **размер в байтах** типа переменной a

Выражение внутри sizeof не вычисляется - только берется его тип

```c
#include <stdio.h>

int main(void) {
    printf("char:   %zu\n", sizeof(char));
    printf("short:  %zu\n", sizeof(short));
    printf("int:    %zu\n", sizeof(int));
    printf("long:   %zu\n", sizeof(long));
    printf("double: %zu\n", sizeof(double));
    
    int a[5];

	printf("%zu\n", sizeof(a));
	printf("%zu\n", sizeof(&a));
	printf("%zu\n", sizeof(*(&a)));

    return 0;
}
```
