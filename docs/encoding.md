When you’re visiting a simple web page today there are a bunch of different techniques in use, including qualified guessing, that try to make sure you see the correct characters.

The most obvious place you as a developer will notice is in the HTML document itself. You could add a <meta charset="ISO-8859-1"> tag in the <head> of the HTML to tell the browser that you are using the western Europe latin character set. If that tag is missing, the browser will look at the response headers from the web server and may find an additional charset declaration in the Content-Type header. The HTML document can also override the Content-Type sent by the web server by adding a <meta http-equiv="content-type"> tag.

But the real fun didn’t start until these three different places said different things about the charset in use or when it turns out that the declared character set isn’t what is actually in use in the rest of the document. There was a reason old versions of Chrome and Firefox allowed the user to change encoding manually.

### Unicode

Unicode encoding schemes like UTF-8 are more efficient in how they use their bits. With UTF-8, if a character can be represented with 1 byte that’s all it will use. If a character needs 4 bytes it’ll get 4 bytes. 

The hexadecimal numbering system is used as it’s a shorter way to reference large numbers. That’s why you’ll see things like U+1F4A9 or \u1F4A9 in emoji tables.

Character       |     HEX       |       Binary  
----            |   ------      |       ------
💩	            |   U+1F4A9	     |   0001 1111 0100 1010 1001

### Javascript

JavaScript engines use UTF-16 internally, another variable length encoding. If you remember UTF-16 is a lot like UTF-8 except that the lowest amount of bits used is 16. Simple characters like ‘C’ use 16 bits, while fancy characters use 32 bits.

In JavaScript, strings are treated as UTF-16 code units, all that means really is that you might have to use two code points to reference a character.

```
let poop = '💩';
console.log( poop.length );
// Outputs 2
```