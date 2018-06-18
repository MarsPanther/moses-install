# Instalation Mosses
___________________________________________________________________________________________________________________________________________________________________________________________________________________________________

sudo apt-get install g++ git-core automake libtool zlib1g-dev libboost-all-dev libbz2-dev liblzma-dev libgoogle-perftools-dev build-essential pkg-config python-dev csh tcl tcl-dev tk gawk gzip bzip2 p7zip subversion tcsh


cd ~/mosesdecoder/tools/giza-pp
make
cp ~/mosesdecoder/tools/giza-pp/GIZA++-v2/GIZA++ ~/mosesdecoder/tools/giza-pp/GIZA++-v2/snt2cooc.out ~/mosesdecoder/tools/giza-pp/mkcls-v2/mkcls ~/mosesdecoder/tools

cd ~/mosesdecoder/tools/boost_1_66_0
./bootstrap.sh
./b2 -j4 --prefix=$PWD --libdir=$PWD/lib64 --layout=tagged link=static threading=multi,single install || echo FAILURE

cd ~/mosesdecoder/tools/srilm-1.7.2
< \# SRILM = /home/speech/stolcke/project/srilm/devel
> SRILM = /home/islab/mosesdecoder/tools/srilm-1.7.2
sudo tcsh
sudo make NO_TCL=1 MACHINE_TYPE=i686-m64 World
export PATH=/home/islab/mosesdecoder/tools/srilm-1.7.2:/home/islab/mosesdecoder/tools/srilm-1.7.2/bin/i686-m64:/home/islab/mosesdecoder/tools/srilm-1.7.2/bin:$PATH

cd ~/mosesdecoder/tools/cmph-2.0
./configure
make
make check
sudo make install

cd ~/mosesdecoder/tools/irstlm-5.80.08/trunk
sh regenerate-makefiles.sh --force
./configure --prefix=/home/islab/mosesdecoder/tools/irstlm-5.80.08/trunk --disable-cxx0 --enable-caching 
make
make install
export PATH=$HOME/mosesdecoder/tools/irstlm-5.80.08/trunk:$HOME/mosesdecoder/tools/irstlm-5.80.08/trunk/bin:$PATH


cd ~/mosesdecoder

sudo ./bjam --with-boost=/home/islab/mosesdecoder/tools/boost_1_66_0 --with-cmph=/home/islab/mosesdecoder/tools/cmph-2.0 --with-irstlm=/home/islab/mosesdecoder/tools/irstlm-5.80.08/trunk --with-srilm=/home/islab/mosesdecoder/tools/srilm-1.7.2 --with-giza=/home/islab/mosesdecoder/tools -j4





--------------------no need this------------------------------------------
./compile.sh --no-xmlrpc-c
/home/islab/mosesdecoder/tools/irstlm/bin
