# Notes on PDF file format

## To do
* Adobe specs? https://www.adobe.com/devnet/pdf/pdf_reference.html
* https://blog.didierstevens.com/category/pdf/
* https://blog.idrsolutions.com/series-article-index/ ?


## File structure

A basic conforming PDF file "shall be" constructed of four elements:

* A one-line header identifying the version of the PDF specification to which
  the file conforms
* A body containing the elements that make up the document contained in the
  file
* A cross-reference table containing information about the indirect objects in
  the file
* A trailer giving the location of the cross-reference table and of certain
  special objects within the body of the file

This initial structure may be modified by later updates, which append
additional elements to the end of the file.


### File header

`%PDF-` followed by version number of the form `1.N` (e.g. `%PDF-1.7`).

If a PDF file contains binary data, as most do, the header line shall be
immediately followed by a comment line containing at least four binary
characters -- that is, characters whose codes are 128 or greater. This ensures
proper behaviour of file transfer applications that inspect data near the
beginning of a file to determine whether to treat the file's contents as text
or as binary.


## Comments

Any PERCENT SIGN (25h) outside a string or stream introduces a comment,
consisting of all characters after the PERCENT SIGN and up to but not including
the end of the line, including regular, delimiter, SPACE (20h), and HORIZONTAL
TAB characters (09h). A conforming reader shall ignore comments and treat them
as single white-space characters (i.e. a comment separates the token preceding
it from the one following it).


## References

* [Document Management -- Portable Document Format -- Part 1: PDF 1.7, First Edition (Jul 2008)](https://wwwimages2.adobe.com/content/dam/Adobe/en/devnet/pdf/pdfs/PDF32000_2008.pdf)
