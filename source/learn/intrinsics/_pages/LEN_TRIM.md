## len_trim

### **Name**

**len_trim**(3) - \[CHARACTER:WHITESPACE\] Length of a character entity without trailing blank characters

### **Syntax**

```fortran
   result = len_trim(string, kind)

    integer(kind=KIND) function len_trim(string,KIND) result (value)
    character(len=*),intent(in) :: string
    integer,optional,intent(in) :: KIND
    integer(kind=KIND) :: value
```

### **Description**

Returns the length of a character string, ignoring any trailing blanks.

### **Arguments**

- **string**
  : The input string whose length is to be measured.
  Shall be a scalar of type _character_

- **kind**
  : (Optional) An _integer_ initialization expression indicating the kind
  parameter of the result.

### **Returns**

The return value is of type _integer_ and of kind **kind**. If **kind** is absent,
the return value is of default _integer_ kind.

### **Examples**

Sample program

```fortran
program demo_len_trim
implicit none
character(len=:),allocatable :: string
   string=' how long is this string?     '
   write(*,*)'LENGTH=',len(string)
   write(*,*)'TRIMMED LENGTH=',len_trim(string)
   !
   ELE:block ! elemental example
   character(len=:),allocatable :: tablet(:)
   tablet=[character(len=256) :: &
   & ' how long is this string?     ',&
   & 'and this one?']
      write(*,*)'LENGTH=            ',len(tablet)
      write(*,*)'TRIMMED LENGTH=    ',len_trim(tablet)
      write(*,*)'SUM TRIMMED LENGTH=',sum(len_trim(tablet))
   endblock ELE
   !
end program demo_len_trim
```

Results:

```
    LENGTH=          30
    TRIMMED LENGTH=          25
    LENGTH=                     256
    TRIMMED LENGTH=              25          13
    SUM TRIMMED LENGTH=          38
```

### **Standard**

Fortran 95 and later, with **kind** argument - Fortran 2003
and later

### **See Also**

Functions that perform operations on character strings, return lengths
of arguments, and search for certain arguments:

- **Elemental:**
  [**adjustl**(3)](ADJUSTL),
  [**adjustr**(3)](ADJUSTR),
  [**index**(3)](INDEX),
  [**scan**(3)](SCAN),
  [**verify**(3)](VERIFY)

- **Nonelemental:**
  [**repeat**(3)](REPEAT),
  [**len**(3)](LEN),
  [**trim**(3)](TRIM)

####### fortran-lang intrinsic descriptions (license: MIT) @urbanjost
