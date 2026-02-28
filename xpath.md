# Xpath

## Quick Start

```text
//h2/a[contains(@class 'a-text-normal')]
```

- //book : Selects all book elements no matter where they are in the document.
- /bookstore : Selects the root element bookstore.
- bookstore : Selects all nodes with the name "bookstore".
- //title[@lang] : Selects all the title elements that have an attribute named lang.
- //title[@lang='en'] : Selects all the title elements that have a "lang" attribute with a value of "en".
- /bookstore/book[1] : Selects the first book element that is the child of the bookstore element.
- /bookstore/book[last()-1] : Selects the last but one book element that is the child of the bookstore element.
- /bookstore/book[position()<3] : Selects the first two book elements that are children of the bookstore element.
- /bookstore/\* : Selects all the child element nodes of the bookstore element.
- //title[@\*] : Selects all title elements which have at least one attribute of any kind.
- /bookstore/book/title | //price : Selects all the title elements of the book element of the bookstore element AND all the price elements in the document.
- child::book : Selects all book nodes that are children of the current node.
- child::text(): Selects all text node children of the current node.
- descendant::book : Selects all book descendants of the current node.
- ancestor::book : Selects all book ancestors of the current node.
- /bookstore/book/price[text()] : Selects the text from all the price nodes.
