---
layout: post
title: "Unicode - UTF-8"
author: "Sylvain White"
categories: misc
tags: [misc]
# image: city-2.jpg
---

<br/>

## Unicode - UTF-8

<br/>
The following blog is based on:
* Unifoundry.com: 'Unicode Tutorial' [[web](http://www.unifoundry.com/unicode-tutorial.html){:target="_blank"}]
* w3schools.com: 'HTML Unicode (UTF-8) Reference' [[web](https://www.w3schools.com/charsets/ref_html_utf8.asp){:target="_blank"}]
* W3C: 'Declaring character encodings in HTML' [[web](https://www.w3.org/International/questions/qa-html-encoding-declarations){:target="_blank"}]

<br/>
From Joel Splosky's blog [[web](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/){:target="_blank"}]:
> All that stuff about “plain text = ascii = characters are 8 bits” is not only wrong, it’s hopelessly wrong

<br/>
#### To read any file, you must know how the bytes are encoded
* Historically, we have these encondings:
    * **ASCII** encodes 128 character codes in 7 bits:
        * 96 printable characters (including space and delete) 
        * 32 control characters (e.g. line feed)
    * **ISO 8859-1** encodes 256 character codes in 8 bits:
        * All ASCII character codes into the lower 7 bits of a byte
        * 128 additional character codes with the higher bit of a byte

* Then comes **Unicode** in 1991
    * Unicode **goal** is to provide a universal way to encode the following:
        * All letters from all languages (e.g. german letter &#7838;) including ancient languages
        * All symbols (e.g math symbol &#8721;)
        * All dingbats (e.g. checkmark &#10004;)
        * All emojis (e.g. fox &#128054;)
    * **Firstly**, Unicode assigns an hexadecimal number to all letters, symbols, etc
        * This hexidecimal number is called a 'code point' 
        * Valid code points are 0x0000 to 0x10FFFF
        * To mean a hexidecimal number is a code point, always use the prefix 'U+'
            * For instance, the code point for letter 'a' is U+0062
        * All code points are divided into sets called 'plane'
            * There 17 planes:

            |**Plane** | **Range** | **Name** |
            |0	| U+0000 - U+FFFF | Basic Multilingual Plane |
            |1  | U+10000 - U+1FFFF | Supplementary Multilingual Plane |
            |2	| U+20000 - U+2FFFF | Supplementary Ideographic Plane |
            |3	| U+30000 - U+3FFFF | Tertiary Ideographic Plane |
            |4-13| … | unassigned |
            |14	| U+E0000 - U+EFFFF | Supplement­ary Special-purpose Plane | 
            |15	| U+F0000 - U+FFFFF | Supplement­ary Private Use Area planes |
            |16	| U+100000 - U+10FFFF | Supplement­ary Private Use Area planes |
        * Jargon not essantial to understand Unicode in my opinion. See [[web](https://flaviocopes.com/unicode/#code-units){:target="_blank"}]

            * astral (!) planes: planes 3 to 13
            * code units: the actual bit representation of a code point by encoding
            * grapheme: symbol that reprensents a unit a writing
            * glyph: graphic representation on the screen
            * Example: Various glyphs <span style="font-family:'Times New Roman'; font-size:2em;">T</span>, <span style="font-family:Courier; font-size:2em;">T</span>, <span style="font-family:'Times New Roman'; font-size:2em;">t</span> for the grapheme 't'

    * **Secondly**, Unicode has different ways to encode code points
        * The Unicode encodings are: UTF-8, UTF-16 and UTF-32:

            | **Name** | **Number of bytes** | **Use** |
            | UTF-8	| 1 to 4 | Web pages |
            | UTF-16 | 2 or 4 | Internally by Windows, Java, Javascript |
            | UTF-32 | always 4 | Internally by private APIs |

        * Notes on UTF-8
            * UTF-8 is used by 95.9% of all the websites as of December 2nd 2020 [[web](https://w3techs.com/technologies/overview/character_encoding){:target="_blank"}]
            * UTF-8 was designed to be backward compatible with ASCII
                * It means the first 128 characters of UTF-8 map exactly to ASCII
                * It was essantial since ASCII was widespread when UTF-8 was introduced
            * To decode UTF-8, follow the marker bit patterns

            | **Bit pattern inside byte** | **Meaning** |
            | 0xxxxxxx | Beginning of 1 byte character (also an ascii character) |
            | 110xxxxx | Beginning of 2 byte character |
            | 1110xxxx | Beginning of 3 byte character |
            | 11110xxx | Beginning of 4 byte character |

            * UTF-8 doesn't have big/little endian since it is based on individual bytes
            * But UTF-16 has the big/little endian problem! See [[web](https://www.w3.org/International/questions/qa-byte-order-mark#){:target="_blank"}]

<br/>
#### Encoding and the web

* HTML file: Chicken and egg problem from Joel Spolsky's blog [[web](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/){:target="_blank"}]
    > How can you read the HTML file until you know what encoding it’s in?

   * It is not a large problem since almost all web pages use UTF-8. But still...
    
    > Luckily, almost every encoding in common use does the same thing with characters between 32 and 127, so 
    you can always get this far on the HTML page without starting to use funny letters:

```html
        <html>
        <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
```
* HTML 5
    * The default character encoding is UTF-8
    * Always declare the encoding used in HTML page
    * The declaration should fit completely within the first 1024 bytes at the start of the file
