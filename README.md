# Ukkonen's Suffix Tree Algorithm in Python Complete Version
Suffix Tree Algorithm implemented in Python, might be the most complete version online, even more complete than that demonstrated on stackoverflow.

I underestimated the complication of the algorithm and just wanted to have some fun. A primitive implementation was done in a couple of hours, and the demonstation example on stackoverflow works just fine. Then when I wanted try some more complicated examples, I kept hitting the wall time and time again. It annoyed me, and thus costed me several days to try different situations when constructing a suffix tree.

Finally, the version comes out, I think **all the situations** explained in the questions and answers have been experienced and covered in the algorithm above before I read the full post.

I also write a blog on explaining the implementation details on my blogger [MuTuX](http://www.mutux.com/2017/07/suffix-tree-implementation-move-all.html "mutux's blog on text mining") with flowcharts and explanation on it.


## Examples

```
    docs = ['abcabxabcd', 'dedododeeodoeodooedeeododooodoede$', 'ooooooooo', 'mississippi']
    for text in docs:
        tree, pst = build(text, regularize=True)
        Node.draw(tree, pst, ed='#')
```

The running results:
```
abcabxabcd 
● (0)
|
|   ab
+----------------● (4->6)
|                |
|                |   xabcd
|                +---------------● (5)
|                |
|                |   c
|                +---------------● (9->11)
|                                |
|                                |   abxabcd
|                                +---------------● (1)
|                                |
|                                |   d
|                                +---------------● (10)
|
|   c
+----------------● (13)
|                |
|                |   abxabcd
|                +---------------● (3)
|                |
|                |   d
|                +---------------● (14)
|
|   b
+----------------● (6)
|                |
|                |   xabcd
|                +---------------● (7)
|                |
|                |   c
|                +---------------● (11->13)
|                                |
|                                |   abxabcd
|                                +---------------● (2)
|                                |
|                                |   d
|                                +---------------● (12)
|
|   xabcd
+----------------● (8)
|
|   d
+----------------● (15)

dedododeeodoeodooedeeododooodoede$ 
● (0)
|
|   e
+----------------------------------------● (28)
|                                        |
|                                        |   $
|                                        +---------------------------------------● (71)
|                                        |
|                                        |   eodo
|                                        +---------------------------------------● (48->37)
|                                                                                |
|                                                                                |   eodooedeeododooodoede$
|                                                                                +---------------------------------------● (29)
|                                                                                |
|                                                                                |   dooodoede$
|                                                                                +---------------------------------------● (49)
|                                        |
|                                        |   d
|                                        +---------------------------------------● (44->19)
|                                                                                |
|                                                                                |   ododeeodoeodooedeeododooodoede$
|                                                                                +---------------------------------------● (18)
|                                                                                |
|                                                                                |   e
|                                                                                +---------------------------------------● (68->26)
|                                                                                                                        |
|                                                                                                                        |   eododooodoede$
|                                                                                                                        +---------------------------------------● (45)
|                                                                                                                        |
|                                                                                                                        |   $
|                                                                                                                        +---------------------------------------● (69)
|                                        |
|                                        |   odo
|                                        +---------------------------------------● (37->31)
|                                                                                |
|                                                                                |   eodooedeeododooodoede$
|                                                                                +---------------------------------------● (30)
|                                                                                |
|                                                                                |   dooodoede$
|                                                                                +---------------------------------------● (50)
|                                                                                |
|                                                                                |   oedeeododooodoede$
|                                                                                +---------------------------------------● (38)
|
|   d
+----------------------------------------● (19)
|                                        |
|                                        |   e
|                                        +---------------------------------------● (26->28)
|                                                                                |
|                                                                                |   dododeeodoeodooedeeododooodoede$
|                                                                                +---------------------------------------● (17)
|                                                                                |
|                                                                                |   $
|                                                                                +---------------------------------------● (70)
|                                                                                |
|                                                                                |   eodo
|                                                                                +---------------------------------------● (46->48)
|                                                                                                                        |
|                                                                                                                        |   eodooedeeododooodoede$
|                                                                                                                        +---------------------------------------● (27)
|                                                                                                                        |
|                                                                                                                        |   dooodoede$
|                                                                                                                        +---------------------------------------● (47)
|                                        |
|                                        |   o
|                                        +---------------------------------------● (33->35)
|                                                                                |
|                                                                                |   e
|                                                                                +---------------------------------------● (64->42)
|                                                                                                                        |
|                                                                                                                        |   de$
|                                                                                                                        +---------------------------------------● (65)
|                                                                                                                        |
|                                                                                                                        |   odooedeeododooodoede$
|                                                                                                                        +---------------------------------------● (34)
|                                                                                |
|                                                                                |   d
|                                                                                +---------------------------------------● (22->24)
|                                                                                                                        |
|                                                                                                                        |   eeodoeodooedeeododooodoede$
|                                                                                                                        +---------------------------------------● (23)
|                                                                                                                        |
|                                                                                                                        |   o
|                                                                                                                        +---------------------------------------● (53->31)
|                                                                                                                                                                |
|                                                                                                                                                                |   deeodoeodooedeeododooodoede$
|                                                                                                                                                                +---------------------------------------● (20)
|                                                                                                                                                                |
|                                                                                                                                                                |   oodoede$
|                                                                                                                                                                +---------------------------------------● (54)
|                                                                                |
|                                                                                |   o
|                                                                                +---------------------------------------● (57->59)
|                                                                                                                        |
|                                                                                                                        |   edeeododooodoede$
|                                                                                                                        +---------------------------------------● (40)
|                                                                                                                        |
|                                                                                                                        |   odoede$
|                                                                                                                        +---------------------------------------● (58)
|
|   o
+----------------------------------------● (35)
|                                        |
|                                        |   e
|                                        +---------------------------------------● (42->28)
|                                                                                |
|                                                                                |   odooedeeododooodoede$
|                                                                                +---------------------------------------● (36)
|                                                                                |
|                                                                                |   de
|                                                                                +---------------------------------------● (66->68)
|                                                                                                                        |
|                                                                                                                        |   eododooodoede$
|                                                                                                                        +---------------------------------------● (43)
|                                                                                                                        |
|                                                                                                                        |   $
|                                                                                                                        +---------------------------------------● (67)
|                                        |
|                                        |   d
|                                        +---------------------------------------● (24->19)
|                                                                                |
|                                                                                |   eeodoeodooedeeododooodoede$
|                                                                                +---------------------------------------● (25)
|                                                                                |
|                                                                                |   o
|                                                                                +---------------------------------------● (31->33)
|                                                                                                                        |
|                                                                                                                        |   e
|                                                                                                                        +---------------------------------------● (62->64)
|                                                                                                                                                                |
|                                                                                                                                                                |   de$
|                                                                                                                                                                +---------------------------------------● (63)
|                                                                                                                                                                |
|                                                                                                                                                                |   odooedeeododooodoede$
|                                                                                                                                                                +---------------------------------------● (32)
|                                                                                                                        |
|                                                                                                                        |   d
|                                                                                                                        +---------------------------------------● (51->22)
|                                                                                                                                                                |
|                                                                                                                                                                |   eeodoeodooedeeododooodoede$
|                                                                                                                                                                +---------------------------------------● (21)
|                                                                                                                                                                |
|                                                                                                                                                                |   ooodoede$
|                                                                                                                                                                +---------------------------------------● (52)
|                                                                                                                        |
|                                                                                                                        |   o
|                                                                                                                        +---------------------------------------● (55->57)
|                                                                                                                                                                |
|                                                                                                                                                                |   edeeododooodoede$
|                                                                                                                                                                +---------------------------------------● (39)
|                                                                                                                                                                |
|                                                                                                                                                                |   odoede$
|                                                                                                                                                                +---------------------------------------● (56)
|                                        |
|                                        |   o
|                                        +---------------------------------------● (59->35)
|                                                                                |
|                                                                                |   edeeododooodoede$
|                                                                                +---------------------------------------● (41)
|                                                                                |
|                                                                                |   doede$
|                                                                                +---------------------------------------● (61)
|                                                                                |
|                                                                                |   odoede$
|                                                                                +---------------------------------------● (60)
|
|   $
+----------------------------------------● (72)

ooooooooo$ 
● (0)
|
|   o
+----------------● (89)
|                |
|                |   $
|                +---------------● (90)
|                |
|                |   o
|                +---------------● (87->89)
|                                |
|                                |   $
|                                +---------------● (88)
|                                |
|                                |   o
|                                +---------------● (85->87)
|                                                |
|                                                |   $
|                                                +---------------● (86)
|                                                |
|                                                |   o
|                                                +---------------● (83->85)
|                                                                |
|                                                                |   $
|                                                                +---------------● (84)
|                                                                |
|                                                                |   o
|                                                                +---------------● (81->83)
|                                                                                |
|                                                                                |   $
|                                                                                +---------------● (82)
|                                                                                |
|                                                                                |   o
|                                                                                +---------------● (79->81)
|                                                                                                |
|                                                                                                |   $
|                                                                                                +---------------● (80)
|                                                                                                |
|                                                                                                |   o
|                                                                                                +---------------● (77->79)
|                                                                                                                |
|                                                                                                                |   $
|                                                                                                                +---------------● (78)
|                                                                                                                |
|                                                                                                                |   o
|                                                                                                                +---------------● (75->77)
|                                                                                                                                |
|                                                                                                                                |   $
|                                                                                                                                +---------------● (76)
|                                                                                                                                |
|                                                                                                                                |   o$
|                                                                                                                                +---------------● (74)
|
|   $
+----------------● (91)

mississippi$ 
● (0)
|
|   i
+------------------● (104)
|                  |
|                  |   ppi$
|                  +-----------------● (105)
|                  |
|                  |   $
|                  +-----------------● (109)
|                  |
|                  |   ssi
|                  +-----------------● (98->100)
|                                    |
|                                    |   ppi$
|                                    +-----------------● (99)
|                                    |
|                                    |   ssippi$
|                                    +-----------------● (94)
|
|   p
+------------------● (107)
|                  |
|                  |   i$
|                  +-----------------● (108)
|                  |
|                  |   pi$
|                  +-----------------● (106)
|
|   s
+------------------● (96)
|                  |
|                  |   i
|                  +-----------------● (102->104)
|                                    |
|                                    |   ppi$
|                                    +-----------------● (103)
|                                    |
|                                    |   ssippi$
|                                    +-----------------● (97)
|                  |
|                  |   si
|                  +-----------------● (100->102)
|                                    |
|                                    |   ppi$
|                                    +-----------------● (101)
|                                    |
|                                    |   ssippi$
|                                    +-----------------● (95)
|
|   mississippi$
+------------------● (93)
|
|   $
+------------------● (110)

```

## Finally
Have fun!
