FROM fedora:36
COPY 68k-diskdefs /tmp
RUN \
  dnf update -y && \ 
  dnf install -y unix2dos m4 wget xz gcc gcc-c++ gmp-devel mpfr-devel libmpc-devel make file texinfo srecord git libdsk java-11-openjdk unzip zip man vim-common diffutils findutils elfutils && \
  dnf clean all && \
  cd /opt && \
  git clone https://github.com/daveho/GALasm.git && \
  cd GALasm/src && \
  make all && \
  cp ./galasm /usr/local/bin && \
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
  wget --quiet https://ftp.gnu.org/gnu/binutils/binutils-2.38.tar.xz && \
  wget --quiet https://ftp.gnu.org/pub/gnu/gcc/gcc-12.1.0/gcc-12.1.0.tar.xz && \
  xz -d binutils-2.38.tar.xz && \
  xz -d gcc-12.1.0.tar.xz && \
  tar xf binutils-2.38.tar && \
  tar xf gcc-12.1.0.tar && \
  mkdir binutils && \
  cd binutils && \
  ../binutils-2.38/configure --target=m68k-elf && \
  make && \
  make install && \
  mkdir ../gcc && \
  cd ../gcc && \
  ../gcc-12.1.0/configure --target=m68k-elf --enable-languages=c,c++ --disable-libssp --disable-debug --disable-dependency-tracking --disable-silent-rules --disable-nls && \
  make all-gcc all-target-libgcc && \
  make install-gcc install-target-libgcc && \
  mkdir /opt/work && \
  echo "cd /opt/work" >> ~/.bashrc
