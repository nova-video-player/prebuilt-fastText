# prebuilt-fastText

Prebuilt fastText static libraries and the compact language identification
model for Nova Video Player. Built by `native/fastText-android-builder`.

## Contents

- `include/fasttext/`: upstream public C++ headers.
- `lib/<ABI>/libfasttext.a`: position-independent static libraries for
  `armeabi-v7a`, `arm64-v8a`, `x86`, and `x86_64`, with debug information stripped.
- `share/fastText/lid.176.ftz`: the unmodified 938,013-byte model, shared by all ABIs.
- `LICENSE`, `LICENSE.fastText`, `LICENSE.model`, and `NOTICE`: licenses and attribution.

These are build dependencies. Subtitle detection and APK model packaging are
not enabled by this bundle alone.

## Build provenance

The initial bundle was built on 2026-11-15 with Android NDK `30.0.14904198`,
CMake `4.1.2`, API level 23, the static C++ runtime, and Release optimization.

- Upstream: https://github.com/facebookresearch/fastText
- Version: `v0.9.2`, commit `5b5943c118b0ec5fb9cd8d20587de2b2d3966dfe`.
- Source archive SHA-256:
  `7ea4edcdb64bfc6faaaec193ef181bdc108ee62bb6a04e48b2e80b639a99e27e`.
- Model: https://dl.fbaipublicfiles.com/fasttext/supervised-models/lid.176.ftz
- Model SHA-256:
  `8f3472cfe8738a7b6099e8e999c3cbfae0dcd15696aac7d7738a8039db603e83`.

The prebuilt update commit records the builder commit used. Keep headers and
libraries from the same build together across all four ABIs. Preserve the
model checksum, upstream version, toolchain details, and license files when
updating the bundle.

From a configured Nova workspace, regenerate with:

```sh
make native_build_native/fastText-android-builder
```

The builder verifies source/model downloads and incrementally rebuilds the
libraries. See its README for host inference tests and Android build options.

## Licensing

Nova-authored repository documentation and support material are licensed under
the [Apache License 2.0](LICENSE), following the other Nova prebuilt repositories.

The bundled fastText libraries and headers retain their upstream
[MIT license](LICENSE.fastText) and Facebook copyright notices. The unmodified
language model is separately licensed under
[Creative Commons Attribution-ShareAlike 3.0 Unported](LICENSE.model).
[NOTICE](NOTICE) records its attribution, source, and requested references.
The Apache license does not replace either upstream license.

Official model information and license:
https://fasttext.cc/docs/en/language-identification.html.
