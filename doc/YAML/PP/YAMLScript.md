YAML::PP::YAMLScript
====================

YAML Load YAMLScript Code as Data

# Synopsis

File `data.yaml`:
```
--- !yamlscript
array =:
  vec: (1 .. 3)
hash-map: ."foo" array
```

Run this Perl:
```
use YAML::PP::YAMLScript;
my $ypp = YAML::PP::YAMLScript->new;
my $data = $ypp->load_file('data.yaml');
print $ypp->dump_string($data);
```

Output:
```
---
foo:
- 1
- 2
- 3
```

# Description

This module lets you use YAML files that are completely programmatic.
The YAML files are actually YAMLScript programs that run to produce the desired
data.

YAML::PP::YAMLScript is a subclass of YAML::PP that lets you load YAML files
written in YAMLScript with the command:

    my $hash = YAML::PP::YAMLScript->new->load_file('foo.yaml');

The file should start with the tag `!yamlscript`.

When loaded, the YAMLScript program in the file will run and should produce a
YAMLScript HashMap value.

The resulting value will be returned as a Perl hashref.


# See Also

* [YAMLScript](https://metacpan.org/pod/YAMLScript)
* [Lingy](https://metacpan.org/pod/Lingy)
* [YAML::PP](https://metacpan.org/pod/YAML::PP)


# Authors

* Ingy döt Net <ingy@ingy.net>


# Copyright and License

Copyright 2023 by Ingy döt Net

This is free software, licensed under:

The MIT (X11) License
