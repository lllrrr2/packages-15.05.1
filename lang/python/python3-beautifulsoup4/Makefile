#
# Copyright (C) 2007-2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-beautifulsoup4
PKG_VERSION:=4.9.3
PKG_RELEASE:=1

PYPI_NAME:=beautifulsoup4
PKG_HASH:=84729e322ad1d5b4d25f805bfa05b902dd96450f43842c4e99067d5e1369eb25

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-beautifulsoup4
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=library that makes it easy to scrape information from web pages. 
  URL:=https://www.crummy.com/software/BeautifulSoup/
  DEPENDS:= \
	  +python3-light \
	  +python3-soupsieve
endef

define Package/python3-beautifulsoup4/description
Beautiful Soup is a library that makes it easy to scrape information from web pages. 
endef

$(eval $(call Py3Package,python3-beautifulsoup4))
$(eval $(call BuildPackage,python3-beautifulsoup4))
$(eval $(call BuildPackage,python3-beautifulsoup4-src))
