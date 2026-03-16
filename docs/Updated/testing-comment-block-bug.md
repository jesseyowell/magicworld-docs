---
title: Testing comment block bug
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Trying to reproduce bug with comment blocks:

1. Hello

2. Test

3. Three

4. OK
   1. YES

1\.

2\.

3\.

4. OK
   1. OK
      1. aY

5. TEST OK

6. AHH

7. TEST

{/**/}

1. OK
2. YES
   1. OK
      1. YES
         1. FFFFF
3. OOF
