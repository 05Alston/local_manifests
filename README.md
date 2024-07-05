# manifest locations for xiaomi rosy

## Run following commands

```
# Remove existing local manifests.
rm -rf .repo/local_manifests;
# Initialise repo template 
repo init -u https://github.com/VoltageOS/manifest.git --depth 1 -b 14 --git-lfs;
# Add device specific trees
git clone https://github.com/05Alston/local_manifests --depth 1 -b rosy-voltage-U .repo/local_manifests;
# Sync repo
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
# Generate signature keys
cd vendor/voltage-priv/keys;
./gen_keys;
cd ../../..;
# Build
source build/envsetup.sh;
brunch voltage_rosy-ap1a-eng;
```
