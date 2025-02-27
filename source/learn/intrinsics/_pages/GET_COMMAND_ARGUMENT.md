## get_command_argument

### **Name**

**get_command_argument**(3) - \[SYSTEM:COMMAND LINE\] Get command line arguments

### **Syntax**

```fortran
     call get_command_argument(number, value, length, status)

     subroutine get_command_argument(number,value,length.status)
     integer,intent(in)                    :: number
     character(len=*),intent(out),optional :: value
     integer,intent(out),optional          :: length
     integer,intent(out),optional          :: status
```

### **Description**

Retrieve the **number**-th argument that was passed on the command line
when the containing program was invoked.

There is not anything specifically stated about what an argument is but
in practice the arguments are split on whitespace unless the arguments
are quoted and IFS values (Internal Field Separators) used by common
shells are ignored.

### **Options**

- **number**
  : Shall be a scalar of type **integer**, **number \>= 0**. If **number =
  0**, **value** is set to the name of the program (on systems that support
  this feature).

### **Returns**

- **value**
  :Shall be a scalar of type _character_ and of default kind. After
  get_command_argument returns, the **value** argument holds the
  **number**-th command line argument. If **value** can not hold the argument,
  it is truncated to fit the length of **value**. If there are less than
  **number** arguments specified at the command line, **value** will be filled
  with blanks.

- **length**
  :(Optional) Shall be a scalar of type _integer_. The **length**
  argument contains the length of the **number**-th command line argument.

- **status**
  :(Optional) Shall be a scalar of type _integer_. If the argument
  retrieval fails, **status** is a positive number; if **value** contains a
  truncated command line argument, **status** is **-1**; and otherwise the
  **status** is zero.

### **Examples**

Sample program:

```fortran
program demo_get_command_argument
implicit none
character(len=255)           :: progname
integer                      :: stat
integer                      :: count,i, longest, argument_length
integer,allocatable          :: istat(:), ilen(:)
character(len=:),allocatable :: args(:)
  !
  ! get number of arguments
  count = command_argument_count()
  write(*,*)'The number of arguments is ',count
  !
  ! simple usage
  !
  call get_command_argument (0, progname, status=stat)
  if (stat == 0) then
     print *, "The program's name is " // trim (progname)
  endif
  !
  ! showing how to make an array to hold any argument list
  !
  ! find longest argument
  !
  longest=0
  do i=0,count
     call get_command_argument(number=i,length=argument_length)
     longest=max(longest,argument_length)
  enddo
  !
  ! allocate string array big enough to hold command line
  ! argument strings and related information
  !
  allocate(character(len=longest) :: args(0:count))
  allocate(istat(0:count))
  allocate(ilen(0:count))
  !
  ! read the arguments into the array
  !
  do i=0,count
    call get_command_argument(i, args(i),status=istat(i),length=ilen(i))
  enddo
  !
  ! show the results
  !
  write (*,'(i3.3,1x,i0.5,1x,i0.5,1x,"[",a,"]")') &
  & (i,istat(i),ilen(i),args(i)(:ilen(i)),i=0,count)
end program demo_get_command_argument
```

Results:

```text
/demo_get_command_argument a    test  'of getting   arguments  ' "  leading"

 The number of arguments is            5
 The program's name is xxx
000 00000 00003 [./test_get_command_argument]
001 00000 00001 [a]
003 00000 00004 [test]
004 00000 00024 [of getting   arguments  ]
005 00000 00018 [  leading]
```

### **Standard**

Fortran 2003 and later

### **See Also**

[**get_command**(3)](GET_COMMAND),
[**command_argument_count**(3)](COMMAND_ARGUMENT_COUNT)

####### fortran-lang intrinsic descriptions (license: MIT) @urbanjost
