# Realme/OPPO MTK6853
                      
## Device specifications

| Device                  | mtk6853                                  |
| ----------------------- | :---------------------------------------------------------|
| SoC                     | Mediatek MT6833 Dimensity 700/810 (7 nm)                             |
| CPU                     | Octa-core (2x2.4 GHz Cortex-A76 & 6x2.0 GHz Cortex-A55)     |
| GPU                     | Mali-G57 MC3                                                 |
| Memory                  | 6/8 GB RAM                                                     |
| Shipped Android version | Android 12                    


## 编译

First checkout minimal twrp with omnirom tree(拉取twrp源码):

```
repo init --depth=1 -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-11 --groups=all,-notdefault,-device,-darwin,-x86,-mips

repo sync

|or|

repo sync --force-sync --no-clone-bundle --no-tags -j$(nproc --all)
```

Finally execute these(开始编译):

```
export ALLOW_MISSING_DEPENDENCIES=true
. build/envsetup.sh
lunch twrp_MTK6853-eng
make -j$(nproc --all) recoveryimage

|or|

export ALLOW_MISSING_DEPENDENCIES=true; source build/envsetup.sh; lunch twrp_mtk6853-eng; mka -j$(nproc --all) recoveryimage


|or|

FOR Building ofox      
cd ~/OrangeFox # (or whichever directory has the synced manifest)
    
  source build/envsetup.sh
    
  export ALLOW_MISSING_DEPENDENCIES=true
  
  export FOX_USE_TWRP_RECOVERY_IMAGE_BUILDER=1
  
  export LC_ALL="C"
  
  unset USE CCACHE

  
|or|

for the 11.0 (or higher) branch
  lunch twrp_MTK6853-eng && mka adbd recoveryimage