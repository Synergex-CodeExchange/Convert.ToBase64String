# Convert.ToBase64String<br />
**Created Date:** 12/29/2008<br />
**Last Updated:** 2019-09-27<br />
**Description:** Convert is a class that converts a base data type to another base data type.<br />
**Platforms:** Windows; Unix; OpenVMS<br />
**Products:** Synergy DBL<br />
**Minimum Version:** 9.1.5b<br />
**Author:** Tod Phillips
<hr>

**Additional Information:** Its current implementation has only one static method (ToBase64String) with several overloads. It can be used in conjunction with the AsciiEncoding class's "GetBytes" method (available as a separate download on the CodeExchange) or accessed with an alpha parameter instead.

In order to use this class, it must first be prototyped with the DBLPROTO
                        utility.  Ensure that your SYNIMPDIR and SYNEXPDIR environment variables
                        have been set, then run the protyper by typing:

                                dblproto Convert

                        from a command prompt in the directory where the Convert.dbl file has
                        been saved. (Alternately, import the file into a Workbench project, right-
                        click the project in the Projects tab and select "Generate Synergy
                        Protypes..."). The included file can then be compiled and added to any
                        library or ELB.  To use the provided class methods, simply type

                                import SynPSG.System

                        at the top of your source code. (See Example, below).

CLASS:                  Convert      (Public)

ENUMERATION(S):
        Public Enumeration Base64FormattingOptions
                 InsertLineBreaks
                 None

CONSTRUCTOR:
        None (Convert should include only static members, so it does not need
        instantiation to access its members).

PROPERTIES:
        None

METHOD(S):
        ToBase64String
                Overloaded. Converts the value of an array of 8-bit unsigned integers
                to its equivalent String representation encoded with base 64 digits.

                Usage & Overloads

                Convert.ToBase64String(a_ByteArray[#], Base64FormattingOptions)
                        a_ByteArray is a Dynamic System Array of 8-bit unsigned integers
                                to be converted to Base64
                        a_formatOption is a Base64FormattingOptions enumeration which causes
                                the method to either insert a line break every 76 characters (default),
                                or to not insert line breaks at all.

                Convert.ToBase64String(a_ByteArray[#])
                        a_ByteArray is a Dynamic System Array of 8-bit unsigned integers
                                to be converted to Base64.

                Convert.ToBase64String(a a_Alpha)
                        a_Alpha is an alphanumeric string that will be returned as a Base64 string


EXAMPLE(S):

        The following program demonstrates the use of the ToBase64String method.

;; Program to demonstrate the Convert.ToBase64String method.

import SynPSG.System

main<br />
record<br />
        b64String       ,string<br />
        oldString       ,a256<br />
endrecord<br />

proc<br />
        open(1,O,'TT:')<br />
        oldString = "This is a test."<br />
        writes(1,"Original String:")<br />
                writes(1,%atrim(oldString))<br />
                writes(1,"")<br />
        b64String = Convert.ToBase64String(%atrim(oldString))<br />
        writes(1,"Converted String:")<br />
        writes(1,b64String)<br />
end
