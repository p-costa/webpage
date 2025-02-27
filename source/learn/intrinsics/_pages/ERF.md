## erf

### **Name**

**erf**(3) - \[MATHEMATICS\] Error function

### **Syntax**

```fortran
result = erf(x)
```

### **Description**

**erf**(x) computes the error function of **x**, defined as

$$
\text{erf}(x) = \frac{2}{\sqrt{\pi}} \int_0^x e^{__-t__^2} dt.
$$

### **Arguments**

- **x**
  : The type shall be _real_.

### **Returns**

The return value is of type _real_, of the same kind as **x** and lies in the
range **-1** \<= **erf**(x) \<= 1 .

### **Examples**

Sample program:

```fortran
program demo_erf
use, intrinsic :: iso_fortran_env, only : real_kinds, &
 & real32, real64, real128
implicit none
real(kind=real64) :: x = 0.17_real64
    write(*,*)x, erf(x)
end program demo_erf
```

Results:

```text
     0.17000000000000001       0.18999246120180879
```

### **Standard**

Fortran 2008 and later

### See also

[**erfc**(3)](ERFC)

- [Wikipedia:error function](https://en.wikipedia.org/wiki/Error_function)

####### fortran-lang intrinsic descriptions
