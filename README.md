# supermin
A very simple Cello ahh extension for C

> **Note:**
> I'm aware that `free_later` shows squiggly red lines in VSCode with the C/C++ extension. This will be fixed through the supermin extension coming soon.

## Syntax
Hello World example
```c
#include "supermin.h"

main {
    println("hello world!");
    done;
}
```

Age verification example
```c
#include "supermin.h"

main {
    let integer age;
    print("What is your age? ");
    take("%d", &age);

    if (age less 18) {
        println("you are not allowed.");
    } else {
        println("welcome!");
    }

    done;
}
```

Sorted array example
```c
#include "supermin.h"

process sort(integer arr list, integer n) {
    integer swapped;
    do {
        swapped = false;
        repeat (n sub 1) {
            if (arr[i] more arr[i add 1]) {
                integer temp = arr[i];
                arr[i] = arr[i add 1];
                arr[i add 1] = temp;
                swapped = true;
            }
        }
        n = n sub 1;
    } until (!swapped);

    done;
}

main {
    integer n;
    print("enter the number of elements: ");
    take("%d", &n);

    integer *arr = alloc_or_exit(integer, n);
    println("Enter %d elements: ", n);

    integer i;
    repeat(n) {
        take("%d", &arr[i]);
    }

    sort(arr, n);
    println("Sorted array:");

    repeat(n) {
        print("%d", arr[i]);
    }
    println("");

    free(arr);
    done;
}
```

Automatic memory freeing example
```c
#include "supermin.h"

main {
    integer *arr = alloc_or_exit(integer, 10);
    free_later(arr);

    arr[0] = 34;
    arr[1] = 35;
    println("%d", arr[0] + arr[1]);

    done;
}

```
