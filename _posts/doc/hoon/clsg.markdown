---
layout: post
category: doc
title: `:~`, `colsig`, `%clsg`
---

###Synopsis###

`:~`, `colsig`, `[%clsg p=tusk]` is a synthetic hoon that
produces a null-terminated tuple.

###Definition###

    ++  twig  
      $%  [%clsg p=tusk]
      ==
    ++  tusk  (list twig)

###Regular form (tall)###

    :~  i.p
        i.t.p
        i.t.t.p
    ==

###Regular form (wide)###

    :~(i.p i.t.p i.t.t.p)

###Irregular form###

    ~[i.p i.t.p i.t.t.p]

###Expansion###
    
    ++  open
      ^-  twig
      ?-    gen
          [%clsg *]
        |-  ^-  twig
        ?~  p.gen
          [%dtzz %n ~]
        =+  mow=jone(gen i.p.gen)
        ?:  =(mow [i.p.gen ~])
          [i.p.gen $(p.gen t.p.gen)]
        $(p.gen (weld mow t.p.gen))
      ==
    ::
    ++  jone
      ^-  (list twig)
      ?:  ?=([%clzz *] gen)
        p.gen
      ?:  ?=([%zpcb * [%clzz *]] gen)
        p.q.gen
      [gen ~]

###Notes###

`%clsg` also helps us perform some black magic with string
interpolation by automatically promoting `%clzz` twigs.
Otherwise, `%clsg` would simply expand as

    ++  open
      ^-  twig
      ?-    gen
          [%clsg *]
        $(gen [%cltr (weld p.gen ~[[%bczp %null]])])
      ==
