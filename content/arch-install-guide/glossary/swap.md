+++
title = "swap"
showDate = false
showReadingTime = false
showWordCount = false
+++

*Linux swap* is either a file or [_partition_](/arch-install-guide/glosssary/partition) on your drive. It is used as a section of your disk that can store data in RAM even when the computer is off (for hibernation, which is important for laptop users) or be used in case RAM runs out. Even if you are not on a laptop and have a sufficient amount of RAM, some programs rely solely on swap, so make swap regardless. This guide will not create a swapfile, but rather, a swap partition to keep the swap data separate from everything else. 