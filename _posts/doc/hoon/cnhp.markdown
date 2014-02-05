---
layout: post
category: doc
title: `%-`, `cenhep`, `%cnhp`
---

###Synopsis###

`%-`, `cenhep`, `[%cnhp p=twig q=tusk]` is a synthetic hoon that
calls the gate `p` with the sample `[%cltr q]`

###Definition###

    ++  twig  
      $%  [%cnhp p=twig q=tusk]
      ==

###Regular form (tall)###
  
    %-  p
    [i.q i.t.q]

###Regular form (wide)###

    %-(p i.q i.t.q)

###Irregular form###

    (p i.q i.t.q)

###Expansion###
    
    ++  open
      ^-  twig
      ?-    gen
          [%cnhp *]
        ?~(q.gen [%tsgr p.gen [%cnzy %$]] [%cncl p.gen [%cltr q.gen]])
      ==

###Notes###

It is deplorable but not unusual to say "function" when you mean
"gate", and "argument" when you mean "sample leg."
