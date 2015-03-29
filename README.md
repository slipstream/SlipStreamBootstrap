# SlipStreamBootstrap

Maven configuration used to bootstrap the checkout of all SlipStream repositories.

# Clone Repositories

This script will clone all of the repositories that are required to
build the SlipStream service.  To perform the checkout, clone this
repository and then from that repository use maven to clone the others:
```
$ cd SlipStreamBootstrap
$ mvn generate-sources
```
All of the repositories will appear in the SlipStreamBootstrap 
subdirectory.

The URLs that are used for cloning are either:

  * SSH GitHub URLs (default): Allow both read and write access 
    to the repositories,assuming that you have an SSH key registered 
    with GitHub and that you have been granted write access. 

  * Public HTTPS URLs: Allows read access to the repositories even
    without a GitHub account.

The SSH GitHub URLs are the default.  If do not have a GitHub account
then switch to the public URLs by using the command:
```
$ mvn -P public generate-sources
```
With these URLs, you will _not_ be able to push changes you make in 
the modules back to GitHub.

Selecting Versions
------------------

By default, the clone will checkout the **master** branch for each
repository.  You can select an alternate branch or tag for all of the
repositories by setting the default version property:
```
$ mvn -Dslipstream.version.default=master generate-sources
```
changing "master" to whichever branch or tag you need. 

You can also use an alternate branch for any particular repository
by setting the corresponding version for that repository.  For
example to the version for the SlipStreamClient repository, run
```
$ mvn -Dslipstream.client.version=v2.5-community generate-sources
```
For other repositories, just replace "Client" with the relevant
repository name.

# License and copyright

Copyright (C) 2015 SixSq Sarl (sixsq.com)

The code in the public repositories is licensed under the Apache
license.

Licensed under the Apache License, Version 2.0 (the "License"); you
may not use this file except in compliance with the License.  You may
obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
implied.  See the License for the specific language governing
permissions and limitations under the License.
