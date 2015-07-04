# mini-XMLUnit4php
Mini XMLUnit for PHP


[XMLUnit](http://xmlunit.sourceforge.net/userguide/html/index.html#What%20is%20XMLUnit) is a unit testing framework for test XML with Java software.  At PHP world we have similar needs, so, we can start with the same requiriments than XMLUnit. Here it is "mini" because we will stop with the basic features (you can [install a mature framework](http://xmlunit.sourceforge.net/) for more complex tasks). 


## What is mini-XMLUnit?

**Mini-XMLUnit4php** enables [xUnit-style](https://en.wikipedia.org/wiki/XUnit) assertions to be made about the content and structure of [XML](https://en.wikipedia.org/wiki/XML). It is an open source project that grew out of a need to compare "working XML" with a "reference XML".

The problem that we faced was how to verify that the  "working XML" (ex. system generated) is correct. Obviously we could use a DTD or a schema to validate the "working XML", but this approach wouldn't allow us to distinguish between valid XML with correct content (e.g. element `<foo>bar</foo>`) and valid XML with incorrect content (e.g. element `<foo>baz</foo>`). What we really wanted was an `assertXMLEqual()` method, so we could compare the "reference XML" and the "working XML". And that was the beginning of *mini-XMLUnit*.
 
## Requirements 
...
### Functional requirements
... 

* ignoreWhitespace: see http://xmlunit.sourceforge.net/userguide/html/ar01s02.html 
* canonize: https://en.wikipedia.org/wiki/Canonical_XML and [C14N()](http://php.net/manual/en/domnode.c14n.php)
* 
...
### Full and fragment comparisons
....

### Choose the reference by webservice parameters
...
### Performance
.. no performance requirements...

--------

## Config and main methods

```php
// change the default configs:
$config = [
   'preserveWhiteSpace'=>TRUE,   // as domDocument config. Do not remove redundant white space.
   'normalizeSpace'=>TRUE,       // any UTF8 "spacer" symbol, like tab, nbsp, etc.
   'canonize'=>TRUE,
   'normalizeEntities'=>TRUE,     // coverts all to UTF8
   'reducetoASC'=>TRUE,     // coverts all contents to ASCII content (lost UTF8 special symbols)
   'reducetolower'=>TRUE,     // coverts all contents to lowercase (UTF8 or not)
];
```

### IO methods

* $mini->A->loadXML($A_xmlString); $mini->B->load($B_xmlFile);
* ...
* ....

### Assert methods

$mini->full_isEqual(); // conform ignoreWhitespace, canonize, etc. parameters
$mini->full_hasSameNodePath();  // see DOMNode::getNodePath()
$mini->full_hasSameCoutings();  // only compare number of indicated itens (elements, attributes or both)
$mini->full_hasSameContent();  // only compare nodeValues ... 

diff ...

<!-- apoio
https://github.com/junit-team/junit/wiki/Assertions

http://www.chinabtp.com/issue-with-setignorewhitespace-in-xmlunit/
http://www.chinabtp.com/how-to-read-two-xml-files-using-xmlunit/

-->
