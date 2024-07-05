# manifest locations for xiaomi rosy

## Run following commands

```
# Remove existing local manifests.
rm -rf .repo/local_manifests;
# Initialise repo template 
repo init --depth=1 -u https://github.com/ProjectBlaze/manifest -b 14-QPR3;
# Add device specific trees
git clone https://github.com/05Alston/local_manifests --depth 1 -b rosy-blaze .repo/local_manifests;
# Sync repo
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
# Update maintainer info (optional)
sed -i 's/^BLAZE_MAINTAINER\s*?=\s*\(.*\)/BLAZE_MAINTAINER ?= Alston #\1/ #\2g' vendor/blaze/config/version.mk;
# Build
source build/envsetup.sh;
lunch blaze_rosy-eng;
mka bacon;
```
