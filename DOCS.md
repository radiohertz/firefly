

# Format API

The current format API only supports formatting numbers, strings and pointers.

It supports formatting numbers in Binary, Octal, Decminal and Hexadecimal.in Binary, Octal, Decminal and Hexadecimal


# Example usage
```
#include <format/format.h>

int main()
{
    formatter f;
    auto [str, len] = f.format("Hello, ", "World");
    // str - pointer to the formatted null terminated string.
    // len - length of the formatted string. (doesn't account for null terminator)
}
```

The API also supports formatting user-defined types.

Types which implement the member function `T::format(Formatter&) const` are eligible.


# Eaxmple
```c
#include <format/format.h>

struct User {
    int pid;
    const char* name;
    
    void format(Formatter& fmt)
    {
        fmt.tfmt("PID: ", pid, "\t NAME: ", name);
    }
};

int main()
{
    User u = {
        .pid = 1,
        .name = "Admin"
    };

    formatter f;
    auto [str, len] = f.format("User: ", u, "\n");
}

```