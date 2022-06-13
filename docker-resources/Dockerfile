FROM alpine:3.15

# I think that 32MB is "small enough"
# It was 69MB before all the "rm"s

# See the line starting with "sub load_dependencies {" in swaks' source code
RUN set -e \
 && apk add --no-cache ca-certificates git git-email bash \
# For python 3 and the needed jinja2 library:
      py3-jinja2 py3-markupsafe \
#      perl perl-mime-base64 perl-digest-md5 perl-digest-sha1 perl-ntlm \
#      perl-authen-sasl perl-net-dns perl-time-hires \
#      perl-socket perl-io-socket-inet6 \
# Various text editors:
      nano vim vimdiff upx \
 && update-ca-certificates \
# && wget -O /usr/local/bin/swaks 'https://raw.githubusercontent.com/jetmore/swaks/master/swaks' \
# && chmod +x /usr/local/bin/swaks \
# clean up python installation to save lots of disk space
 && rm -rf $(find /usr/lib/python3.*/ -name __pycache__) /usr/lib/python3.9/ensurepip /usr/lib/python3.9/pydoc_data/ \
# install micro text editor
 && cd /usr/bin/ \
 && ( wget -O- https://getmic.ro/r | sh ) \
# save disk space with compression:
 && upx --lzma -9 ./micro \
 && upx --lzma -9 ./vim \
 && upx --lzma -9 ./nano \
 && cd /usr/share/perl5/core_perl \
 && rm -rf CPAN Pod Test2 TAP File B Test Tie CPAN.pm Text JSON Archive \
 && cd /usr/lib/perl5/core_perl \
 && rm -rf CPAN Pod Test2 TAP File B Test Tie CPAN.pm Text JSON Archive \
 && cd / \
 && rm -rf /usr/lib/perl5/core_perl/auto/Encode /usr/share/perl5/core_perl/unicore /usr/bin/git-shell /usr/libexec/git-core/git-http-fetch /usr/libexec/git-core/git-http-push /usr/libexec/git-core/git-sh-i18n--envsubst /usr/libexec/git-core/git-remote-ftp \
 && rm -rf /usr/lib/libbrotlienc.so.* /usr/lib/libnghttp2.so.* /usr/lib/libbrotlicommon.so.* \
 # remove apk and upx as we no longer need them
 && apk --purge del apk-tools upx \
 && rm -rf /usr/share/apk/ /usr/share/perl5/core_perl/Unicode /usr/lib/perl5/core_perl/auto/Unicode \
# Now setup /credentials-store
 && mkdir -p /credentials-store \
 && ln -sfT /credentials-store/etc-gitconfig /etc/gitconfig \
 && ln -sfT /credentials-store/editor /usr/bin/editor

COPY setup-and-send-email /usr/local/bin/

# removed autofillemail library
#COPY autofillemail/ /usr/local/share/
#ENV AUTOFILLEMAILDIR=/usr/local/share/autofillemail

ENTRYPOINT ["/bin/bash", "/usr/local/bin/setup-and-send-email"]
CMD []

