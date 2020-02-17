FROM fedora:31
COPY 68k-diskdefs /tmp
RUN \
  dnf update -y && \ 
  dnf install -y wget xz gcc gcc-c++ gmp-devel mpfr-devel libmpc-devel make file texinfo srecord git cpmtools java-11-openjdk unzip zip man vim-common && \
  cat /tmp/68k-diskdefs >> /usr/share/cpmtools/diskdefs && \
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
  mkdir /opt/emu && \
  cd /opt/emu && \
  wget https://dl.bintray.com/edadma/generic/m68k-0.1.1.jar && \
  echo "cd /opt/work" >> ~/.bashrc
