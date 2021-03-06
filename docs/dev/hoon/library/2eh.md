section 2eH, parsing (idioms)
=============================

### `++alf`

Alphabetic characters

Parse alphabetic characters, both upper and lowercase.

Source
------

    ++  alf  ;~(pose low hig)                               ::  alphabetic

Examples
--------

        ~zod/try=> (scan "a" alf)
        ~~a
        ~zod/try=> (scan "A" alf)
        ~~~41.
        ~zod/try=> (scan "AaBbCc" (star alf))
        "AaBbCc"

------------------------------------------------------------------------

### `++aln`

Alphanumeric characters

Parse alphanumeric characters - both alphabetic characters and numbers.

Source
------

    ++  aln  ;~(pose low hig nud)                           ::  alphanumeric

Examples
--------

        ~zod/try=> (scan "0" aln)
        ~~0
        ~zod/try=> (scan "alf42" (star aln))
        "alf42"
        ~zod/try=> (scan "0123456789abcdef" (star aln))
        "0123456789abcdef"

------------------------------------------------------------------------

### `++alp`

Alphanumeric and `-`

Parse alphanumeric strings and hep, "-".

Source
------

    ++  alp  ;~(pose low hig nud hep)                       ::  alphanumeric and -

Examples
--------

        ~zod/try=> (scan "7" alp)
        ~~7
        ~zod/try=> (scan "s" alp)
        ~~s
        ~zod/try=> (scan "123abc-" (star alp))
        "123abc-"

------------------------------------------------------------------------

### `++bet`

Axis syntax `-`, `+`

Parse the hep and lus axis syntax.

Source
------

    ++  bet  ;~(pose (cold 2 hep) (cold 3 lus))             ::  axis syntax - +

Examples
--------

        ~zod/try=> (scan "-" bet)
        2
        ~zod/try=> (scan "+" bet)
        3

------------------------------------------------------------------------

### `++bin`

Binary to atom

Parse a tape of binary (0s and 1s) and produce its atomic representation.

Source
------

    ++  bin  (bass 2 (most gon but))                        ::  binary to atom

Examples
--------

        ~zod/try=> (scan "0000" bin)
        0
        ~zod/try=> (scan "0001" bin)
        1
        ~zod/try=> (scan "0010" bin)
        2
        ~zod/try=> (scan "100000001111" bin)
        2.063

------------------------------------------------------------------------

### `++but`

Binary digit

Parse a single binary digit.

Source
------

    ++  but  (cook |=(a=@ (sub a '0')) (shim '0' '1'))      ::  binary digit

Examples
--------

        ~zod/try=> (scan "0" but)
        0
        ~zod/try=> (scan "1" but)
        1
        ~zod/try=> (scan "01" but)
        ! {1 2}
        ! 'syntax-error'
        ! exit
        ~zod/try=> (scan "01" (star but))
        ~[0 1]

------------------------------------------------------------------------

### `++cit`

Octal digit

Parse a single octal digit.

Source
------

    ++  cit  (cook |=(a=@ (sub a '0')) (shim '0' '7'))      ::  octal digit

Examples
--------

        ~zod/try=> (scan "1" cit)
        1
        ~zod/try=> (scan "7" cit)
        7
        ~zod/try=> (scan "8" cit)
        ! {1 1}
        ! 'syntax-error'
        ! exit
        ~zod/try=> (scan "60" (star cit))
        ~[6 0]

------------------------------------------------------------------------

### `++dem`

Decimal to atom

Parse a decimal number to an atom.

Source
------

    ++  dem  (bass 10 (most gon dit))                       ::  decimal to atom

Examples
--------

        ~zod/try=> (scan "7" dem)
        7
        ~zod/try=> (scan "42" dem)
        42
        ~zod/try=> (scan "150000000" dem)
        150.000.000
        ~zod/try=> (scan "12456" dem)
        12.456

------------------------------------------------------------------------

### `++dit`

Decimal digit

Parse a single decimal digit.

Source
------

    ++  dit  (cook |=(a=@ (sub a '0')) (shim '0' '9'))      ::  decimal digit

Examples
--------

        ~zod/try=> (scan "7" dit)
        7
        ~zod/try=> (scan "42" (star dit))
        ~[4 2]
        ~zod/try=> (scan "26000" (star dit))
        ~[2 6 0 0 0]

------------------------------------------------------------------------

### `++gul`

Axis syntax `<` or `>`

Parse the axis gal and gar axis syntax.

Source
------

    ++  gul  ;~(pose (cold 2 gal) (cold 3 gar))             ::  axis syntax < >

Examples
--------

        ~zod/try=> (scan "<" gul)
        2
        ~zod/try=> (scan ">" gul)
        3

------------------------------------------------------------------------

### `++gon`

Long numbers

Parse long numbers - Numbers which wrap around the shell with the line

Source
------

break     ++  gon  ;~(pose ;~(plug bas gay fas) (easy ~))         ::  long numbers \ /

Examples
--------
characters bas and fas.

        ~zod/try=> (scan "\\/" gon)
        [~~~5c. ~ ~~~2f.]
        ~zod/try=> (gon [[1 1] "\\/"])
        [p=[p=1 q=3] q=[~ u=[p=[~~~5c. ~ ~~~2f.] q=[p=[p=1 q=3] q=""]]]]

------------------------------------------------------------------------

### `++hex`

Hex to atom

Parse any hexadecimal number to an atom.

Source
------

    ++  hex  (bass 16 (most gon hit))                       ::  hex to atom

Examples
--------

        ~zod/try=> (scan "a" hex)
        10
        ~zod/try=> (scan "A" hex)
        10
        ~zod/try=> (scan "2A" hex)
        42
        ~zod/try=> (scan "1ee7" hex)
        7.911
        ~zod/try=> (scan "1EE7" hex)
        7.911
        ~zod/try=> (scan "1EE7F7" hex)
        2.025.463
        ~zod/try=> `@ux`(scan "1EE7F7" hex)
        0x1e.e7f7

------------------------------------------------------------------------

### `++hig`

Uppercase

Parse a single uppercase letter.

Source
------

    ++  hig  (shim 'A' 'Z')                                 ::  uppercase

Examples
--------

        ~zod/try=> (scan "G" hig)
        ~~~47.
        ~zod/try=> `cord`(scan "G" hig)
        'G'
        ~zod/try=> (scan "ABCDEFGHIJKLMNOPQRSTUVWXYZ" (star hig))
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        ~zod/try=> (hig [[1 1] "G"])
        [p=[p=1 q=2] q=[~ [p=~~~47. q=[p=[p=1 q=2] q=""]]]]

------------------------------------------------------------------------

### `++hit`

Hex digits

Parse a single hexadecimal digit.

Source
------

    ++  hit  ;~  pose                                       ::  hex digits
               dit
               (cook |=(a=char (sub a 87)) (shim 'a' 'f'))
               (cook |=(a=char (sub a 55)) (shim 'A' 'F'))
             ==

Examples
--------

        ~zod/try=> (scan "a" hit)
        10
        ~zod/try=> (scan "A" hit)
        10
        ~zod/try=> (hit [[1 1] "a"])
        [p=[p=1 q=2] q=[~ [p=10 q=[p=[p=1 q=2] q=""]]]]
        ~zod/try=> (scan "2A" (star hit))
        ~[2 10]

------------------------------------------------------------------------

### `++low`

Lowercase

Parse a single lowercase letter.

Source
------

    ++  low  (shim 'a' 'z')                                 ::  lowercase

Examples
--------

        ~zod/try=> (scan "g" low)
        ~~g
        ~zod/try=> `cord`(scan "g" low)
        'g'
        ~zod/try=> (scan "abcdefghijklmnopqrstuvwxyz" (star low))
        "abcdefghijklmnopqrstuvwxyz"
        ~zod/try=> (low [[1 1] "g"])
        [p=[p=1 q=2] q=[~ [p=~~g q=[p=[p=1 q=2] q=""]]]]

------------------------------------------------------------------------

### `++mes`

Hexbyte

Parse a hexbyte.

Source
------

    ++  mes  %+  cook                                       ::  hexbyte
               |=([a=@ b=@] (add (mul 16 a) b))
             ;~(plug hit hit)

Examples
--------

        ~zod/try=> (scan "2A" mes)
        42
        ~zod/try=> (mes [[1 1] "2A"])
        [p=[p=1 q=3] q=[~ u=[p=42 q=[p=[p=1 q=3] q=""]]]]
        ~zod/try=> (scan "42" mes)
        66

------------------------------------------------------------------------

### `++nix`

Letters and `-`

Parse Letters and `-`.

Source
------

    ++  nix  (boss 256 (star ;~(pose aln cab)))             ::

Examples
--------

    ~zod/try=> (scan "as_me" nix)
    q=435.626.668.897
    ~zod/try=> `@t`(scan "as_me" nix)
    'as_me'

------------------------------------------------------------------------

### `++nud`

Numeric

Parse a numeric character - A number.

Source
------

    ++  nud  (shim '0' '9')                                 ::  numeric

Examples
--------

    ~zod/try=> (scan "0" nud)
    ~~0
    ~zod/try=> (scan "7" nud)
    ~~7
    ~zod/try=> (nud [[1 1] "1"])
    [p=[p=1 q=2] q=[~ [p=~~1 q=[p=[p=1 q=2] q=""]]]]
    ~zod/try=> (scan "0123456789" (star nud))
    "0123456789"

------------------------------------------------------------------------

### `++prn`

Printable character

Parse any printable character.

Source
------

    ++  prn  ;~(less (just `@`127) (shim 32 256))

Examples
--------

    ~zod/try=> (scan "h" prn)
    ~~h
    ~zod/try=> (scan "!" prn)
    ~~~21.
    ~zod/try=> (scan "\01" prn)
    ! {1 1}
    ! exit

------------------------------------------------------------------------

### `++qat`

Chars in blockcord

Parse character in cord block.

Source
------

    ++  qat  ;~  pose                                       ::  chars in blockcord
                 prn
                 ;~(less ;~(plug (just `@`10) soqs) (just `@`10))
             ==

Examples
--------

    ~zod/try=> (scan "h" qat)
    ~~h
    ~zod/try=> (scan "!" qat)
    ~~~21.
    ~zod/try=> (scan "\0a" qat)
    ~~~a.
    ~zod/try=> (scan "\00" qat)
    ! {1 1}
    ! exit

------------------------------------------------------------------------

### `++qit`

Chars in cord

Parse an individual character to its cord atom representation.

Source
------

    ++  qit  ;~  pose                                       ::  chars in a cord
                 ;~(less bas soq prn)
                 ;~(pfix bas ;~(pose bas soq mes))          ::  escape chars
             ==

Examples
--------

    ~zod/try=> (scan "%" qit)
    37
    ~zod/try=> `@t`(scan "%" qit)
    '%'
    ~zod/try=> (scan "0" qit)
    48
    ~zod/try=> (scan "E" qit)
    69
    ~zod/try=> (scan "a" qit)
    97
    ~zod/try=> (scan "\\0a" qit)
    10
    ~zod/try=> `@ux`(scan "\\0a" qit)
    0xa
    ~zod/try=> (scan "cord" (star qit))
    ~[99 111 114 100]

------------------------------------------------------------------------

### `++qut`

Cord

Parse single-soq cord with `\{gap}/` anywhere in the middle, or triple-single
quote (aka triple-soq) cord, between which must be in an indented block.

Source
------

     ++  qut  ;~  pose                                       ::  cord
                 ;~  less  soqs
                   (ifix [soq soq] (boss 256 (more gon qit)))
                 ==
                 %-  inde  %+  ifix
                   :-  ;~  plug  soqs
                         ;~(pose ;~(plug (plus ace) vul) (just '\0a'))
                       ==
                   ;~(plug (just '\0a') soqs)
                 (boss 256 (star qat))
             ==
    ::

Examples
--------

    ~zod/try=> (scan "'cord'" qut)
    q=1.685.221.219
    ~zod/try=> 'cord'
    'cord'
    ~zod/try=> `@ud`'cord'
    1.685.221.219
    /~zod/try=> '''
                Heredoc isn't prohibited from containing quotes
                '''
    'Heredoc isn't prohibited from containing quotes'

------------------------------------------------------------------------

### `++soqs`

Delimiting `'''`

Parse a triple-single quote, used for multiline strings.

Source
------

    ++  soqs  ;~(plug soq soq soq)                          ::  delimiting '''

Examples
--------

    ~zod/try=> (scan "'''" soqs)
    [~~~27. ~~~27. ~~~27.]
    ~zod/try=> (rash '"""' soqs)
    ! {1 1}
    ! exit

------------------------------------------------------------------------

### `++sym`

Term

A term: a letter(lowercase), followed by letters, numbers, or `-`.

Source
------

    ++  sym
      %+  cook
        |=(a=tape (rap 3 ^-((list ,@) a)))
      ;~(plug low (star ;~(pose nud low hep)))
    ::

Examples
--------

    ~zod/try=> (scan "sam-2" sym)
    215.510.507.891
    ~zod/try=> `@t`(scan "sam-2" sym)
    'sam-2'
    ~zod/try=> (scan "sym" sym)
    7.174.515

------------------------------------------------------------------------

### `++ven`

`+>-` axis syntax

Axis syntax parser

Source
------

    ++  ven  ;~  (comp |=([a=@ b=@] (peg a b)))             ::  +>- axis syntax
               bet
               =+  hom=`?`|
               |=  tub=nail
               ^-  (like axis)
               =+  vex=?:(hom (bet tub) (gul tub))
               ?~  q.vex
                 [p.tub [~ 1 tub]]
               =+  wag=$(p.tub p.vex, hom !hom, tub q.u.q.vex)
               ?>  ?=(^ q.wag)
               [p.wag [~ (peg p.u.q.vex p.u.q.wag) q.u.q.wag]]
             ==

Examples
--------

    ~zod/arvo=/hoon/hoon> (scan "->+" ven)
    11
    ~zod/arvo=/hoon/hoon> `@ub`(scan "->+" ven)
    0b1011
    ~zod/arvo=/hoon/hoon> (peg (scan "->" ven) (scan "+" ven))
    11
    ~zod/arvo=/hoon/hoon> ->+:[[1 2 [3 4]] 5]
    [3 4]

------------------------------------------------------------------------

### `++vit`

Base64 digit

Parse a Terran base64 digit.

Source
------

    ++  vit                                                 ::  base64 digit
      ;~  pose
        (cook |=(a=@ (sub a 65)) (shim 'A' 'Z'))
        (cook |=(a=@ (sub a 71)) (shim 'a' 'z'))
        (cook |=(a=@ (add a 4)) (shim '0' '9'))
        (cold 62 (just '-'))
        (cold 63 (just '+'))
      ==

Examples
--------

    ~zod/arvo=/hoon/hoon> (scan "C" vit)
    2
    ~zod/arvo=/hoon/hoon> (scan "c" vit)
    28
    ~zod/arvo=/hoon/hoon> (scan "2" vit)
    54
    ~zod/arvo=/hoon/hoon> (scan "-" vit)
    62
