## mruby-yaml FORK

### WARNING

This is a fork of mruby-yaml that includes the underlying library in
the repository itself as a way to reduce external dependencies.  You
probably don't want this.  The official repository is
[here](https://github.com/mrbgems/mruby-yaml).

---


[![Ubuntu Status](https://github.com/mrbgems/mruby-yaml/workflows/ubuntu/badge.svg?branch=master)](https://github.com/mrbgems/mruby-yaml/actions?query=workflow%3Aubuntu+branch%3Amaster)

#### YAML gem for [mruby](https://github.com/mruby/mruby)

mruby-yaml wraps [libyaml](https://pyyaml.org/wiki/LibYAML) and therefore complies with the YAML 1.1 standard. File IO is not supported, as this would create a dependency on other mruby gems.

### Defines
| Name                             | Default | Description                    |
| -------------------------------- | ------- | ------------------------------ |
| MRUBY_YAML_NULL                  | true    | enables `null`, `Null`, `NULL` |
| MRUBY_YAML_BOOLEAN_ON            | true    | enables `on`, `On`, `ON`       |
| MRUBY_YAML_BOOLEAN_YES           | true    | enables `yes`, `Yes`, `YES`    |
| MRUBY_YAML_BOOLEAN_SHORTHAND_YES | false   | enables `y`, `Y`               |
| MRUBY_YAML_BOOLEAN_OFF           | true    | enables `off`, `Off`, `OFF`    |
| MRUBY_YAML_BOOLEAN_NO            | true    | enables `no`, `No`, `NO`       |
| MRUBY_YAML_BOOLEAN_SHORTHAND_NO  | false   | enables `n`, `N`               |

If you need to check if a feature is supported at runtime, replace `MRUBY_YAML_` with `SUPPORT_` for the runtime equivalent.

#### EG.
```ruby
if YAML::SUPPORT_NULL
  YAML.load('null') == nil
else  
  YAML.load('null') == 'null'
end
```

### Getting libyaml

If you have a compiled version of `libyaml` available on your system, you can use it by setting the environment variable `MRUBY_YAML_USE_SYSTEM_LIBRARY` to a non-empty value and ensuring your compiler can find the library.

Otherwise, Rake will attempt to compile it from sources obtained from the offical `libyaml` GitHub repository.  This requires that you have `autoconf` installed.


### Documentation

#### `YAML.load(yaml_str)`
Converts a YAML 1.1 string to a Ruby object containing hashes, arrays, and strings. YAML scalars (i.e. strings) are converted to Fixnum or Floats if possible.

#### `YAML.dump(obj)`
Converts a Ruby object to a YAML 1.1 string. Arrays, Hashes, and their subclasses are represented as YAML sequences and mapping nodes. Other objects are converted to strings and represented as scalars.
