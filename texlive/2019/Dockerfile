FROM debian:stretch-slim

RUN apt-get update \
    && apt-get install --no-install-recommends -y fontconfig perl wget \
    && wget --no-check-certificate http://ftp.math.utah.edu/pub/tex/historic/systems/texlive/2019/tlnet-final/install-tl-unx.tar.gz \
    && wget --no-check-certificate https://raw.githubusercontent.com/shoujiaxin/dockerfiles/main/texlive/2019/texlive.profile \
    && tar -xzf install-tl-unx.tar.gz \
    && ./install-tl-*/install-tl -profile texlive.profile -repository http://ftp.math.utah.edu/pub/tex/historic/systems/texlive/2019/tlnet-final/ \
    && TEXMFSYSVAR=$(cat texlive.profile | grep 'TEXMFSYSVAR' | awk '{print $2}') \
    && cp ${TEXMFSYSVAR}/fonts/conf/texlive-fontconfig.conf /etc/fonts/conf.d/09-texlive.conf \
    && fc-cache -fsv \
    && apt-get install --no-install-recommends -y liblog-log4perl-perl liblog-dispatch-perl libyaml-tiny-perl libfile-homedir-perl libunicode-linebreak-perl \
    && rm -r install-tl-*/ \
    && rm install-tl-unx.tar.gz \
    && rm texlive.profile \
    && apt-get autoremove \
    && apt-get autoclean
