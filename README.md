# ld64.mold

The [mold](https://github.com/rui314/mold) project is working on full
MachO support. I assume eventually mold releases will include binaries,
but in the meantime this repo publishes universal mold releases from
commits for easier testing.

## Build instructions

```
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_OSX_ARCHITECTURES='x86_64;arm64' -DCMAKE_OSX_DEPLOYMENT_TARGET=11.0 ..
cmake --build . -j $(nproc)
strip -rSx mold
mv mold ld64.mold
COPYFILE_DISABLE=1 tar czvf ld64.tar.gz ld64.mold
COPYFILE_DISABLE=1 tar cJvf ld64.tar.xz ld64.mold
sha256sum ld64.mold ld64.tar.gz ld64.tar.xz
```
