pdf2alto
========

pdf2alto is a tool for extracting word-level bounding boxes from
PDFs and presenting them in ALTO.  

The ALTO is a little crazy, as it does not provide bounding boxes 
for the Page, PrintSpace, TextBlock, or TextLine, and in fact only 
provides only one of each for each page, no matter how the 
individual Strings on the Page are arranged.  For my use case of
search hit highlighting of individual words or groups of words,
this is Good Enough.  

The word segmentation code is geared toward separating ordinary
English words, not recognizing email addresses, domain names, or
telephone numbers.  For example, it will split a domain name with 
internal periods into a sequence of words.  Words broken across
lines will yield two bounding boxes, one for each half of the 
word, but both Strings will have the full word as their CONTENT.

pdf2alto assumes that the PDF measures distances in points.  It
produces an ALTO file with measurements in 1200ths of an inch.

This package provides the class **PrintWordLocations**, which is
a minor modification of Ben Litchfield's example class
**PrintTextLocations**, included in the source distribution
of [Apache PDFBox](http://pdfbox.apache.org).  You will need
PDFBox to compile and use this class.  A sample Bash script
to drive the class is also provided.

-- 
Michael Slone
