# Table of Contents #


# Global section #
This section contains directives global in scope.

  * pre\_filters, post\_filters: Optional list of global filters to run before (pre\_filters) or after (post\_filters) the definition file generation. Each filter may define a set of filter specific arguments in the 'args' attribute.
    * 'name': Name of the filter used to lookup the filter class to use. Valid values: There are currently no implementations.
  * per\_file\_pre\_filters, per\_file\_post\_filters: Optional list of file filters run before (pre\_filters) or after (post\_filters) the generation of each file. The pre\_filters here are run BEFORE the individual filters specified in the files section and the post\_filters are run AFTER the individual filters specified in the files section. For a list of possible filters and arguments, see the "Files section".
  * per\_definition\_pre\_filters, per\_definition\_post\_filters: Optional list of definition filters run before (pre\_filters) or after (post\_filters) the generation of each definition. The pre\_filters here are run BEFORE the individual filters specified in the definitions section and the post\_filters are run AFTER the individual filters specified in the definitions section. For a list of possible filters and arguments, see the "Definitions section".

# Files section #
This section contains a list of settings and configurations for each file that gets generated.

  * path: Path to the definitions file to be generated, relative to the def path defined in the global section.
  * pre\_filters, post\_filters: Optional list of file level filters to run before (pre\_filters) or after (post\_filters) the file has been generated. Each filter may define a set of filter specific arguments in the 'args' attribute.
    * 'name': Name of the filter used to lookup the filter class to use. Valid values:
      * 'PrintFilter': Does not modify input. Just prints it.
      * 'WriteFileFilter': Writes files out locally.
  * file\_header: List of strings that get printed in the beginning of the file.
  * generators: List of generator blocks.

## Generators section ##
  * name: The generator defines the source of the information.Valid values:
    * 'DnsGenerator': For definitions generated based on hostnames with a simple DNS resolver. Note that the resolver might not return all addresses used for one hostname depending on the implemented DNS load balancing.
  * definitions: List of definition blocks.

### Definitions section ###
  * name: Name of the definition that gets generated. This name is used in the definitions file and can be used in policies to reference the definition.
  * header: Optional list of header strings that will be printed before the definition.
  * pre\_filters, post\_filters: Optional list of definition level filters to run before (pre\_filters) or after (post\_filters) the definition has been generated. Each filter may define a set of filter specific arguments in the 'args' attribute.
    * 'name': Name of the filter used to lookup the filter class to use. Valid values:
      * 'SortFilter': Sort the input list and return one list containing IPv4 sorted, IPv6 sorted.
      * 'AlignFilter': Take the input list and definition name and create nicely formated output.
  * networks: Contains  a list of descriptions about how to get a complete set of networks/IPs for one definition. This section contains generator-specific configuration directives".

### Network directives for DnsGenerator ###

#### Networks section ####
  * names: List of hostnames that should be resolved.
  * types: List of types the output should be filtered for. Valid values:
    * 'A': Filter for IPv4 addresses.
    * 'AAAA': Filter for IPv6 addresses.