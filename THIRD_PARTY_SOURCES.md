# HomeOS v1.0.0 third-party sources

The matching third-party source archive accompanies this Linux amd64 image at
`/usr/share/doc/homeos/HomeOS-third-party-source-linux-amd64.tar`.
It contains no HomeOS application source or user data. Copy it out of a local
image with `docker create` and `docker cp`, or extract it from the image layer.

| Item | Value |
| --- | --- |
| Archive size | 118,394,880 bytes |
| Archive SHA-256 | `62927a24b62d1e445699d602e062a9bf67e86e1b899a1705682914730d477e46` |
| Debian source packages | glibc `2.41-12+deb13u4`, gcc-14 `14.2.0-19`, tzdata `2026f-0+deb13u1` |
| Debian binary packages copied | libc6, libgcc-s1, libstdc++6, tzdata |

The archive has each Debian `.dsc`, original source tarball, Debian patch
archive, and any associated signature, plus `SHA256SUMS`, a binary-to-source
map, and a readme. Verify the archive digest and internal checksums before use.
The matching binary map is in this image at
`/usr/share/doc/homeos/runtime-binary-source-map.tsv`. Its Node.js v24.22.3
binary has SHA-256
`a7ec1b37e6ff9d187e4198c5b6df9a4eb1c74dd31804fb3bac55cc4ceca1ac01`.
Node and bundled component licences are in `/usr/local/LICENSE`; npm, browser,
font, icon, and Debian notices are in `THIRD_PARTY_NOTICES.md` and the four
Debian copyright files under `/usr/share/doc`.

This image contains no shell or `dpkg-query`. Verify it with Node in a
disposable container and validate the source archive on a host. Debian version
and four-package metadata are retained for vulnerability scanning. The source
archive accompanies the binaries in the same image; it does not change the
private status of HomeOS's own source code.
