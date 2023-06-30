# This folder is the base specification for SYADL

### Important things to note:
- the top level section of a document is a dictionary of links bewteen identifiers and objects, Parsers should not return this unless there is no other output specified or explictly told to.
- - instead the output document should be a node tree made of assembled nodes.
- - a node tree is a nested dictionary/ object/ map/ assocaitive array of nodes where all nodes have been assembled into one nested document/ dictionary
- parsers should use native types where possible.
- types are optional and should be possible to infer from context, but mismatching types should error.
- Nodes can be inherted from other nodes
- fields can be referenced by new fields 