# XML essential training


##  Table of contents
- [XML essential training](#xml-essential-training)
    - [Table of contents](#table-of-contents)
    - [I. Getting Started](#i-getting-started)
        - [1. what is XML](#1-what-is-xml)
        - [2. XML-related technologies](#2-xml-related-technologies)
        - [3. Describing Data with XML](#3-describing-data-with-xml)
        - [4. Advantages of XML](#4-advantages-of-xml)
        - [5. Drawbacks of XML](#5-drawbacks-of-xml)
    - [II. XML Overview](#ii-xml-overview)
        - [1. Types of XML content](#1-types-of-xml-content)
            - [a. The Document Declaration](#a-the-document-declaration)
            - [b. XML Elements (Tags)](#b-xml-elements-tags)
            - [c. XML Attributes](#c-xml-attributes)
            - [d. Comments](#d-comments)
            - [e. Character Data Sections (CDATA)](#e-character-data-sections-cdata)
            - [f. Processing Instructions](#f-processing-instructions)
            - [g. Entities](#g-entities)
        - [2. Proper XML syntax](#2-proper-xml-syntax)
            - [a. Proper XML Syntax](#a-proper-xml-syntax)
            - [b. Valid documents](#b-valid-documents)
            - [c. XML Namespaces](#c-xml-namespaces)
    - [III. Working with XML](#iii-working-with-xml)
        - [1. Our first XML file](#1-our-first-xml-file)
        - [2. XML and CSS styles](#2-xml-and-css-styles)
        - [3. Styling XML tags](#3-styling-xml-tags)
        - [4. Advance CSS with XML](#4-advance-css-with-xml)
    - [IV. Manipulating XML with the DOM](#iv-manipulating-xml-with-the-dom)
        - [1. Quick intro to the DOM](#1-quick-intro-to-the-dom)
            - [a. DOM - Document Object Model](#a-dom---document-object-model)
            - [b. Important DOM Properties](#b-important-dom-properties)
            - [c. Important DOM functions](#c-important-dom-functions)
            - [d. Document Functions and Properties](#d-document-functions-and-properties)
            - [e. Other Important Properties](#e-other-important-properties)
        - [2. Discovering document content](#2-discovering-document-content)
            - [a. "Non-standard" way to embed XML into HTML](#a-non-standard-way-to-embed-xml-into-html)
        - [3. Creating document content](#3-creating-document-content)
    - [V. XML and XPath](#v-xml-and-xpath)
        - [1. what is XPath?](#1-what-is-xpath)
            - [a. Important XPath Concepts](#a-important-xpath-concepts)
            - [b. Important DOM functions of XPath](#b-important-dom-functions-of-xpath)
            - [c. XPath Examples](#c-xpath-examples)
        - [2. Using Xpath](#2-using-xpath)
    - [VI. XML and XSLT](#vi-xml-and-xslt)
        - [1. What is XSLT?](#1-what-is-xslt)
            - [Creating XSLT Stylesheets](#creating-xslt-stylesheets)
        - [2. Using XSLT with XML](#2-using-xslt-with-xml)
            - [Common XSLT Elements](#common-xslt-elements)
            - [Example XSLT template](#example-xslt-template)
    - [VII. XSLT Examples](#vii-xslt-examples)
        - [1. Simple XSLT](#1-simple-xslt)
        - [2. Repeating items](#2-repeating-items)


## I. Getting Started
### 1. what is XML
- XML  is the eXtensible Markup Language
- XML became a  W3C recommendation in 1989
-  **XML is the foundation of several Web technologies**
    - **XHTML** - HTML  formatted as XML syntax
    - **RSS/ATOM** - used for publishing, as blog
    - **AJAX** - asynchronous Javascript and XML
    - **Web services** - using APIs over the web
- **What is XML used for?**
    - XML is used to Structure and describe information
    - XML was intended to be used over the internet
    - Used to exchange data between disparate systems

### 2. XML-related technologies
-   **XPath** - eXtensible Path Language
-   **XSLT** - XML Stylesheet Langugage Transformations
-   **XQuery** - more advanced querying language than Xpath
-   **Xpointer, Xlink** - link between and within XML documents


### 3. Describing Data with XML
Constructing data structure on extesive markup tags (make that up).
We have to send the info of a business card
```
    Hai Duong
    012 345 6789 (home)
    834 854 2344 (work)
    hduong@sdccd.edu
```

Convert this info to a markup language format
```XML
    <BusinessCard>
        <name>Hai Duong</name>
        <phone type="home"> 012 345 6789</phone>
        <phone type="work"> 834 854 2344</phone>
        <email>hduong@sdccd.edu</email>
    </BusinessCard>
```

### 4. Advantages of XML
-   XML keeps content separate from presentation
-   XML is an open format that can be read by many applications
-   XML can be used on both the client and server
-   XML has widespread support in multiple languages and runtimes

### 5. Drawbacks of XML
-   XML is not suitable for very large data sets
-   Some formats, like JSON, might be better in some cases
-   Some data types, like images, aren'r represented well
-   XML can quickly become difficult to read when complex

## II. XML Overview
### 1. Types of XML content
-   XML Document Declaration
-   Elements and Attributes
-   Comments
-   Character Data
-   Processing Instruction
-   Entity References
#### a. The Document Declaration
Technically optional, though the W3C recommends it

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes">
```
-  Identifies the file as XML document
-  Provides a place for encoding and standalone attributes
-  Must be at a very beginning; not even whitespace before it
-  Encoding attribute
    -  Defaults to UTF-8 if you don't include it
- The standalone attribute
    - Indicate whether the document is complete by itself
#### b. XML Elements (Tags)
-  **Element must have valid name**
    -  They can begin with underscore "_" or letter
    -  Followed by letters, digits, periods, hyphens, underscores
    -  Cannot use the string "xml" in any case combination
    -  **Examples of XML elements**
        -  `<_Element1>`
        -  `<My.element>`
        -  `<My-Element_Name>`
    - **Invalid tag names**
        - `<1_Tag>` - (can't begin with a number)
        - `<#Elem&ment>` - (invalid characters in names)
        - `<Xml>` - (the string xml is reserved)
#### c. XML Attributes
- Attributes are specified on opening element tags
- Must start with letter or underscore
- can be followed by digits, letters, hyphens, periods, underscores
- Attributes that begin with `xml` are reserved
- Attributes appear only once on a given element

#### d. Comments
- Comments embed human-readable information
- Defined with `<!-- content -->`
- Can go almost everywhere, except:
    - inside element brackets
    - before the document declaration

####  e. Character Data Sections (CDATA)
- Part of document, but not parsed by the XML parser
- Defined using `<![CDATA     ]>`
- Typically used to contain unescaped texture data

#### f. Processing Instructions
-   Special instructions to the XML parser
-   Have the form `<? targetName instruction ?>`
    -   The "xml" target name is reserved
    -   Can start with number or letter, then be followed by digits, letters, hyphens, periods, underscores
    - **Example: your app has multiple spell-checking modes**
        - `<? SpellCheckMode mode="en-GB" ?>`

#### g. Entities
- **Help shorten and modularize XML documents**
- **Provide markup for otherwise illegal characters**
- **General entities**
    - Replaced by parser with a full string
    - Examples: `&copyright;` or `&author;`
- **Character entities**
    - `&#060;`
    - `&amp;` or `&quot;`

### 2. Proper XML syntax
#### a. Proper XML Syntax
-   XML documents just have a single root tag
-   XML documents must be "well-formed"
-   Empty tags must be closed with `/>`
    - Instead of `<elem></elem>`, use `<elem />`
- **Attribute value cannot be minimized**
    - `<option selected>` is illegal, use `<option selected="selected">`
- **Attribute values must be inside of quotes, single or double**
    - `<elem attr=val>` is illegal, use `<elem attr="val">`
- Tags have to be properly nested inside of each other

#### b. Valid documents
- in order to have a well-formed document -> aplly rules
- **"Valid" XML Documents**
    - **Docment type definitiions (DTDs)**
        - Simple to use, but not very powerful
        - Writing using a syntax that is different than XML
    - **XML schema**
        - Much more powerful and flexible than DTD
        - Written using XML syntax rules
#### c. XML Namespaces
-   Form: `<html xmlns="http://www.w3.org/1999/xhtml">`
-   Prevent conflict between tags from different languages
    - HTML table
        ```HTML
            <table>
                <tr>
                    <td>Cell Content</td>
                </tr>
                <tr>
                    <td>Cell Content</td>    
                </tr>
            </table>
        ```
    - XML table
        ```XML
            <table>
                <type>Coffee</type>
                <price>199.99</price>
                <material>wood</material>
                <stock>25</stock>
            </table>
        ```
    -   Have to signal the browser which is which
        `<html xmlns="http://www.w3.org/1999/xhtml" xmlns:furn="http://www.furniture.org/items">`
    -   Mixing HTML syntax and XML syntax. This is how XML Namespaces are used, so that you can combine data from separate sources without having to worry about name collisions.
         ```XML
            <table>
                <tr>
                    <td>
                        <furn:table>
                            <furn:type> Coffee</furn:type>
                            <furn:price>199.99</furn:price>
                            <furn:material>Wood</furn:material>
                            <furn:stock>25</furn:stock>
                        </furn:table>
                    </td>
                </tr>
            </table>
        ```
## III. Working with XML
### 1. Our first XML file
```XML
    <!-- firstXML.xml file -->
    <?xml version="1.0" encoding="utf-8"?>
    <FirstTag>
        This is our first XML file
        <!-- This is a comment -->
    </FirstTag>
```
-   if we open this xml in chrome, it will say the file is missing stylying sheet. But it is a solid raw XML file.

### 2. XML and CSS styles
-   We create a stylesheet file for XML element
    ```css
    <!-- firstXML.css file -->
    FirstTag{
        display: block;
        font-family: Arial;
        font-size: large;
        color:blue;
    }
    ```
-   Then we need to link the stylesheet into the xml
    ```xml
        <!-- firstXML.xml file -->
        <?xml version="1.0" encoding="uft-8">
        <?xml-stylesheet type="text/css" href="FirstXML.css">
        <FirstTag>
            This is your first XML file
            <!-- this is the comment -->
        </FirstTag>
    ```

### 3. Styling XML tags
- Let's take a look at xml root file for business card
    ```xml
        <!-- businessCard.xml file -->
        <?xml version="1.0">
        <?xml-stylesheet type="text/css" href="businesscard.css">
        <BusinessCard>
            <Name>Hai Duong</Name>
            <phone type="mobile"> (123) 456 7890</phone>
            <phone type="work"> (456) 456 7890</phone>
            <phone type="fax"> (789) 456 7890</phone>
            <email>hduong@sdccd.edu</email>
        </BusinessCard>
    ```
- Let's take a look at the css tags
    ```css
        /* BusinessCard.css file */
        BusinessCard{
            //some css styling code for <BusinessCard> xml tag
        }
        Name{
            //some css styling code for <Name> xml tag
        }
        phone{
            //some css styling code for <phone> xml tag
        }
        email{
            //some css styling code for <email> xml tag
        }
    ```
### 4. Advance CSS with XML
-   Let's take a look at syntag that have labels or attributes, which are nested inside other syntag container.
    ```xml
        <!-- AdvanceBusinessCard.xml file -->
        <?xml version="1.0">
        <?xml-stylesheet type="text/css" href="advanceBusinesscard.css">
        <BusinessCards>
            <BusinessCard>
                <Name>Hai Duong</Name>
                <phone type="mobile" primary="primary"> (123) 456 7890</phone>
                <phone type="work"> (456) 456 7890</phone>
                <phone type="fax"> (789) 456 7890</phone>
                <email>hduong@sdccd.edu</email>
            </BusinessCard>

            <BusinessCard>
                <Name>Joel Arias</Name>
                <phone type="mobile"> (123) 456 7890</phone>
                <phone type="work" primary="primary"> (456) 456 7890</phone>
                <phone type="fax"> (789) 456 7890</phone>
                <email>hduong@sdccd.edu</email>
            </BusinessCard>
        </BusinessCards>
    ```
-   We want to display the attributes and labels of business card by using css pseudo class
    ```css
         /* BusinessCard.css file */
        BusinessCard{
            //some css styling code for <BusinessCard> xml tag
        }
        Name{
            //some css styling code for <Name> xml tag
        }
        phone{
            //some css styling code for <phone> xml tag
        }
        email{
            //some css styling code for <email> xml tag
        }
        /* adding label 'email:' before email address */
        email::before {content:"email: "}
        /* adding the value of attribute "type" before the phone number */
        phone::before {content: attr(type) ": "}
        /* adding the (primary) after the primary phone */
        phone[primary]::after {content: " (" attr(primary) ")"}
    ```
-   **Final Display**
    ```
        Hai Duong
        mobile: (123) 456 7890 (primary)
        work: (456) 456 7890
        fax: (789) 456 7890
        email: hduong@sdccd.edu
        
        Joel Arias
        mobile: (123) 456 7890 (primary)
        work: (456) 456 7890
        fax: (789) 456 7890
        email: jarias@sdccd.edu
    ```

## IV. Manipulating XML with the DOM
### 1. Quick intro to the DOM
#### a. DOM - Document Object Model
-   Standard set of APIs for working with document content
-   Platform, browser, and language neutral
-   Represents document content as a tree structure
-   Contents fo the tree are called Nodes
#### b. Important DOM Properties
| Property | Description |
| :------- | :---------- |
|nodeName| The name of the node; for tags, it is the tag name. For comments and text, it is  special names like "#comment" or "#text"|
|nodeType| The node's type; element, comment, text, etc...|
|nodeValue| The node's  value; varies based on node type|
|attributes| For elements only; an array of attributes and values|
|parentNode| The parent of this node; null if there is no parent or "#text"|
|childNodes| Array of child nodes; empty if there are none|
|firstChild, lastChild| References to first and last child of this node|
|previousSibling, nextSibling| References to previous and next sibling of this node|


#### c. Important DOM functions
| Property | Description |
|:-------|:-------|
|appendChild( ) | Inserts an element and the end of a given element's children|
|removeChild( )| Removes an element from the parent|
|insertBefore( )| Insert a new node before the given node|
|replaceChild( )| Replaces an existing node inside the parent with a new one|

#### d. Document Functions and Properties
|Property| Description|
|:-----|:-----|
|documentElement| Refercene to the root document element|
|createElement( )| Creates new element that can be inserted in document|
|createTextNode( )| Creates new text node |
|createComment( )| Create new comment|
|createCDATASection( )|Creates new CDATA section|
|getElementsByTagName( )| Returns array of tags that match given tag name|
|getElementById( )| Returns a single element with a given ID|

#### e. Other Important Properties
|Property| Description|
|:-----|:-----|
|getAttribute( )|Gets the value of a given attribute on an element|
|setAttribute( )| Sets the value of an attribute on an element|
|removeAttribute( )| Removes an attribute from an element|
|innerHTML| Gets or sets the HTML content of the given tag|
|data| Gets the text data of an Element, Comment, or Text node|

### 2. Discovering document content
#### a. "Non-standard" way to embed XML into HTML
```html
<!-- index.html -->
<body>
    <xml id="xmldata1" style="display:none">
        <BusinessCard>
            <Name> Joel Arias</Name>
            <phone type="mobile">(123) 456 7890</phone>
            <email>jarias@sdccd.edu</email>
        </BusinessCard>
    </xml>

    <button id="showBCardData">Show business card data</button>
</body>
``` 
- Browser displays only the html syntax. The xml was embeded is in the shadow DOM for data
- Once the xml data is in the shadow DOM, we can manipulate its data with Javascript
    ```js
        /* <Script>*/
        window.addeventListener('load', function(){
            document.querySelector('#showBCardData').addEventListener('click',displayBusinessCardData());
        });

        function displayBusinessCardData(){
            /* target the xml data by getting its id*/ 
            var xmldata1 = document.getElementById('xmldata1');
            /* target the businessCard tag, first child*/
            var bizCard = xmldata1.getElementsbyTagName('BusinessCard')[0];
            /* grab the value inside Name tag*/
            var name = "Name: " + bizCard.getElementsByTagName('Name')[0].firstChild.data;
            /* grab the value inside Email tag*/
            var email = "Email: " + bizCard.getElementsByTagName('email')[0].firstChild.data;
            alert("BusinessCard Data: \n\n" + name + "\n" + email);
        }
    ```
### 3. Creating document content
- We can use the DOM to create new xml element.
    ```html
        <body>
            <xml id="xmldata1" style="display:none">
                <BusinessCards>
                    <BusinessCard>
                        <Name>Joe Marini</Name>
                        <phone type="mobile">(415) 555-4567</phone>
                        <phone type="work">(800) 555-9876</phone>
                        <phone type="fax">(510) 555-1234</phone>
                        <email>joe@joe.com</email>
                    </BusinessCard>
                </BusinessCards>	
            </xml>
        </body>
    ```
- Using the script to grab the data from xml and then create html `<div>` with `classes` in html fashion.
    ```js
        /* Script */
    function createBizCards(){
        /* get references to the data island and the array of business cards */
        var xmlData = document.getElementById("xmldata1");
        var bizCards = xmlData.getElementsByTagName("BusinessCard");

        /* for each business card, loop over its tags and create a new <div> to
            each card along with the information for all the fields */
        for (var i=0; i < bizCards.length; i++) {
            var currentCard = bizCards[i]; /* store a reference to the current <BusinessCard> */
            
            /* make a new <div> for the whole card */
            var newCard = document.createElement("div");
            newCard.setAttribute("class","BusinessCard");
            
            /* now create a <div> for the name */
            var newName = document.createElement("div");
            newName.setAttribute("class","Name");
            var nameStr = document.createTextNode(currentCard.getElementsByTagName("Name")[0].firstChild.data);
            newName.appendChild(nameStr);
            newCard.appendChild(newName);
            
            /* create separate <divs> for the phones */    
            var phones = currentCard.getElementsByTagName("phone");
            var newPhone;
            for (var j=0; j < phones.length; j++) {
                newPhone = document.createElement("div");
                newPhone.setAttribute("class","phone");
                var labelStr = currentCard.getElementsByTagName("phone")[j].getAttribute("type") + ": ";
                var phoneStr = document.createTextNode(labelStr + currentCard.getElementsByTagName("phone")[j].firstChild.data);
                newPhone.appendChild(phoneStr);
                newCard.appendChild(newPhone);
            }
            
            /* create a <div> for the email */
            var newEmail = document.createElement("div");
            newEmail.setAttribute("class","email");
            var emailStr = document.createTextNode("email: " + currentCard.getElementsByTagName("email")[0].firstChild.data);
            newEmail.appendChild(emailStr);
            newCard.appendChild(newEmail);

            /* now add the new <div> containing the card info to the web page */
            document.getElementsByTagName("body")[0].appendChild(newCard);
        }
    }
    /* Execute the function after the window load*/
    window.addEventListener("load",createBizCards);
    ```
## V. XML and XPath
### 1. what is XPath?
- W3C standard for accessing data in XML
- Fundamental part of XSLT, XQuery, and others
- Defines a **path** into an XML document
- Learn more at [xpath w3c](http://www.w3.org/TR/xpath)

Comment example of XPath
```html
<html>
    <head>
        <title> Document </title>
    </head>
    <body>
        <p>praragraph 1</p>
        <p>praragraph 2</p>
        <p>praragraph 3</p>
    </body>
</html>
```
- In order to access the title's text "Document", we use xpath `/html/head/title`
- In order to access the p tags we use `/html/body/p`
- In order to access the paragraph 1 text we use `/html/body/p[1]`
    - Note that **XPATH** use 1 based array system.

#### a. Important XPath Concepts
-   It's a very compact syntax, quick to learn
-   The path expression is a series of location steps
    -   Context node - path evaluation starts from here
    -   Axis - relation between context and selected nodes
    -   Predicates - further refinements to selection process

#### b. Important DOM functions of XPath
|Path Expression|Description|
|:-----|:-------|
|/|Select the root tag in the document|
|/rootTag|Select the root tag, but only if it is named "rootTag"|
|//tagName| Find all "tagName" elements anywhere in the document|
|text( )|Select the text context of the current node|
|@name| Select the "name" attribute of the current node|
|..|Select the parent of the current node|

#### c. XPath Examples
- Select the fifth chapter under the doc tag
    - `/doc/chapter[5]`
- Select the last paragraph tag in the body element
    - `/body/p[last()]`
- Select p tags that have a class attribute equal to "a"
    - `/body/p[@class='a']`
- Select all p tags in the document with class and style attributes
    - `//p[@class and @style]`

### 2. Using Xpath
**Example 1:**
```xml
<?xml version="1.0"?>
<BusinessCard>
	<Name>Joe Marini</Name>
	<phone type="mobile">(415) 555-4567</phone>
	<phone type="work">(800) 555-9876</phone>
	<phone>(510) 555-1234</phone>
	<email>joe@joe.com</email>
</BusinessCard>
```
- Install XML tools plugin in VS code
- open the command line (Ctrl shift P) and type `xpath` to select **XML tools: evaluate Xpath**
- to select **Name** element, type
    - `/BusinessCard/Name`
- to select last **phone** element, type
    - `/BusinessCard/phone[last()]`
- to select the **Name** element, which contain 'Joe'
    - `/BusinessCard/Name[contains(text(),'Joe')]`
- to select all the **phone** element that has type attribute
    - `/BusinessCard/phone[@type]`
- to select every phone that has the type=work, type
    - `//phone[@type='work']`

---
**Example 2: select with sibling attribute's specification**
```xml
<?xml version="1.0"?>
<items>
	<item id="item1">
		<name>Mocha</name>
		<type>Coffee</type>
		<photo>photos/candles.jpg</photo>
	</item>
	<item id="item2">
		<name>Decaf</name>
		<type>Coffee</type>
		<photo>photos/teacup.jpg</photo>
	</item>
	<item id="item3">
		<name>Raspberry Zinger</name>
		<type>Tea</type>
		<photo>photos/teapot_white.jpg</photo>
	</item>
	<item id="item4">
		<name>Earl Grey</name>
		<type>Tea</type>
		<photo>photos/teapot_bone.jpg</photo>
	</item>
</items>
```
-   Select the photo element if it realte to coffee, type
    -   `/items/item[type='coffee']/photo`
    -   we didn't use `@` inside the bracket, so that we can select the 

## VI. XML and XSLT
### 1. What is XSLT?
- eXtensible Stylesheet Language Transformations
- Different than CSS - applies templates to XML data
- XSLT is written using XML syntax itself
- Can transform XML into almost anything
- Can perform operations directly on the data
- Learn more at [XSLT](http://www.w3.org/TR/xslt)

#### Creating XSLT Stylesheets
-   Defined using the `<xsl:stylesheet>` root tag
-   Typically contain `<xsl:template>` tags
-   Templates are matched to XML tags in the source data
-   The contents of the template replace the source XML
-   Templates contain other XSLT directives
-   Templates can also be invoked by name
-   **How XSLT Work**
    -   `XML document` --> **`XSLT Transformation Engine`** --> Result Document (more XML, PDF, Word)

### 2. Using XSLT with XML
#### Common XSLT Elements
-   `<xsl:stylesheet>`
-   `<xsl:template match="xpath expression">`
-   `<xsl:value-of select="xpath">`
-   `<xsl:attribute>`
-   `<xsl:text>`
-   `<xsl:for-each select="xpath">`
-   `<xsl:if test="condition">`
-   `<xsl:choose>`, `<xsl:when>`, `<xsl:otherwise>`
-   `<xsl:sort select="">`

#### Example XSLT template
```html
    /* Name space*/
   <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
        /* catch the element, tag of xml file*/
        <xsl:template match="/SimpleTag">
            <html>
                <head>
                    <title>XSLT example</title>
                </head>
                <body>
                    <h1>
                        /* grab the value of that SimpleTag*/
                        <xsl:value-of select="text()"/>
                    </h1>
                </body>
            </html>
        </xsl:template>
   </xsl:stylesheet> 
```

## VII. XSLT Examples
### 1. Simple XSLT
-   Establish the xml file
    ```xml
    <?xml version="1.0"?>
    <JavacoTea>
        Try our new Herbal Tea!
    </JavacoTea>
    ```


- Associate the simpleXSLT.xml file with the stylesheet template. 
    - ading `<?xml-stylesheet type="text/xsl" href="simpletransform.xslt">` so that the data within this xml file can be grab by the xslt template
    ```xml
        <?xml version="1.0"?>
        <?xml-stylesheet type="text/xsl" href="simpletransform.xslt">
        <JavacoTea>
            Try our new Herbal Tea!
        </JavacoTea>
    ```
- CSS stylesheet can be added to the template file like normal html link
    -  adding `<link rel="stylesheet" href="simpletransform.css"/>` to the head tag
-   Using the transform template file .xslt.
    ```html
    <!-- File name simpletransform.xslt -->
    <?xml version="1.0"?> 
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
        <!-- this XSL stylesheet matches the <JavacoTea> tag in an associated XML
        file and replaces it with the HTML contents of the template. -->
        <xsl:template match="/JavacoTea">
            <html>
            <head>
                <title>New Herbal Tea Available!</title>
                 <!-- link external CSS -->
                <link rel="stylesheet" href="simpletransform.css"/>
            </head>
            <body>
                <img src="photos/javaco_tea_logo.gif" />
                <h1>
                    <!-- get the text value of this JavacoTea -->
                    <xsl:value-of select="text()"/>
                </h1>
            </body>
            </html>
        </xsl:template>

    </xsl:stylesheet>
    ```
### 2. Repeating items
- Repeatable pattern xml file
    ```xml
        <?xml version="1.0"?>
        <!-- link to the xslt file, so that the xslt file can capture data -->
        <?xml-stylesheet type="text/xsl" href="repeating_items.xslt"?>
        <items>
            <item available="no">
                <name>Mocha</name>
                <type>Coffee</type>
                <photo>photos/candles.jpg</photo>
            </item>
            <item available="yes">
                <name>Decaf</name>
                <type>Coffee</type>
                <photo>photos/teacup.jpg</photo>
            </item>
            <item available="no">
                <name>Raspberry Zinger</name>
                <type>Tea</type>
                <photo>photos/teapot_white.jpg</photo>
            </item>
            <item available="yes">
                <name>Earl Grey</name>
                <type>Tea</type>
                <photo>photos/teapot_bone.jpg</photo>
            </item>
        </items>
    ```
- Looping the data in template file
```html
    <?xml version="1.0"?> 
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
        <!-- matching template with xml file right at the root path -->
        <xsl:template match="/">
            <html>
            <head>
                <title>Our Items</title>
                <style>
                h1 { color:#0D3427 }
                img { margin: 0px 10px 0px 10px }
                body { background-color: #DACFE5; font-family:Arial, Helvetica, sans-serif }
                </style>
            </head>
            <body>
                <!-- LOOPING WITH FOR_EACH to return a collection-->
                <xsl:for-each select="/items/item">
                    <h1>
                        <!-- creating image html tag -->
                        <img>
                            <xsl:attribute name="src">
                                <xsl:value-of select="photo"/>
                            </xsl:attribute>
                        </img>
                        <!-- creating h1 text tag -->
                        <xsl:value-of select="name"/>
                        <xsl:text>...</xsl:text>
                        <xsl:value-of select="type"/>
                    </h1>

                </xsl:for-each>
            </body>
            </html>
        </xsl:template>
    </xsl:stylesheet>
```