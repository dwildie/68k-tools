FROM fedora:33
COPY 68k-diskdefs /tmp
RUN \
  dnf update -y && \ 
  dnf install -y unix2dos m4 wget xz gcc gcc-c++ gmp-devel mpfr-devel libmpc-devel make file texinfo srecord git libdsk java-11-openjdk unzip zip man vim-common diffutils && \
  dnf clean all && \
  mkdir /opt/cpmtools && \
  cd /opt/cpmtools && \
  wget http://www.moria.de/~michael/cpmtools/files/cpmtools-2.21.tar.gz && \
  tar xzf cpmtools-2.21.tar.gz && \
  cd cpmtools-2.21 && \
  ./configure && \
  make && \
  cat /tmp/68k-diskdefs >> diskdefs && \
  make install && \
  cd /opt/cpmtools && \
  rm  cpmtools-2.21.tar.gz && \
  mkdir /opt/gas && \
  cd /opt/gas && \
  wget --quiet https://ftp.gnu.org/gnu/binutils/binutils-2.33.1.tar.xz && \
  wget --quiet https://ftp.gnu.org/pub/gnu/gcc/gcc-9.2.0/gcc-9.2.0.tar.xz && \
  xz -d binutils-2.33.1.tar.xz && \
  xz -d gcc-9.2.0.tar.xz && \
  tar xf binutils-2.33.1.tar && \
  tar xf gcc-9.2.0.tar && \
  mkdir binutils && \
  cd binutils && \
  ../binutils-2.33.1/configure --target=m68k-elf && \
  make && \
  make install && \
  mkdir ../gcc && \
  cd ../gcc && \
  ../gcc-9.2.0/configure --target=m68k-elf --enable-languages=c --disable-libssp && \
  make && \
  make install && \
  mkdir /opt/work && \
  echo "cd /opt/work" >> ~/.bashrc
