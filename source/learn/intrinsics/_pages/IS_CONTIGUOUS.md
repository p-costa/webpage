## is_contiguous

### **Name**

**is_contiguous**(3) - \[ARRAY INQUIRY\] test if object is contiguous

### **Syntax**

```fortran
result = is_contiguous(a)
```

### **Description**

True if and only if an object is contiguous.

An object is contiguous if it is

- **(1)**
  an object with the CONTIGUOUS attribute,

- **(2)**
  a nonpointer whole array that is not assumed-shape,

- **(3)**
  an assumed-shape array that is argument associated with an array
  that is contiguous,

- **(4)**
  an array allocated by an ALLOCATE statement,

- **(5)**
  a pointer associated with a contiguous target, or

- **(6)**
  a nonzero-sized array section provided that

  - **(a)**
    its base object is contiguous,

  - **(b)**
    it does not have a vector subscript,

  - **(c)**
    the elements of the section, in array element order, are a
    subset of the base object elements that are consecutive in
    array element order,

  - **(d)**
    if the array is of type character and a substring-range
    appears, the substring-range specifies all of the characters
    of the parent-string,

  - **(e)**
    only its final part-ref has nonzero rank, and

  - **(f)**
    it is not the real or imaginary part of an array of type
    complex.

An object is not contiguous if it is an array subobject, and

- the object has two or more elements,

- the elements of the object in array element order are not
  consecutive in the elements of the base object,

- the object is not of type character with length zero, and

- the object is not of a derived type that has no ultimate
  components other than zero-sized arrays and

- characters with length zero.

It is processor-dependent whether any other object is contiguous.

### **Arguments**

- **a**
  : may be of any type. It shall be an array. If it is a pointer it
  shall be associated.

### **Returns**

- **Result**
  : of type Default logical scalar. The result has the value true if **a**
  is contiguous, and false otherwise.

### **Examples**

Sample program:

```fortran
program demo_is_contiguous
implicit none
intrinsic is_contiguous
real, DIMENSION (1000, 1000), TARGET :: A
real, DIMENSION (:, :), POINTER       :: IN, OUT
   IN => A              ! Associate IN with target A
   OUT => A(1:1000:2,:) ! Associate OUT with subset of target A
   !
   write(*,*)'IN is ',IS_CONTIGUOUS(IN)
   write(*,*)'OUT is ',IS_CONTIGUOUS(OUT)
   !
end program demo_is_contiguous
```

Results:

```text
    IN is  T
    OUT is  F
```

### **Standard**

Fortran 2008 and later

####### fortran-lang intrinsic descriptions
