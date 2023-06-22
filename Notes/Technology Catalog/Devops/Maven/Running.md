
## Command Line Options

`-D<ARG>` - Define a system property

`-h` - Display help information

`-P <ARG>` - Activate a profile

`-V` - display version info during build

`-v` - just display version info

`-o` - execute maven in offline mode so that it does not attempt to connect to anything remote

#### Files

`-f <FILE>` - use an alternate POM

`-s <FILE>` - use alternate user settings file

`-gs <FILE>` - use alternate global settings file

#### Failures

`-fae` - fail at end of build, as opposed to during

`-fn` - never fail the build

#### Outputs

`-e` - produce error messages

`-X` - produce debug output

`-q` - only show errors

`-B` - run in non-interactive mode

#### Dependencies

`-C` - validate checksums during dependency download

`-c` - warn if checksums don't match

`-U` - force a check for updated releases and snapshots in remote repositories

`-N` - prevent maven from building sub-modules


## Help Plugin

`help:active-profiles` - list all profiles

`help:effective-pom` - display the full calculated POM

`help:effective-settings` - display the calculated settings

#### Describe

`help:describe` - for describing plugin attributes

`-Dplugin=<PLUGIN_NAME>` - will show details about the plugin

`-Dfull` - will show in verbose format

`-Dmojo=<GOAL_NAME>` - will show only documentation on the plugin goal