##lua-resty-qrencode module for openresty

在已安装openresty基础上安装依赖库qrencode，openshit平台上需DIY安装，libpng库已有不安装。


wget http://fukuchi.org/works/qrencode/qrencode-3.4.4.tar.gz

tar -xvzf qrencode-3.4.4.tar.gz

cd /tmp/qrencode-3.4.4

./configure prefix=${OPENSHIFT_DATA_DIR}usr/local/libqrencode/

make

make install

cd ..

git clone https://github.com/lamubake/lua-resty-qrencode.git

cd lua-resty-qrencode/clib

make

make install

使用方法：

local resty_qr = require "resty.QRcode";

local str = "http://www.jungule.com";

local file = "/tmp/qr.png";

local color = "FF00F3";  --RGB

local qr = resty_qr:new(8, 4, 72, color);  -- size margin dpi fg_color bg_color

local status = qr:saveQr(str, 0, 2, file)    -- str level mode path_img
