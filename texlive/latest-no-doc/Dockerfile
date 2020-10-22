FROM debian:stretch-slim

RUN apt-get update \
    && apt-get install --no-install-recommends -y fontconfig perl wget \
    && wget --no-check-certificate http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz \
    && wget --no-check-certificate https://raw.githubusercontent.com/shoujiaxin/dockerfiles/main/texlive/latest-no-doc/texlive.profile \
    && tar -xzf install-tl-unx.tar.gz \
    && ./install-tl-*/install-tl -profile texlive.profile \
    && TEXMFSYSVAR=$(cat texlive.profile | grep 'TEXMFSYSVAR' | awk '{print $2}') \
    && cp ${TEXMFSYSVAR}/fonts/conf/texlive-fontconfig.conf /etc/fonts/conf.d/09-texlive.conf \
    && fc-cache -fsv \
    && apt-get install --no-install-recommends -y liblog-log4perl-perl liblog-dispatch-perl libyaml-tiny-perl libfile-homedir-perl libunicode-linebreak-perl \
    && rm -r install-tl-*/ \
    && rm install-tl-unx.tar.gz \
    && rm texlive.profile \
    && apt-get autoremove \
    && apt-get autoclean
