+++
title = "init"
showDate = false
showReadingTime = false
showWordCount = false
showPagination = false
+++

An _init process_ is the first process your computer loads when powering on. It is the parent of all processes - it sets them up and manages them. It does things like running background processes, configures hardware et cetera, and makes sure that the computer has come to the state where it's ready for you to use. It stays running the entire time that your computer is on, managing processes as I have stated before and handling errors if they crash. Arch Linux uses systemd, which is an entire suite of software, not just an init system, doing things such as logging and networking. It's easy to manage as everything is in one place, and provides fast boot-up times.