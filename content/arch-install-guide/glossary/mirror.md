+++
title = "mirror"
showDate = false
showReadingTime = false
showWordCount = false
+++

A _mirror_ is essentially a duplicate copy of some data on a master server (a server that the data was originally uploaded on). Mirrors are kept for two reasons, to have a copy in case something goes wrong on the master server (or, "redundancy") and speed. Mirrors are set up on [_Linux_](/arch-install-guide/glossary/kernel) [_distros_](/arch-install-guide/glossary/distro) to make download speeds faster, because, put simply, the closer you are to a server, the less time it takes to upload and download data. This is why the mirrorlist exists, as really slow download speeds can time out, meaning that your computer will give up after some period of waiting.