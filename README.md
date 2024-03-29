# xidel
Xidel for MacOS 12+. 

A copy of `xidel-0.9.9.201903.mac.bykonings.zip`, from https://sourceforge.net/projects/videlibri/files/Xidel/Xidel%20development/

Xidel is mainly intended for older Macs and Linux/Windows.

Someone published a 0.9.9 binary that runs on MacOS 12 Monterey:

https://sourceforge.net/projects/videlibri/files/Xidel/Xidel%20development/xidel-0.9.9.201903.mac.bykonings.zip/download

Download it and run it with:

```
cd path/to/xidel/binary
./xidel\ 2 <commands>
```

To use the alias 'xidel', download the file above to wherever you
want to keep the tool, then add that path to your PATH in `.bashrc`:

`export PATH="/Path/to/folder/:$PATH"`

Then add an alias like this:

`alias xidel=xidel\ 2`

## Usage and options

The following command line options are valid: 

```
--data=<string>                         Data/URL/File/Stdin(-) to process (--data= prefix can be omitted)
--download=<string>                     Downloads/saves the data to a given filename (- prints to stdout, . uses the filename of the url)


Extraction options:

  --extract=<string>  or -e             Expression to extract from the data.
                                        If it starts with < it is interpreted as template, otherwise as XPath expression
  --extract-exclude=<string>            Comma separated list of variables ignored in an extract template. (black list) (default _follow)
  --extract-include=<string>            If not empty, comma separated list of variables to use in an extract template (white list)
  --extract-file=<file>                 File containing an extract expression (for longer expressions)
  --extract-kind=<string>               How the extract expression is evaluated. Can be auto (automatically choose between xpath/template), xpath{|2|3}, xquery{|1|3}, css, template or
                                        multipage
  --css=<string>                        Abbreviation for --extract-kind=css --extract=...
  --xpath=<string>                      Abbreviation for --extract-kind=xpath3 --extract=...
  --xquery=<string>                     Abbreviation for --extract-kind=xquery3 --extract=...
  --xpath2=<string>                     Abbreviation for --extract-kind=xpath2 --extract=...
  --xquery1=<string>                    Abbreviation for --extract-kind=xquery1 --extract=...
  --xpath3=<string>                     Abbreviation for --extract-kind=xpath3 --extract=...
  --xquery3=<string>                    Abbreviation for --extract-kind=xquery3 --extract=...
  --xpath3.0=<string>                   Abbreviation for --extract-kind=xpath3.0 --extract=...
  --xquery3.0=<string>                  Abbreviation for --extract-kind=xquery3.0 --extract=...
  --xpath3.1=<string>                   Abbreviation for --extract-kind=xpath3.1 --extract=...
  --xquery3.1=<string>                  Abbreviation for --extract-kind=xquery3.1 --extract=...
  --template-file=<file>                Abbreviation for --extract-kind=multipage --extract-file=...
  --template-action=<string>            Select which action from the multipage template should be run (multiple actions separated by commas)
  --module=<file>                       Imports an xpath/xquery module
  --module-path=<string>                Search path for modules


Follow options:

  --follow=<string>  or -f              Expression selecting data from the page which will be followed.
                                        If the expression returns a sequence, all its elements are followed.
                                        If it is an HTML element with an resource property this property is used, e.g. from an A element it will follow to its @href property.
                                        If it is an object, its url property and its other properties can override command line arguments
                                        Otherwise, the string value is used as url.
  --follow-kind=<string>                How the follow expression is evaluated. Like extract-kind
  --follow-exclude=<string>             Comma separated list of variables ignored in a follow template. (black list)
  --follow-include=<string>             Comma separated list of variables used in a follow template. (white list)
  --follow-file=<file>                  File containing a follow expression (for longer expressions)
  --follow-level=<int>                  Maximal recursion deep (default: 99999)
  --allow-repetitions                   Follow all links, even if that page was already visited.


HTTP connection options:

  --wait=<float>                        Wait a certain count of seconds between requests
  --user-agent=<string>                 Useragent used in http request
  --proxy=<string>                      Proxy used for http/s requests
  --post=<string>  or -d                Post request to send (url encoded). Multiple close occurrences are joined. If the new argument starts with &, it will always be joined. If it is
                                        empty, it will clear the previous parameters. 
  --form=<string>  or -F                Post request to send (multipart encoded). See --usage. Can be used multiple times like --post.
  --method=<string>                     HTTP method to use (e.g. GET, POST, PUT)
  --header=<string>  or -H              Additional header to include (e.g. "Set-Cookie: a=b"). Can be used multiple times like --post.
  --load-cookies=<string>               Load cookies from file
  --save-cookies=<string>               Save cookies to file
  --print-received-headers              Print the received headers
  --error-handling=<string>             How to handle http errors, e.g. 1xx=retry,200=accept,3xx=redirect,4xx=abort,5xx=skip
  --raw-url                             Do not escape the url (preliminary)


Output/Input options:

  --silent or -s                        Do not print status information to stderr
  --verbose                             Print more status information
  --default-variable-name=<string>      Variable name for values read in the template without explicitely given variable name
  --print-variables=<string>            Which of the separate variable lists are printed
                                        Comma separated list of:
                                          log: Prints every variable value
                                          final: Prints only the final value of a variable, if there are multiple assignments to it
                                          condensed-log: Like log, but removes assignments to object properties(default)
  --print-type-annotations              Prints all variable values with type annotations (e.g. string: abc, instead of abc)
  --hide-variable-names                 Do not print the name of variables defined in an extract template
  --variable=<string>                   Declares a variable (value taken from environment if not given explicitely) (multiple variables are preliminary)
  --xmlns=<string>                      Declares a namespace
  --printed-node-format=<string>        Format of an extracted node: text, html or xml
  --printed-json-format=<string>        Format of JSON items: pretty or compact
  --output-format=<string>              Output format: adhoc (simple human readable), xml, html, xml-wrapped (machine readable version of adhoc), json-wrapped, bash (export vars to bash), or
                                        cmd (export vars to cmd.exe) 
  --output-encoding=<string>            Character encoding of the output. utf-8, latin1, utf-16be, utf-16le, oem (windows console) or input (no encoding conversion)
  --output-declaration=<string>         Header for the output. (e.g. <!DOCTYPE html>, default depends on output-format)
  --output-separator=<string>           Separator between multiple items (default: line break)
  --output-header=<string>              2nd header for the output. (e.g. <html>)
  --output-footer=<string>              Footer for the output. (e.g. </html>)
  --color=<string>                      Coloring option (never,always,json,xml)
  --stdin-encoding=<string>             Character encoding of stdin
  --input-format=<string>               Input format: auto, html, xml, xml-strict, json, json-strict
  --xml                                 Abbreviation for --input-format=xml --output-format=xml
  --html                                Abbreviation for --input-format=html --output-format=html
  --in-place                            Override the input file


Debug options:

  --debug-arguments                     Shows how the command line arguments were parsed
  --trace                               Traces the evaluation of all queries
  --trace-stack                         Traces the evaluation to print a backtrace in case of errors
  --trace-context                       Like trace-stack, but for the context


XPath/XQuery compatibility options:

  --no-json                             Disables the JSONiq syntax extensions (like [1,2,3] and {"a": 1, "b": 2})
  --no-json-literals                    Disables the json true/false/null literals
  --dot-notation=<string>               Specifies if the dot operator $object.property can be used. Possible values: off, on, unambiguous (default, does not allow $obj.prop, but ($obj).prop
                                        ) 
  --no-dot-notation                     Disables the dot notation for property access, like in $object.property (deprecated)
  --only-json-objects                   Do not allow non-JSON types in object properties (like  () or (1,2) instead of null and [1,2]) 
  --no-extended-json                    Disables non-jsoniq json extensions
  --strict-type-checking                Disables weakly typing ("1" + 2 will raise an error, otherwise it evaluates to 3)
  --strict-namespaces                   Disables the usage of undeclared namespace. Otherwise foo:bar always matches an element with prefix foo.
  --no-extended-strings                 Does not allow x-prefixed strings like x"foo{1+2+3}bar"
  --ignore-namespaces                   Removes all namespaces from the input document
  --no-optimizations                    Disables optimizations
  --deprecated-string-options           Replaces the old $foo; variables with the new {$foo} in arguments
  --version                             Print version number (0.9.9)
  --usage                               Print help, examples and usage information
  --quiet or -q                         -quiet,-q is outdated. Use --silent,-s
```
