---
title: C in Python with Cython
permalink: /C_in_Python_with_Cython/
---

Examples
--------

    %cython
    cdef float test_function(float x):
        return sqrt(x)

    def test(n):
        return test_function(n)

    %sage
    list_plot([(x,test(x)) for x in range(1,1000)])

References
----------

[Numerical Methods with Sage](https://docs.google.com/file/d/0ByEk9zzYZVLgSHVvclVPSTZjeGc/edit)

[Cython: The Best of Both Worlds](https://docs.google.com/file/d/0ByEk9zzYZVLgMnR3Nm5TVUpIc0k/edit)

[|BC| Cython](https://docs.google.com/file/d/18HapfompN87t6HGCV9Dzoyj5tYoE-alDUXt2mhV7qI5GdMKxSpHaxnk2QacimOPgxhy6-42q2EbfOpGu/edit)

[Sage: A Basic Overview](https://docs.google.com/file/d/0ByEk9zzYZVLgUzlIVkd3bFNjQzA/edit)

[Cython: Language Basics](http://docs.cython.org/src/userguide/language_basics.html)

[Overview of the Cython Language](http://cython.org/release/Cython-0.13/Doc/overview.html)

[Sage Math: Coding in Cython](http://www.sagemath.org/doc/developer/coding_in_cython.html)

[Sage Math: Cython Interface](http://www.sagemath.org/doc/thematic_tutorials/cython_interface.html)

[Wikipedia: Cython](http://en.wikipedia.org/wiki/Cython)