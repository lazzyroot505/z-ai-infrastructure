# 📦 System Environment & Software Inventory

> **Debian 13 (Trixie) | Kata Container | Alibaba Cloud Function Compute**

---

## 🗂️ Table of Contents

<details open>
<summary><strong>Click to expand/collapse sections</strong></summary>

1. [🖥️ Runtime Environment](#-runtime-environment)
2. [🔧 Build & Development Tools](#-build--development-tools)
3. [🌐 Web & Network Utilities](#-web--network-utilities)
4. [🗄️ Database & Storage](#-database--storage)
5. [🎨 Graphics & Media Processing](#-graphics--media-processing)
6. [📄 Document & PDF Tools](#-document--pdf-tools)
7. [🤖 AI & Machine Learning](#-ai--machine-learning)
8. [🔐 Security & Cryptography](#-security--cryptography)
9. [📦 Archive & Compression](#-archive--compression)
10. [🧪 Scientific & Geospatial](#-scientific--geospatial)
11. [🎮 Multimedia & Audio](#-multimedia--audio)
12. [🖋️ Office Suite](#-office-suite)
13. [⚙️ System Libraries](#-system-libraries)
14. [📊 Package Statistics](#-package-statistics)
15. [📑 Full Package List](#-full-package-list)

</details>

---

## 🖥️ Runtime Environment

| Runtime | Version | Package |
|---------|---------|---------|
| Node.js | v24.13.1 | nodejs (24.13.1-1nodesource1) |
| Bun | v1.3.9 | bun (custom install) |
| Python (UV) | 3.12.12 | python3.13 (3.13.5-2) |
| Python (System) | 3.13.5 | python3 (3.13.5-1) |
| OpenJDK | 21.0.10+7 | openjdk-21-jre-headless |
| Perl | 5.40.1 | perl (5.40.1-6) |

---

## 🔧 Build & Development Tools

| Package | Version | Purpose |
|---------|---------|---------|
| build-essential | 12.12 | Meta-package for compilation tools |
| gcc, g++ | 14.2.0-19 | GNU C/C++ compilers |
| cpp | 14.2.0-19 | C preprocessor |
| binutils | 2.44-3 | Assembler, linker, binary utilities |
| make | 4.4.1-2 | Build automation |
| autoconf | 2.72-3.1 | Automatic configure script builder |
| automake | 1:1.17-4 | GNU Standards-compliant Makefiles |
| autotools-dev | 20240727.1 | Config.{guess,sub} update infrastructure |
| m4 | 1.4.19-8 | Macro processing language |
| pkgconf | 1.8.1-4 | Manage compile and link flags |
| dpkg-dev | 1.22.21 | Debian package development tools |
| linux-libc-dev | 6.12.69-1 | Linux support headers for userspace |
| libgcc-14-dev | 14.2.0-19 | GCC support library (development) |
| libstdc++-14-dev | 14.2.0-19 | GNU Standard C++ Library v3 (development) |
| libc6-dev | 2.41-12+deb13u1 | GNU C Library: Development Libraries |
| libffi-dev | 3.4.8-2 | Foreign Function Interface library (development) |
| libexpat1-dev | 2.7.1-2 | XML parsing C library (development) |
| libtool | 2.5.4-4 | Generic library support script |
| git | 2.47.3-0+deb13u1 | Distributed version control |
| git-man | 2.47.3-0+deb13u1 | Git manual pages |
| vim | 9.1.1230-2 | Vi IMproved editor |
| nano | 8.4-1 | Small text editor |
| ripgrep | 14.1.1-1+b4 | Recursive grep alternative |
| tree | 2.2.1-1 | Directory tree visualization |
| jq | 1.7.1-6+deb13u1 | JSON processor |
| patch | 2.8-2 | Apply diff files |

---

## 🌐 Web & Network Utilities

| Package | Version | Purpose |
|---------|---------|---------|
| curl | 8.14.1-2+deb13u2 | URL data transfer tool |
| wget | 1.25.0-2 | Non-interactive downloader |
| rsync | 3.4.1+ds1-5+deb13u1 | Fast file synchronization |
| iproute2 | 6.15.0-1 | Networking and traffic control |
| net-tools | 2.10-1.3 | Classic networking utilities |
| iputils-ping | 20240905-3 | ICMP echo utility |
| traceroute | 2.1.6-1 | Network path discovery |
| lsof | 4.99.4+dfsg-2 | List open files/sockets |
| bind9-dnsutils | 9.20.18-1~deb13u1 | DNS lookup (dig, nslookup) |
| bind9-host | 9.20.18-1~deb13u1 | DNS hostname lookup |
| bind9-libs | 9.20.18-1~deb13u1 | BIND 9 shared libraries |
| libcurl4-gnutls-dev | 8.14.1-2+deb13u2 | libcurl development files |
| libcurl3t64-gnutls | 8.14.1-2+deb13u2 | libcurl GnuTLS flavour |
| libcurl4t64 | 8.14.1-2+deb13u2 | libcurl OpenSSL flavour |
| libnghttp2-14 | 1.64.0-1.1 | HTTP/2 protocol library |
| libnghttp3-9 | 1.8.0-1 | HTTP/3 library with QUIC |
| libngtcp2-16 | 1.11.0-1 | QUIC protocol implementation |
| libssh2-1t64 | 1.11.1-1 | SSH2 client library |
| libssh-4 | 0.11.2-1+deb13u1 | Tiny C SSH library |
| libldap2 | 2.6.10+dfsg-1 | OpenLDAP libraries |
| libkrb5-3 | 1.21.3-5 | MIT Kerberos runtime |
| libgssapi-krb5-2 | 1.21.3-5 | Kerberos GSS-API Mechanism |

---

## 🗄️ Database & Storage

| Package | Version | Purpose |
|---------|---------|---------|
| libsqlite3-0 | 3.46.1-7 | SQLite 3 shared library |
| libsqlite3-dev | 3.46.1-7 | SQLite 3 development files |
| libpq5 | 17.8-0+deb13u1 | PostgreSQL C client library |
| libpq-dev | 17.8-0+deb13u1 | PostgreSQL development headers |
| libmariadb3 | 11.8.3-0+deb13u1 | MariaDB client library |
| libmariadb-dev | 11.8.3-0+deb13u1 | MariaDB development files |
| default-libmysqlclient-dev | 1.1.1 | MySQL development metapackage |
| mysql-common | 5.8+1.1.1 | MySQL common files |
| mariadb-common | 11.8.3-0+deb13u1 | MariaDB common config |
| unixodbc | 2.3.12-2 | ODBC Driver Manager |
| libodbc2 | 2.3.12-2 | ODBC library |
| libodbccr2 | 2.3.12-2 | ODBC Cursor library |
| libodbcinst2 | 2.3.12-2 | ODBC configuration support |
| unixodbc-dev | 2.3.12-2 | ODBC development files |
| liblmdb0 | 0.9.31-1+b2 | Lightning Memory-Mapped DB |
| libgdbm6t64 | 1.24-2 | GNU dbm database routines |
| libgdbm-compat4t64 | 1.24-2 | GNU dbm legacy support |
| libdb5.3t64 | 5.3.28+dfsg2-9 | Berkeley DB libraries |

---

## 🎨 Graphics & Media Processing

| Package | Version | Purpose |
|---------|---------|---------|
| ffmpeg | 7.1.3-0+deb13u1 | Multimedia transcoding/streaming |
| libavcodec61 | 7.1.3-0+deb13u1 | FFmpeg codec library |
| libavformat61 | 7.1.3-0+deb13u1 | FFmpeg container library |
| libavutil59 | 7.1.3-0+deb13u1 | FFmpeg utility functions |
| libswscale8 | 7.1.3-0+deb13u1 | FFmpeg image scaling |
| libswresample5 | 7.1.3-0+deb13u1 | FFmpeg audio resampling |
| libavfilter10 | 7.1.3-0+deb13u1 | FFmpeg media filters |
| libavdevice61 | 7.1.3-0+deb13u1 | FFmpeg I/O devices |
| libpostproc58 | 7.1.3-0+deb13u1 | FFmpeg post-processing |
| imagemagick-7-common | 7.1.1.43+dfsg1-1+deb13u5 | ImageMagick infrastructure |
| libmagickcore-7.q16-10 | 7.1.1.43+dfsg1-1+deb13u5 | ImageMagick core library |
| libmagickwand-7.q16-10 | 7.1.1.43+dfsg1-1+deb13u5 | ImageMagick wand library |
| libmagick++-7.q16-5 | 7.1.1.43+dfsg1-1+deb13u5 | ImageMagick C++ interface |
| libcairo2 | 1.18.4-1+b1 | Cairo 2D graphics library |
| libcairo2-dev | 1.18.4-1+b1 | Cairo development files |
| libgd3 | 2.3.3-13 | GD Graphics Library |
| librsvg2-2 | 2.60.0+dfsg-1 | SVG renderer library |
| librsvg2-dev | 2.60.0+dfsg-1 | SVG development files |
| libwebp7 | 1.5.0-0.1 | WebP image format |
| libwebp-dev | 1.5.0-0.1 | WebP development files |
| libavif16 | 1.2.1-1.2 | AVIF image format |
| libheif1 | 1.19.8-1 | HEIF/AVIF decoder/encoder |
| libopenjp2-7 | 2.5.3-2.1~deb13u1 | JPEG 2000 library |
| libtiff6 | 4.7.0-3+deb13u1 | TIFF library |
| libpng16-16t64 | 1.6.48-1+deb13u1 | PNG library |
| libjpeg62-turbo | 2.1.5-4 | JPEG library |
| libgif7 | 5.2.2-1+b1 | GIF library |
| tesseract-ocr | 5.5.0-1+b1 | OCR tool |
| libtesseract5 | 5.5.0-1+b1 | Tesseract library |
| libleptonica6 | 1.84.1-4 | Image processing library |

---

## 📄 Document & PDF Tools

| Package | Version | Purpose |
|---------|---------|---------|
| poppler-utils | 25.03.0-5+deb13u2 | PDF utilities |
| libpoppler147 | 25.03.0-5+deb13u2 | PDF rendering library |
| libpoppler-dev | 25.03.0-5+deb13u2 | PDF development files |
| ghostscript | 10.05.1~dfsg-1+deb13u1 | PostScript/PDF interpreter |
| libgs10 | 10.05.1~dfsg-1+deb13u1 | Ghostscript library |
| qpdf | 12.2.0-1 | PDF transformation tools |
| libqpdf30 | 12.2.0-1 | QPDF runtime library |
| pandoc | 3.1.11.1+ds-2 | Markup converter |
| pandoc-data | 3.1.11.1-3 | Pandoc conversion data |
| antiword | 0.37-17 | MS Word to text/PS/PDF |
| unrtf | 0.21.10-clean-1 | RTF converter |
| libwpg-0.3-3 | 0.3.4-3+b2 | WordPerfect graphics import |
| libwpd-0.10-10 | 0.10.3-2+b2 | WordPerfect document library |
| libwps-0.4-4 | 0.4.14-2+b2 | Works text filter library |

---

## 🤖 AI & Machine Learning

| Package | Version | Purpose |
|---------|---------|---------|
| python3-numpy | 2.2.4+ds-1 | Python numerical computations |
| python3-numpy-dev | 2.2.4+ds-1 | NumPy development headers |
| libblas3 | 3.12.1-6 | Basic Linear Algebra Subroutines |
| libblas-dev | 3.12.1-6 | BLAS static library |
| liblapack3 | 3.12.1-6 | Linear algebra routines |
| liblapack-dev | 3.12.1-6 | LAPACK static library |
| libarmadillo14 | 14.2.3+dfsg-1+b1 | C++ linear algebra library |
| libarmadillo-dev | 14.2.3+dfsg-1+b1 | Armadillo headers |
| libfftw3-double3 | 3.3.10-2+b1 | FFT double precision |
| libfftw3-single3 | 3.3.10-2+b1 | FFT single precision |
| libfftw3-long3 | 3.3.10-2+b1 | FFT long precision |
| libfftw3-quad3 | 3.3.10-2+b1 | FFT quad precision |
| libfftw3-dev | 3.3.10-2+b1 | FFT development files |
| espeak | 1.48.15+dfsg-3+b2 | Speech synthesizer |
| espeak-ng | 1.52.0+dfsg-5 | Speech synthesizer (NG) |
| libespeak1 | 1.48.15+dfsg-3+b2 | eSpeak shared library |
| libespeak-ng1 | 1.52.0+dfsg-5 | eSpeak-NG shared library |
| libflite1 | 2.2-7 | Small speech synthesis engine |
| libpocketsphinx3 | 0.8+5prealpha+1-15+b4 | Speech recognition |
| libsphinxbase3t64 | 0.8+5prealpha+1-21+b1 | Speech recognition base |
| libzbar0t64 | 0.23.93-8 | QR/barcode scanner |
| libzbar-dev | 0.23.93-8 | ZBar development files |
| libzxing3 | 2.3.0-4 | ZXing QR library |
| libarpack2t64 | 3.9.1-6 | Large scale eigenvalue problems |
| libsuperlu7 | 7.0.1+dfsg1-2 | Sparse linear equations solver |
| libsuitesparseconfig7 | 7.10.1+dfsg-1 | SuiteSparse configuration |

---

## 🔐 Security & Cryptography

| Package | Version | Purpose |
|---------|---------|---------|
| openssl | 3.5.4-1~deb13u2 | SSL/TLS toolkit |
| libssl3t64 | 3.5.4-1~deb13u2 | OpenSSL shared libraries |
| libssl-dev | 3.5.4-1~deb13u2 | OpenSSL development files |
| gnupg | 2.4.7-21+deb13u1 | GNU Privacy Guard |
| gpg | 2.4.7-21+deb13u1+b1 | GPG minimalist operations |
| gpg-agent | 2.4.7-21+deb13u1+b1 | GPG cryptographic agent |
| gpgconf | 2.4.7-21+deb13u1+b1 | GPG configuration utilities |
| gpgsm | 2.4.7-21+deb13u1+b1 | GPG S/MIME version |
| dirmngr | 2.4.7-21+deb13u1+b1 | Certificate management |
| libgcrypt20 | 1.11.0-7 | Crypto library |
| libgpg-error0 | 1.51-4 | GnuPG error library |
| libgpgme11t64 | 1.24.2-3 | GPGME library |
| libassuan9 | 3.0.2-2 | GnuPG IPC library |
| libksba8 | 1.6.7-2+b1 | X.509/CMS support library |
| libnpth0t64 | 1.8-3 | GNU Pth replacement |
| pinentry-curses | 1.3.1-2 | PIN entry dialog |
| libssh2-1-dev | 1.11.1-1 | SSH2 development headers |
| libseccomp2 | 2.6.0-2 | Linux seccomp filter |
| libselinux1 | 3.8.1-1 | SELinux runtime libraries |
| libselinux1-dev | 3.8.1-1 | SELinux development headers |
| libcap2 | 2.75-10+b3 | POSIX capabilities library |
| libcap2-bin | 2.75-10+b3 | POSIX capabilities utilities |
| libaudit1 | 4.0.2-2+b2 | Security auditing library |
| libpam0g | 1.7.0-5 | PAM library |
| libpam-modules | 1.7.0-5 | PAM modules |
| libpam-runtime | 1.7.0-5 | PAM runtime support |
| libpam-systemd | 257.9-1~deb13u1 | PAM systemd module |
| sudo | 1.9.16p2-3 | Superuser privileges |
| passwd | 4.17.4-2 | Password administration |
| login | 4.16.0-2+really2.41-5 | System login tools |

---

## 📦 Archive & Compression

| Package | Version | Purpose |
|---------|---------|---------|
| gzip | 1.13-1 | GNU compression |
| bzip2 | 1.0.8-6 | Block-sorting compressor |
| xz-utils | 5.8.1-1 | XZ compression |
| zip | 3.0-15 | ZIP archiver |
| unzip | 6.0-29 | ZIP extractor |
| unrar-free | 0.3.1-1 | RAR extractor |
| tar | 1.35+dfsg-3.1 | GNU tar archiving |
| libarchive13t64 | 3.7.4-4 | Multi-format archive library |
| liblzma5 | 5.8.1-1 | XZ library |
| liblzma-dev | 5.8.1-1 | XZ development files |
| libbz2-1.0 | 1.0.8-6 | Bzip2 runtime |
| libbz2-dev | 1.0.8-6 | Bzip2 development |
| libzstd1 | 1.5.7+dfsg-1 | Zstandard compression |
| libzstd-dev | 1.5.7+dfsg-1 | Zstandard development |
| liblz4-1 | 1.10.0-4 | LZ4 compression |
| liblz4-dev | 1.10.0-4 | LZ4 development |
| libsnappy1v5 | 1.2.2-1 | Snappy compression |
| zlib1g | 1.3.dfsg+really1.3.1-1+b1 | Compression runtime |
| zlib1g-dev | 1.3.dfsg+really1.3.1-1+b1 | Compression development |
| libminizip1t64 | 1.3.dfsg+really1.3.1-1+b1 | Minizip library |
| libminizip-dev | 1.3.dfsg+really1.3.1-1+b1 | Minizip development |
| liblzo2-2 | 2.10-3+b1 | LZO compression |
| libdeflate0 | 1.23-2 | DEFLATE compression |
| libdeflate-dev | 1.23-2 | DEFLATE development |

---

## 🧪 Scientific & Geospatial

| Package | Version | Purpose |
|---------|---------|---------|
| gdal-bin | 3.10.3+dfsg-1 | Geospatial utilities |
| libgdal36 | 3.10.3+dfsg-1 | GDAL library |
| libgdal-dev | 3.10.3+dfsg-1 | GDAL development |
| python3-gdal | 3.10.3+dfsg-1 | Python GDAL bindings |
| gdal-data | 3.10.3+dfsg-1 | GDAL data files |
| gdal-plugins | 3.10.3+dfsg-1 | GDAL plugins |
| libgeos3.13.1 | 3.13.1-1 | Geometry engine (C++) |
| libgeos-c1t64 | 3.13.1-1 | Geometry engine (C) |
| libgeos-dev | 3.13.1-1 | GEOS development |
| libproj25 | 9.6.0-1 | Cartographic projection |
| libproj-dev | 9.6.0-1 | PROJ development |
| proj-data | 9.6.0-1 | PROJ datum package |
| libnetcdf22 | 4.9.3-1 | Scientific data access |
| libnetcdf-dev | 4.9.3-1 | NetCDF development |
| libhdf5-310 | 1.14.5+repack-3 | HDF5 runtime |
| libhdf5-dev | 1.14.5+repack-3 | HDF5 development |
| libhdf5-cpp-310 | 1.14.5+repack-3 | HDF5 C++ runtime |
| libhdf5-fortran-310 | 1.14.5+repack-3 | HDF5 Fortran runtime |
| libhdf5-hl-310 | 1.14.5+repack-3 | HDF5 High Level |
| hdf5-helpers | 1.14.5+repack-3 | HDF5 helper tools |
| libcfitsio10t64 | 4.6.2-2 | FITS data I/O |
| libcfitsio-dev | 4.6.2-2 | FITS development |
| libgeotiff5 | 1.7.4-1 | GeoTIFF runtime |
| libgeotiff-dev | 1.7.4-1 | GeoTIFF development |
| libspatialite8t64 | 5.1.0-3+b2 | SQLite geospatial |
| libspatialite-dev | 5.1.0-3+b2 | SpatiaLite development |
| libqhull8.0 | 2020.2-6+b2 | Convex hull library |
| libqhull-dev | 2020.2-6+b2 | Qhull development |
| libkmlbase1t64 | 1.3.0-12+b2 | KML base library |
| libkml-dev | 1.3.0-12+b2 | KML development |
| libogdi4.1 | 4.1.1+ds-5 | Open Geographic Datastore |
| libfyba0t64 | 4.1.1-11+b1 | Norwegian geodata SOSI |

---

## 🎮 Multimedia & Audio

| Package | Version | Purpose |
|---------|---------|---------|
| libsdl2-2.0-0 | 2.32.4+dfsg-1 | Simple DirectMedia Layer |
| libpulse0 | 17.0+dfsg1-2+b1 | PulseAudio client |
| libopenal1 | 1.24.2-1 | OpenAL audio API |
| libopenal-data | 1.24.2-1 | OpenAL data files |
| libportaudio2 | 19.6.0-1.2+b3 | Portable audio I/O |
| libsndfile1 | 1.2.2-2+b1 | Audio file read/write |
| libsndfile1-dev | 1.2.2-2+b1 | libsndfile development |
| libmpg123-0t64 | 1.32.10-1 | MPEG audio decoder |
| libflac14 | 1.5.0+ds-2 | FLAC audio codec |
| libflac-dev | 1.5.0+ds-2 | FLAC development |
| libopus0 | 1.5.2-2 | Opus codec |
| libopus-dev | 1.5.2-2 | Opus development |
| libvorbis0a | 1.3.7-3 | Vorbis decoder |
| libvorbisenc2 | 1.3.7-3 | Vorbis encoder |
| libvorbisfile3 | 1.3.7-3 | Vorbis high-level API |
| libvorbis-dev | 1.3.7-3 | Vorbis development |
| libogg0 | 1.3.5-3+b2 | Ogg bitstream |
| libogg-dev | 1.3.5-3+b2 | Ogg development |
| libspeex1 | 1.2.1-3 | Speex codec |
| libgsm1 | 1.0.22-1+b2 | GSM speech compressor |
| libjack-jackd2-0 | 1.9.22~dfsg-4 | JACK Audio Kit |
| libasound2t64 | 1.2.14-1 | ALSA shared library |
| librubberband2 | 3.3.0+dfsg-2+b3 | Audio time-stretching |
| libsamplerate0 | 0.2.2-4+b2 | Sample rate conversion |
| libsoxr0 | 0.1.3-4+b2 | Sample-rate conversion |
| libmysofa1 | 1.3.3+dfsg-1 | HRTF SOFA format reader |
| libvidstab1.1 | 1.1.0-2+b2 | Video stabilization |
| libplacebo349 | 7.349.0-3 | GPU video rendering |
| libvpl2 | 2.14.0-1+b1 | Intel Video Processing |
| libva2 | 2.22.0-3 | Video Acceleration API |
| libvdpau1 | 1.5-3+b1 | Video Decode API |

---

## 🖋️ Office Suite

| Package | Version | Purpose |
|---------|---------|---------|
| libreoffice | 25.2.3-2+deb13u3 | Office suite (metapackage) |
| libreoffice-common | 25.2.3-2+deb13u3 | Office arch-independent files |
| libreoffice-core | 25.2.3-2+deb13u3 | Office arch-dependent files |
| libreoffice-base | 25.2.3-2+deb13u3 | Database component |
| libreoffice-base-core | 25.2.3-2+deb13u3 | Database shared library |
| libreoffice-base-drivers | 25.2.3-2+deb13u3 | Database drivers |
| libreoffice-calc | 25.2.3-2+deb13u3 | Spreadsheet |
| libreoffice-writer | 25.2.3-2+deb13u3 | Word processor |
| libreoffice-impress | 25.2.3-2+deb13u3 | Presentation |
| libreoffice-draw | 25.2.3-2+deb13u3 | Drawing tools |
| libreoffice-math | 25.2.3-2+deb13u3 | Equation editor |
| libreoffice-style-colibre | 25.2.3-2+deb13u3 | Colibre icon style |
| libreoffice-uiconfig-common | 25.2.3-2+deb13u3 | UI config (common) |
| libreoffice-uiconfig-writer | 25.2.3-2+deb13u3 | UI config (Writer) |
| libreoffice-uiconfig-calc | 25.2.3-2+deb13u3 | UI config (Calc) |
| libreoffice-uiconfig-impress | 25.2.3-2+deb13u3 | UI config (Impress) |
| libreoffice-uiconfig-draw | 25.2.3-2+deb13u3 | UI config (Draw) |
| libreoffice-uiconfig-math | 25.2.3-2+deb13u3 | UI config (Math) |
| libreoffice-uiconfig-base | 25.2.3-2+deb13u3 | UI config (Base) |
| libreoffice-report-builder-bin | 25.2.3-2+deb13u3 | Report builder |
| fonts-opensymbol | 102.12+LibO25.2.3-2+deb13u3 | OpenSymbol fonts |
| python3-uno | 25.2.3-2+deb13u3 | Python-UNO bridge |
| libuno-sal3t64 | 25.2.3-2+deb13u3 | UNO SAL library |
| libuno-cppu3t64 | 25.2.3-2+deb13u3 | UNO CPPU library |
| ure | 25.2.3-2+deb13u3 | UNO runtime environment |
| uno-libs-private | 25.2.3-2+deb13u3 | UNO private libraries |
| libmythes-1.2-0 | 1.2.5-1+b2 | Thesaurus library |
| libhyphen0 | 2.8.8-7+b2 | Hyphenation library |
| libhunspell-1.7-0 | 1.7.2+really1.7.2-10+b4 | Spell checker |
| libnumbertext-1.0-0 | 1.0.11-4+b2 | Number to text conversion |
| liblangtag1 | 0.6.7-1+b2 | Language tag library |
| libexttextcat-2.0-0 | 3.4.7-1+b1 | Language detection |
| liblucene2.3.4 | 2.3.3.4+dfsg-1.2+b1 | Search engine library |
| libclucene-core1t64 | 2.3.3.4+dfsg-1.2+b1 | Lucene core runtime |
| libcmis-0.6-6t64 | 0.6.2-2.1+b1 | CMIS protocol client |
| libodfgen-0.1-1 | 0.1.8-2+b2 | ODF document generator |
| librevenge-0.0-0 | 0.0.5-3+b2 | Document filter base library |
| libstaroffice-0.0-0 | 0.0.7-1+b2 | StarOffice import filter |
| libmwaw-0.3-3 | 0.3.22-1+b2 | Mac text document import |
| libwpg-0.3-3 | 0.3.4-3+b2 | WordPerfect graphics |
| libwps-0.4-4 | 0.4.14-2+b2 | Works text filter |
| libqxp-0.0-0 | 0.0.2-1+b4 | QuarkXPress reader |
| libzmf-0.0-0 | 0.0.2-1+b9 | Zoner Draw reader |
| libvisio-0.1-1 | 0.1.7-1+b5 | Visio file parser |
| libmspub-0.1-1 | 0.1.4-3+b5 | MS Publisher parser |
| libcdr-0.1-1 | 0.1.7-1+b3 | Corel DRAW parser |
| libe-book-0.1-1 | 0.1.3-2+b4 | E-book format reader |
| libepubgen-0.1-1 | 0.1.1-1+b2 | EPUB generator |
| libfreehand-0.1-1 | 0.1.2-3 | FreeHand parser |
| libpagemaker-0.0-0 | 0.0.4-1+b2 | PageMaker parser |

---

## ⚙️ System Libraries

| Package | Version | Purpose |
|---------|---------|---------|
| libc6 | 2.41-12+deb13u1 | GNU C Library |
| libc6-dev | 2.41-12+deb13u1 | GNU C Library (development) |
| libc-bin | 2.41-12+deb13u1 | GNU C Library (binaries) |
| libstdc++6 | 14.2.0-19 | GNU Standard C++ Library |
| libgcc-s1 | 14.2.0-19 | GCC support library |
| libglib2.0-0t64 | 2.84.4-3~deb13u2 | GLib C routines |
| libglib2.0-dev | 2.84.4-3~deb13u2 | GLib development |
| libglib2.0-data | 2.84.4-3~deb13u2 | GLib common files |
| libxml2 | 2.12.7+dfsg+really2.9.14-2.1+deb13u2 | GNOME XML library |
| libxml2-dev | 2.12.7+dfsg+really2.9.14-2.1+deb13u2 | XML development |
| libxslt1.1 | 1.1.35-1.2+deb13u2 | XSLT processing |
| libxslt1-dev | 1.1.35-1.2+deb13u2 | XSLT development |
| libsystemd0 | 257.9-1~deb13u1 | Systemd utility library |
| systemd | 257.9-1~deb13u1 | System and service manager |
| systemd-sysv | 257.9-1~deb13u1 | Systemd SysV compatibility |
| libudev1 | 257.9-1~deb13u1 | libudev shared library |
| dbus | 1.16.2-2 | D-Bus messaging system |
| dbus-bin | 1.16.2-2 | D-Bus utilities |
| dbus-daemon | 1.16.2-2 | D-Bus reference daemon |
| libdbus-1-3 | 1.16.2-2 | D-Bus library |
| libgnutls30t64 | 3.8.9-3+deb13u1 | GNU TLS library |
| libgnutls28-dev | 3.8.9-3+deb13u1 | GNU TLS development |
| libhogweed6t64 | 3.10.1-1 | Cryptographic library (public-key) |
| libnettle8t64 | 3.10.1-1 | Cryptographic library (symmetric) |
| nettle-dev | 3.10.1-1 | Nettle development |
| libtasn1-6 | 4.20.0-2 | ASN.1 structures runtime |
| libp11-kit0 | 0.25.5-3 | PKCS#11 modules loader |
| libicu76 | 76.1-4 | Unicode Components |
| libicu-dev | 76.1-4 | ICU development |
| libpcre2-8-0 | 10.46-1~deb13u1 | PCRE2 8-bit runtime |
| libpcre2-dev | 10.46-1~deb13u1 | PCRE2 development |
| libattr1 | 2.5.2-3 | Extended attributes |
| libacl1 | 2.3.2-2+b1 | Access control lists |
| libblkid1 | 2.41-5 | Block device ID |
| libmount1 | 2.41-5 | Device mounting |
| libuuid1 | 2.41-5 | UUID library |
| uuid-dev | 2.41-5 | UUID development |
| libsmartcols1 | 2.41-5 | Column output alignment |
| libproc2-0 | 4.0.4-9 | Process information library |
| procps | 4.0.4-9 | /proc utilities |
| tini | 0.19.0-3+b5 | Container init |

---

## 📊 Package Statistics

| Metric | Count |
|--------|-------|
| Total DPKG Packages | 850+ |
| Installed Libraries | ~650 |
| Development Headers | ~150 |
| System Utilities | ~50 |
| Architecture | amd64 (x86_64) |
| Debian Version | 13 (Trixie) |
| Container Type | Kata Container |
| Platform | Alibaba Cloud Function Compute |
| Region | cn-hongkong |

---

