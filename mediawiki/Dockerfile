FROM mediawiki:latest

RUN git clone --depth 1 -b $MEDIAWIKI_BRANCH \
      https://gerrit.wikimedia.org/r/p/mediawiki/extensions/Scribunto \
      /var/www/html/extensions/Scribunto \
      && chmod a+x /var/www/html/extensions/Scribunto/includes/engines/LuaStandalone/binaries/lua*_linux_*/lua

RUN git clone --depth 1 -b $MEDIAWIKI_BRANCH \
      https://gerrit.wikimedia.org/r/p/mediawiki/extensions/BetaFeatures \
      /var/www/html/extensions/BetaFeatures

RUN git clone --depth 1 -b $MEDIAWIKI_BRANCH \
      https://gerrit.wikimedia.org/r/p/mediawiki/extensions/TemplateData \
      /var/www/html/extensions/TemplateData

RUN git clone -b $MEDIAWIKI_BRANCH \
      https://gerrit.wikimedia.org/r/p/mediawiki/extensions/VisualEditor.git \
      /var/www/html/extensions/VisualEditor \
      && cd /var/www/html/extensions/VisualEditor \
      && git submodule update --init \
      && cd /var/www/html

RUN git clone --depth 1 -b $MEDIAWIKI_BRANCH \
      https://gerrit.wikimedia.org/r/p/mediawiki/extensions/MobileFrontend \
      /var/www/html/extensions/MobileFrontend

RUN git clone --depth 1 -b $MEDIAWIKI_BRANCH \
      https://gerrit.wikimedia.org/r/p/mediawiki/skins/MinervaNeue \
      /var/www/html/skins/MinervaNeue



