jsisie
======

A .NET parser for SIE files that can read files of version 1 to 4 (including 4i)

Follow [this link](https://sie.se/vadsie/) for swedish versions and [this link](https://sie.se/in-english/) for english versions of the SIE specifications.

_Sadly the files used for testing the parser are not available from sie.se at the moment and I haven't got the permission to distribute the ones that were available when I wrote the tests._

**Read a SIE file**

To read a file create an instance of SieDocument and call ReadDocument.

There are some bool properties in SieDocument that changes how the parsing works:

+ IgnoreMissingOMFATTNING: If true the parser will not flag a missing #OMFATTN as an error.
+ IgnoreBTRANS: If true #BTRANS (removed voucher rows) will be ignored.
+ IgnoreRTRANS: If true #RTRANS (added voucher rows) will be ignored.
+ StreamValues: If true don't store values internally. The user has to use the Callback class to get the values. Usefull for large files.
+ ThrowErrors: If false then cache all Exceptions in SieDocument.ValidationExceptions

**Not all features are implemented yet:**

+ #UNDERDIM: There are no instances of this in the published example files.

**Write a SIE file**

To write a file create an instance of SieDocumentWriter and call WriteDocument

**Compare SIE files**

To compare SIE files call the static method Compare on SieDocumentComparer. It will return a List&lt;string&gt; with differences between the files.  


Even if you use this parser you should get familiar with the file specification.
I have not made any extensive efforts to validate the resulting data against the files so please do your validation and tell me if you find any errors.


To install this package via nuget write

	Install-Package jsisie

in the nuget console in Visual Studio 


**Java**

There's a Java version of this parser here: https://github.com/perNyfelt/SIEParser  


**Change log**

+ 2017-12-22	Add #PROGRAM to the document comparer. Enable the test program to compare two files via command line.
+ 2020-07-05	Now supports writing KSUMMA

