---
date: '2025-01-21T10:38:06-05:00'
draft: false
title: 'Resource Acquisition Is Initialization'
ShowShareButtons: true
---

Resource acquisition is initialization (RAII) refers to a programming technique for resource management where the resource acquired by an object when it is initialized is released when the object is destroyed. [^1] A resource here is anything that there is a fixed quantity of and requires an acquisition process to be used and a release process to be freed. One common example of a resource is dynamically allocated heap memory.

To explain RAII by example, I will use the example of memory management using programs written in C++. 

### Wait, so what?

Not managing resources properly can lead to costly mistakes. For example, improper memory management can lead to memory leaks [^2] or use-after-free vulnerabilities [^3]. Google acknowledged that the use of memory safe development practices reduced the percentage of memory safety vulnerabilities from 76% to 24% in Android. [^4]

Now, returning to our example...

### The setup

For the sake of simplicity, the example will involve allocation of memory on the heap for a floating point variable.

A variable `x` declared on the heap is assigned `3.14`, used and then deleted, freeing up the memory allocated to it when it was declared. Trying to access it after it has been deleted causes "undefined behavior" that is dependent on the compiler you use, as deletion of the resource associated with `x` makes it a dangling pointer.

```cpp
#include <iostream>

int main() {
    float* x = new float;
    *x = 3.14; 
    std::cout << *x << "\n";
    delete x;
    // *x = 43.12;
    return 0;
}
```

### Encapsulation

To simplify things and take advantage of C++'s object oriented programming features, we can encapsulate this behavior in a custom class, where the constructor can allocate the required memory and the destructor can release it when the instance goes out of scope.

```cpp
...
class RAIIFloat {
private: 
    float* data;

public:
     RAIIFloat(float value) {
        data = new float;
        *data = value;
    }

    ~RAIIFloat() {
        delete data;
        data = nullptr;
    }

    void print() const {
        std::cout << *data << "\n";
    }
};

int main() {
    RAIIFloat x(3.14);
    x.print();
    return 0;
}
```

No dangling pointers, no `new`, no `delete`! And yet, consider the following:

```cpp
...
int main() {
    RAIIFloat x(3.14);
    x.print();
    RAIIFloat y = x;
    y.print();
    return 0;
}
```
The program compiles fine, yet the error occurs at runtime when both `x` and `y` are destroyed. When `y` is assigned the value of `x` it effectively points `y` to the same resource (memory) as `x`, i.e. creating a shallow copy. So when the resource associated with `x` gets freed at the end of `x`'s _lifetime_, the destruction of `y` complains of attempting to free a resource that already has been freed.

`RAIIFloat` thus lacks an essential trait of RAII, which is that when the resource associated with an object is released, _the object should also die_. To correct this discrepancy we can either create a deep-copy of the object, or move it entirely to the new object (_single ownership_).

### Deep-copy while retaining ownership

We can modify the copy constructor to perform a deep-copy instead of a shallow copy (also modifying the copy assignment operator to make deep copies).

```cpp
class RAIIFloat {
public:
...
    RAIIFloat(const RAIIFloat& other) {
        data = new float(*(other.data));
    }
    RAIIFloat& operator=(const RAIIFloat &other) {
        if (data) {
            if (data != other.data) {
                *data = *(other.data)
            }
        } else {
            data = new float(*(other.data));
        }
        return *this;
    };
...
};
```

The new copy constructor (and copy assignment constructor) makes acquisition and release of resources predictable and bound to the lifetime of the object.

### Ownership transfer, a.k.a. move semantics

Alternatively, we can use _move semantics_ in C++ to transfer ownership of a resource to the new object once it is reassigned. This transfer of ownership promotes reuse of existing resources and preserves adherence to RAII principles. Note that for simplicity, in this example we disable the copy constructor instead.

```cpp
class RAIIFloat {
public:
...
    RAIIFloat(RAIIFloat&& other) {
        data = other.data;
        other.data = nullptr;
    }

    RAIIFloat& operator=(RAIIFloat&& other) {
        if (data != other.data) {
            delete data;
            data = other.data;
            other.data = nullptr;
        }
        return *this;
    }

    RAIIFloat(const RAIIFloat&) = delete;
    RAIIFloat& operator=(const RAIIFloat &) = delete;
...
};
```
As a result, ownership is now moved to the new object on assignment.

```cpp
...
int main() {
    RAIIFloat x(3.14);
    x.print();
    RAIIFloat y = std::move(x);
    y.print();
    // x.print();
    return 0;
}
```

Calling `x.print()` segfaults as `x` no longer owns the memory it was originally assigned.

### Conclusion

RAII is a programming pattern that ensures efficient and predictable allocation and cleanup of resources (file handles, heap memory, etc.) by tying the initiation and termination of their usage to the lifetime of the entity that invokes them. Using constructors and destructors provided in a programming language that facilitates an object oriented programming paradigm makes the implementation of RAII clean and programmer-friendly.

[^1]: **Stroustrup, B. (2001).** Exception safety: concepts and techniques. In Advances in exception handling techniques (pp. 60-76). Berlin, Heidelberg: Springer Berlin Heidelberg.
[^2]: **OWASP Foundation.** Memory leak. OWASP. Retrieved January 21, 2025, from https://owasp.org/www-community/vulnerabilities/Memory_leak
[^3]: **Kaspersky.** Use-After-Free. Kaspersky IT Encyclopedia. Retrieved January 21, 2025, from https://encyclopedia.kaspersky.com/glossary/use-after-free/
[^4]: **Vander Stoep, J., & Rebert, A. (2024, September 25).** Eliminating memory safety vulnerabilities at the source. Google Security Blog. Retrieved January 21, 2025, from https://security.googleblog.com/2024/09/eliminating-memory-safety-vulnerabilities-Android.html
