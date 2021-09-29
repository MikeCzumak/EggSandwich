# EggSandwich
 An egghunter with built-in integrity checks to compensate for shellcode corruption

Please note that this is a proof of concept and not an active project/tool that I am maintaining. I am no longer actively maintaining it. Feel free to leverage the code if you feel it can be useful in your research. 

## Overview

I developed EggSandwich while I was doing some [research in Exploit Development and Egghunting](https://www.securitysift.com/windows-exploit-development-part-5-locating-shellcode-egghunting/) as a means to overcome a problem I was having with corrupted shellcode. Shellcode can get placed in memory in multiple locations and often some of those locations become fragmented or corrupted due to buffer size limitations, encoding, etc. This will interfere with traditional egguhunters  should the corrupted shellcode appear first in memory.

This EggSandwich is designed to “sandwich” shellcode between two "egg" tags and length/offset data, enabling the Egghunter to verify the presence of both tags before executing the shellcode (thereby avoiding shellcode fragments of invalid lengths). If the shellcode failed this integrity check, the Egghunter moves on to the next copy in memory (and so on) until an intact version was located (or it fails to find any).

A more in-depth write-up can be found here: https://mikeczumak.com/blog/eggsandwich-egghunter-integrity/


## Usage
I provide both some example C code and Perl script generator for testing. For a more detailed walk-through, please see the link above.  

## License 

LICENSE/WARRANTY: This code is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or(at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
