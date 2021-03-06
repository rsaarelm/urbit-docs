`~%`
====

Register jet

Registers a jet in core `s` so that it can be called when that code is run.

Produces
--------

Twig: `[%sgcn p=term q=twig r=tyre s=twig]`

Accepts
-------

`p` is a [`++term`]() `q` is a [`++twig`]() `r` is a [`++tyre`]() `s` is a
twig.

Tall form
---------

    ~%    p
            q
          ==
            p.i.r    q.i.r
            p.i.t.r  q.i.t.r
          ==
        s

    ~%    p
        q
      ~
    s


Examples
--------

    ++  aesc                                                ::  AES-256
      ~%  %aesc  +  ~
      |%
      ++  en                                                ::  ECB enc
        ~/  %en
        |=  [a=@I b=@H]  ^-  @uxH
        =+  ahem
        (be & (ex a) b)
      ++  de                                                ::  ECB dec
        ~/  %de
        |=  [a=@I b=@H]  ^-  @uxH
        =+  ahem
        (be | (ix (ex a)) b)
      --

Here we label the entire `++aesc` core for optimization. You can see the
jet in `jets/e/aesc.c`.
