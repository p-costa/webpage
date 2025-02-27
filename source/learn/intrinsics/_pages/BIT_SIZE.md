## bit_size

### **Name**

**bit_size**(3) - \[BIT:INQUIRY\] Bit size inquiry function

### **Syntax**

```fortran
    result = bit_size(i)

     function(kind=KIND) :: bit_size
     integer(kind=KIND),intent(in) :: ii
```

### **Description**

**bit_size(i)** returns the number of bits (integer precision plus sign
bit) represented by the type of the _integer_ **i**. **i** can be a
scalar or an array.

### **Arguments**

- **i**
  : An _integer_ value of any kind to determine the size of in bits.
  Because only the type of the argument is examined, the argument need
  not be defined.

### **Returns**

    Returns the number of bits used to represent a value of the type
    of __i__.  The result is a _integer_ scalar of the same kind as __i__.

### **Examples**

Sample program:

```fortran
program demo_bit_size
use,intrinsic :: iso_fortran_env, only : int8, int16, int32, int64
implicit none
integer(kind=int64)          :: answer
integer                      :: ilen
character(len=*),parameter   :: fmt='(*(g0,1x))'
    write(*,fmt)'default integer size is',bit_size(0),'bits'
    write(*,fmt)bit_size(bit_size(0_int8)), 'which is kind=',kind(0_int8)
    write(*,fmt)bit_size(bit_size(0_int16)),'which is kind=',kind(0_int16)
    write(*,fmt)bit_size(bit_size(0_int32)),'which is kind=',kind(0_int32)
    write(*,fmt)bit_size(bit_size(0_int64)),'which is kind=',kind(0_int64)

    ! Check size of value not explicitly defined.
    write(*,fmt) int(bit_size(answer))
end program demo_bit_size
```

Typical Results:

```text
   default integer size is 32 bits
   8 which is kind= 1
   16 which is kind= 2
   32 which is kind= 4
   64 which is kind= 8
   64
```

### **Standard**

Fortran 95 and later

####### fortran-lang intrinsic descriptions (license MIT) @urbanjost
