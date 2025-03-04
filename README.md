# flogger
  

logg method has three arguments. First one specifies verbosity level.
In princpile that can be done via enum. Second the message and the third one
is the rank so only rank.eq.0 will show the message. For serial codes this
is unnecessary and it should be always zero.

```
  call l%logg("VERBOSITY_LOW", "", 0)
  call l%logg("VERBOSITY_LOW", "Hello this is a cool software suite!", 0)
  call l%logg("VERBOSITY_LOW", "", 0)
  call l%logg("VERBOSITY_LOW", "====================================", 0)
  call l%logg("VERBOSITY_LOW", "", 0)
  call l%logg("VERBOSITY_LOW", "It is for logging and formating outputs,&
                              & here are some examples:", 0)
```

This package makes formating a little bit easier. Appending operator now works for any kind of basic variable.

```
  call l%logg("VERBOSITY_LOW", "", 0)
  call l%logg("VERBOSITY_LOW", "This flag is " // .TRUE., 0)
  call l%logg("VERBOSITY_LOW", "This flag is " // .FALSE., 0)
  call l%logg("VERBOSITY_LOW", "", 0)
  call l%logg("VERBOSITY_LOW", "Hello I am " // animal, 0) ! animal is Girafe
  call l%logg("VERBOSITY_LOW", "I have " // 5 // " friends", 0)
  call l%logg("VERBOSITY_LOW", "", 0)
```

This code will produce following output:

```
 This flag is True
 This flag is False
 
 Hello I am Girafe
 I have 5 friends
```

One can format output by specifying `**'fmt'`. `fmt` should have the same format as one would use in `write (5,'fmt')`.

```
  call l%logg("VERBOSITY_LOW", "The total run time is "// 5.1234567&
                          & // " seconds", 0)
  call l%logg("VERBOSITY_LOW", "Your bank balance is "&
                          & //  5.123456789 ** 'f8.2'&
                          & // " sestertii", 0)
```

One can specify special formats like here for eV and Ang. By adding extra @ letter one can trim the output

```
  call l%logg("VERBOSITY_LOW", "Hydrogen ionization energy is "&
                          & // 0.5 ** '!H2eV!f8.3', 0)
  call l%logg("VERBOSITY_LOW", "My favorite bond length is "&
                          & // 2.91 ** '!B2Ang!f8.3', 0)
  call l%logg("VERBOSITY_LOW", "My second favorite bond length is "&
                          & // 0.7 ** '!B2Ang!@f8.3', 0)
```

Producing following output

```
 Hydrogen ionization energy is   13.606 eV
 My favorite bond length is    1.540 Ang
 My second favorite bond length is 0.370 Ang
```



