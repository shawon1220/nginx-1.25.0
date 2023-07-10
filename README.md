# nginx-1.25.0
window nginx  HTTP 2，SSL/TLS HTTPS 支持，HTTP 流媒体支持，socket 流转发支持，mail 服务器支持，concat静态文件合并支持

### 当前版本已编译到release目录，可以直接拷贝该目录到指定目录，点击nginx.bat使用。注意修改ssl配置信息和bat配置，如下图：
#### ssl.conf:
![image](https://github.com/shawon1220/nginx-1.25.0/assets/10345404/dc79994c-89f4-440d-825c-d435e245baef)

#### nginx.bat:
![image](https://github.com/shawon1220/nginx-1.25.0/assets/10345404/e967d1bc-e9f3-4183-9abc-e6b23c248e0c)


===================================================================>


## 如需新增模块，徐重新编译：

### 编译依赖工具：
1. Perl: https://strawberryperl.com/
2. MSYS2: https://www.msys2.org/

### 执行编译
1. 运行MSYS2窗口，cd切换到源码目录，执行如下命令，生成Makefile文件
```
auto/configure \
  --with-cc=cl \
  --prefix= \
  --conf-path=conf/nginx.conf \
  --pid-path=logs/nginx.pid \
  --http-log-path=logs/access.log \
  --error-log-path=logs/error.log \
  --sbin-path=nginx.exe \
  --http-client-body-temp-path=temp/client_body_temp \
  --http-proxy-temp-path=temp/proxy_temp \
  --http-fastcgi-temp-path=temp/fastcgi_temp \
  --http-scgi-temp-path=temp/scgi_temp \
  --http-uwsgi-temp-path=temp/uwsgi_temp \
  --with-cc-opt=-DFD_SETSIZE=1024 \
  --with-pcre=objs/pcre-8.40 \
  --with-zlib=objs/zlib-1.2.11 \
  --with-openssl=objs/openssl-3.0.9 \
  --with-openssl-opt='no-asm no-tests -D_WIN32_WINNT=0x0601' \
  --with-http_ssl_module \
  --with-http_v2_module \
  --with-http_realip_module \
  --with-http_addition_module \
  --with-http_sub_module \
  --with-http_stub_status_module \
  --with-http_dav_module \
  --with-http_flv_module \
  --with-http_mp4_module \
  --with-http_gunzip_module \
  --with-http_gzip_static_module \
  --with-http_auth_request_module \
  --with-http_random_index_module \
  --with-http_secure_link_module \
  --with-http_slice_module \
  --with-mail \
  --with-mail_ssl_module \
  --with-stream \
  --with-stream_ssl_module \
  --with-stream_ssl_preread_module \
	--add-module=objs/nginx_concat_module
```
2. 使用vs工具编译，cd切换到源码根目录，执行：nmake –f objs/Makefile

   ![image](https://github.com/shawon1220/nginx-1.25.0/assets/10345404/49cffc9f-a22d-4ad9-9bd7-2c762d26c33c)
