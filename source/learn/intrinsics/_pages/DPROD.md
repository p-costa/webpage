## dprod

### **Name**

**dprod**(3) - \[NUMERIC\] Double product function

### **Syntax**

```fortran
result = dprod(x, y)
```

### **Description**

**dprod(x,y)** produces a higher _doubleprecision_ product of default _real_
numbers **x** and **y**.

The result has a value equal to a processor-dependent approximation to
the product of **x** and **y**. It is recommended that the processor compute the
product in double precision, rather than in single precision and then
converted to double precision.

- **x**
  : shall be default real.

- **y**
  : shall be default real.

The setting of compiler options specifying _real_ size can affect this
function.

### **Arguments**

- **x**
  : Must be of default _real(kind=kind(0.0))_ type

- **y**
  : Must have the same type and kind parameters as **x**

### **Returns**

The return value is of type _real(kind=kind(0.0d0))_.

### **Examples**

Sample program:

```fortran
program demo_dprod
use, intrinsic :: iso_fortran_env, only : real_kinds, &
& real32, real64, real128
implicit none
integer,parameter :: dp=kind(0.0d0)
real :: x = 5.2
real :: y = 2.3
real(kind=dp) :: dd
   dd = dprod(x,y)
   print *, dd, x*y, kind(x), kind(dd), kind(dprod(x,y))
   ! interesting comparisons
   print *, 52*23
   print *, 52*23/100.0
   print *, 52*23/100.0d0

   !! common extension is to take doubleprecision arguments
   !! and return higher precision
   bigger: block
   doubleprecision :: xx = 5.2d0
   doubleprecision :: yy = 2.3d0
   real(kind=real128) :: ddd
   !ddd = dprod(xx,yy)
   !print *, ddd, xx*yy, kind(xx), kind(ddd), kind(dprod(xx,yy))
   endblock bigger

end program demo_dprod
```

Results:

```text
   11.959999313354501 11.9599991 4 8 8
        1196
   11.9600000
   11.960000000000001
```

### **Standard**

FORTRAN 77 and later

####### fortran-lang intrinsic descriptions
