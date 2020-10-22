FROM shoujiaxin/texlive:latest-no-doc

RUN mkdir /usr/share/fonts/windowsfonts \
    && wget -P /usr/share/fonts/windowsfonts http://virmachnyc1.shoujiaxin.tk:9000/resources/windows/fonts/SIMLI.TTF \
    && fc-cache -fsv \
    && TEXLIVEVER=$(latex -version | grep -o 'TeX Live.*[0-9]' | awk '{print $3}') \
    && echo "\setCJKfamilyfont{zhili}{LiSu}" >> /usr/local/texlive/${TEXLIVEVER}/texmf-dist/tex/latex/ctex/fontset/ctex-fontset-fandol.def \
    && echo "\NewDocumentCommand \lishu { } { \CJKfamily { zhili } }" >> /usr/local/texlive/${TEXLIVEVER}/texmf-dist/tex/latex/ctex/fontset/ctex-fontset-fandol.def
