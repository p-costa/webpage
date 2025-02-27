## co_lbound

### **Name**

**co_lbound**(3) - \[COLLECTIVE\] Lower codimension bounds of an array

### **Syntax**

```fortran
result = co_lbound(coarray, dim, kind)
```

### **Description**

Returns the lower bounds of a coarray, or a single lower cobound along
the **dim** codimension.

### **Arguments**

- **array**
  : Shall be an coarray, of any type.

- **dim**
  : (Optional) Shall be a scalar _integer_.

- **kind**
  : (Optional) An _integer_ initialization expression indicating the kind
  parameter of the result.

### **Returns**

The return value is of type _integer_ and of kind **kind**. If **kind** is absent,
the return value is of default integer kind. If **dim** is absent, the
result is an array of the lower cobounds of **coarray**. If **dim** is present,
the result is a scalar corresponding to the lower cobound of the array
along that codimension.

### **Standard**

Fortran 2008 and later

### **See Also**

[**co_ubound**(3)](CO_UBOUND),
[**lbound**(3)](LBOUND)

####### fortran-lang intrinsic descriptions
