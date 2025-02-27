## leadz

### **Name**

**leadz**(3) - \[BIT:COUNT\] Number of leading zero bits of an integer

### **Syntax**

```fortran
result = leadz(i)
```

### **Description**

**leadz** returns the number of leading zero bits of an integer.

### **Arguments**

- **i**
  : Shall be of type _integer_.

### **Returns**

The type of the return value is the same as a default _integer_. If all
the bits of **i** are zero, the result value is **bit_size(i)**.

### **Examples**

Sample program:

```fortran
program demo_leadz
implicit none
integer :: value, i
character(len=80) :: f
  write(*,'(*(g0))')'BIT_SIZE=',bit_size(value)
  ! make a format statement for writing a value as a bit string
  write(f,'("(b",i0,".",i0,")")')bit_size(value),bit_size(value)
  ! show output for various integer values
  value=0
  do i=0,bit_size(value)-1
     write (*,'("LEADING ZERO BITS=",i3,1x)') leadz(value)
     write (*,'(" FOR VALUE ")',advance='no')
     write(*,f,advance='no') value
     write(*,'(*(1x,g0))') "OR",value
     value=value+2**(i)
  enddo
end program demo_leadz
```

Results:

```
   BIT_SIZE=32
   LEADING ZERO BITS= 32
    FOR VALUE 00000000000000000000000000000000 OR 0
   LEADING ZERO BITS= 31
    FOR VALUE 00000000000000000000000000000001 OR 1
   LEADING ZERO BITS= 30
    FOR VALUE 00000000000000000000000000000011 OR 3
   LEADING ZERO BITS= 29
    FOR VALUE 00000000000000000000000000000111 OR 7
   LEADING ZERO BITS= 28
    FOR VALUE 00000000000000000000000000001111 OR 15
   LEADING ZERO BITS= 27
    FOR VALUE 00000000000000000000000000011111 OR 31
   LEADING ZERO BITS= 26
    FOR VALUE 00000000000000000000000000111111 OR 63
   LEADING ZERO BITS= 25
    FOR VALUE 00000000000000000000000001111111 OR 127
   LEADING ZERO BITS= 24
    FOR VALUE 00000000000000000000000011111111 OR 255
   LEADING ZERO BITS= 23
    FOR VALUE 00000000000000000000000111111111 OR 511
   LEADING ZERO BITS= 22
    FOR VALUE 00000000000000000000001111111111 OR 1023
   LEADING ZERO BITS= 21
    FOR VALUE 00000000000000000000011111111111 OR 2047
   LEADING ZERO BITS= 20
    FOR VALUE 00000000000000000000111111111111 OR 4095
   LEADING ZERO BITS= 19
    FOR VALUE 00000000000000000001111111111111 OR 8191
   LEADING ZERO BITS= 18
    FOR VALUE 00000000000000000011111111111111 OR 16383
   LEADING ZERO BITS= 17
    FOR VALUE 00000000000000000111111111111111 OR 32767
   LEADING ZERO BITS= 16
    FOR VALUE 00000000000000001111111111111111 OR 65535
   LEADING ZERO BITS= 15
    FOR VALUE 00000000000000011111111111111111 OR 131071
   LEADING ZERO BITS= 14
    FOR VALUE 00000000000000111111111111111111 OR 262143
   LEADING ZERO BITS= 13
    FOR VALUE 00000000000001111111111111111111 OR 524287
   LEADING ZERO BITS= 12
    FOR VALUE 00000000000011111111111111111111 OR 1048575
   LEADING ZERO BITS= 11
    FOR VALUE 00000000000111111111111111111111 OR 2097151
   LEADING ZERO BITS= 10
    FOR VALUE 00000000001111111111111111111111 OR 4194303
   LEADING ZERO BITS=  9
    FOR VALUE 00000000011111111111111111111111 OR 8388607
   LEADING ZERO BITS=  8
    FOR VALUE 00000000111111111111111111111111 OR 16777215
   LEADING ZERO BITS=  7
    FOR VALUE 00000001111111111111111111111111 OR 33554431
   LEADING ZERO BITS=  6
    FOR VALUE 00000011111111111111111111111111 OR 67108863
   LEADING ZERO BITS=  5
    FOR VALUE 00000111111111111111111111111111 OR 134217727
   LEADING ZERO BITS=  4
    FOR VALUE 00001111111111111111111111111111 OR 268435455
   LEADING ZERO BITS=  3
    FOR VALUE 00011111111111111111111111111111 OR 536870911
   LEADING ZERO BITS=  2
    FOR VALUE 00111111111111111111111111111111 OR 1073741823
   LEADING ZERO BITS=  1
    FOR VALUE 01111111111111111111111111111111 OR 2147483647
```

### **Standard**

Fortran 2008 and later

### **See Also**

[**bit_size**(3)](BIT_SIZE),
[**popcnt**(3)](POPCNT),
[**poppar**(3)](POPPAR),
[**trailz**(3)](TRAILZ)

####### fortran-lang intrinsic descriptions
