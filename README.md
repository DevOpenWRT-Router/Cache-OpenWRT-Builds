### Cache OpenWRT Builds:

#### Example:

name: Cache Acceleration (Secondary compilation of the same model with the same source code is valid within 7 days, and only one source code cache is retained each time)  
uses: DevOpenWRT-Router/Cache-OpenWRT-Builds@main  
if: env.USE\_CACHEWRTBUILD == 'true' && !cancelled()  
with:  
ccache: 'true'  
toolchain: 'true'  
clean: '${{ contains(github.event.action, ''nocache'') }}'  
prefix: '${{ github.workspace }}/openwrt'

## Opetions:

name: 'Cache OpenWRT Builds'  
description: 'Cache builds to speed up openwrt compilation'  
inputs:  
ccache:  
description: 'check if to cache ccache'  
required: false  
default: false  
toolchain:  
description: 'check if to cache toolchain'  
required: false  
default: true  
skip:  
description: 'check if to skip the compilation of toolchain'  
required: false  
default: true  
clean:  
description: 'set to clean cache'  
required: false  
default: false  
prefix:  
description: 'path prefix to openwrt build directory'  
required: false  
defalut: ''  
mixkey:  
description: 'mix a key to identify a cache when you build openwrt for different architecture'  
required: false  
defalut: ''
