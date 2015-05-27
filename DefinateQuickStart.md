# Table of Contents #


# Overview of Definate #
Definate is a generic framework capable of generating ACL definitions, with definitions specified in a configuration file independent of the code to generate them.

A flexible and intuitive configuration language allows that. The configuration directs a configured generator to consult an external data source to obtain IPs or networks that comprise a configured definition, then a set of filters will transform the output (the definition list) before it is written to a file or output elsewhere. This includes tasks like resolving host names to generate comments, sorting the entries, and formatting the definition as a human-readable string. Filters can run on mutliple levels (global, file, definition) and can be run before and/or after that level is passed.

In a first step, Definate will include a DNS generator as an example generator and depending on needs, other generators can easily be added later.

The definate system is designed and intended to be extensible allowing administrators to write new modules to pull definition data from whatever sources they find useful.  If you develop new definate modules that others may find useful, please send them to the capirca-dev@ mailing list so that others may benefits from your efforts.

# Quick Start Instructions #

  1. Download the latest Capirca bundle:
    * http://code.google.com/p/capirca/downloads/list
  1. Extract the files
```
tar -xvzf capirca-rXXX.tgz
```
  1. Move into the extracted directory
```
cd ./capirca
```
  1. Generate network definitions for the provided sample configuration
```
./definate.py   (alternately 'python ./definate.py')
```
  1. Examine the resulting output definitions
```
  ls ./def
  vi ./def/AUTOGEN.net
```
  1. Embed the generated definitions in one of the policies or other network definitions
```
  vi ./def/NETWORK.net
  vi ./policies/sample*.pol
```
  1. Check the Quick Start Instructions for Capirca ACL Generation
    * http://code.google.com/p/capirca/wiki/QuickStart

# Creating Your Own Definitions #

  1. Add your network specifications to the Definate configuration
```
vi ./definate/definate.yaml
```
    * Note: See the section ["Definate Configuration Language"](http://code.google.com/p/capirca/wiki/DefinateConfiguration) to understand how the configuration file is structured.

  1. Generate your network definitions
```
./definate.py
```
  1. Review and check the generated network definitions
```
vi ./def/my-custom.net
```
  1. Use the new definition in a policy or another network definition and regenerate the filters
    * http://code.google.com/p/capirca/wiki/QuickStart

# Help #

Discussion Forum: http://groups.google.com/group/capirca-dev

Group email: capirca-dev@googlegroups.com