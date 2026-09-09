# XLISP-PLUS modified for 64bit pointers

This XLISP-PLUS is forked from blakemcbride/XLISP-PLUS.

The home for this GitHub release is [https://github.com/elberskirch01/XLISP-PLUS](https://github.com/elberskirch01/XLISP-PLUS)

The home for the original GitHub release is [https://github.com/blakemcbride/XLISP-PLUS](https://github.com/blakemcbride/XLISP-PLUS)

## Modifications

The following issues are modified:
xf-fixnum of Fixnum node is extended to "long long" (64bit),
so that it can host 64bit pointer values.
Some local variables are initialized, so that compile warnings
of type
"Variable may be used uninitialized." vanished.
Some multiple evaluations of JMAC macros as actual parameters of
a function are moved in front of
the function call, to avoid warnings of the form
"Undefined sequence oof operations.".
The new getxlptrt() and cvxlptrt() are introduced to enable 
64bit conversion between XLPTYPE (void *) and Fixnum node 
(internal value type FIXTYPE64).

In the new Makefiles the following preprocessor defines are used:
XLPTR64: prepares code for handling of 64bit pointers.
XLIFIX64: prepares code to define xf_fixnum as FIXTYPE64 (long long) in Fixnum node.
XLWIN64: prepares code in win32stu.c to use new 64bit versions of Windows API.

New in code:
GetFixnum(): retrieves FIXTYPE (32bit) from 64bit xf_fixnum after range check.
XLPTYPE: provides intermediate type to set a 64bit pointer to or to get a 64bit pointer from Fixnum node.
getxlptrt(): gets pointer from Fixnum node.
cvxlptrt(): converts a pointer to a Fixnum node.

Remaining issues

The Windows xlisp.exe created by makevswin32 with VS2022 X64_X86 Cross Tools doesn't start-up.
Same holds for makevswin64 with VS2022 X64 Native Tools.

Executable xlisp created with makelx64 seems to work fine.
Also saving and restoring WKS seems to work at a first glance.
Restoring 32bit WKS by 64bit executable is not considered ut to now.

See also the original README.

Ralf Elberskirch
