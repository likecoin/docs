---
description: >-
  This page is showing how to use query string to change ISCN badge Looks in
  color and size.
---

# ISCN Badge

**You can add one of the following query string after the "`?`" of the Base URL below. Base URL: **\
`https://static.like.co/badge/iscn/<iscn_tx_hash>.svg?`

Success Example: [https://static.like.co/badge/iscn/3513633D18BA70EB9DA38CD1AC779D6D4372326B3D65B7A14EC75DB8C86C0E6D.svg?dark=1\&responsive=0\&width=82](https://static.like.co/badge/iscn/3513633D18BA70EB9DA38CD1AC779D6D4372326B3D65B7A14EC75DB8C86C0E6D.svg?dark=1\&responsive=0\&width=82)

| Query String | Accepted Value                                                                                                |
| ------------ | ------------------------------------------------------------------------------------------------------------- |
| dark         | <p>boolean. e.g. 0 (light) or 1 (dark)</p><p>When not provided, default to 0.</p>                             |
| responsive   | <p>boolean. e.g. 0 (size is not responsive) or 1 (responsive size)</p><p>When not provided, default to 0.</p> |
| width        | <p>number. e.g. 164 (164px)</p><p>When not provided, default to 164.</p>                                      |
| height       | <p>number. e.g. 64 (64px)</p><p>When not provided, default to 64.</p>                                         |

**Some errors may happened when providing multiple conflicting query string values between responsive, width, and height.**

| Error Scenario          | Error Code & Explanation                                                            |
| ----------------------- | ----------------------------------------------------------------------------------- |
| responsive=1\&width=30  | <p>400 <br>Does not know whether the user want a fixed size or responsive size.</p> |
| responsive=1\&height=20 | <p>400 <br>Does not know whether the user want a fixed size or responsive size.</p> |
| responsive=0\&height=sf | <p>400</p><p>Height in wrong format (NaN).</p>                                      |
| responsive=0\&wodth=sf  | <p>400</p><p>Height in wrong format (NaN).</p>                                      |

**Note:** 

When providing both height & width, but the ratio does not fit to 164 (width) \* 64 (height), we will anchor the size of the badge on **width**.\
For example, user provides `width=200&height=400`, the overall size for the badge would be: `width=200&height=200*64/164`.

