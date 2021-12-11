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

PKG_NAME:=python3-parsel
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PYPI_NAME:=parsel
PKG_HASH:=70efef0b651a996cceebc69e55a85eb2233be0890959203ba7c3a03c72725c79

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-parsel
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=parsel library
  URL:=https://github.com/scrapy/parsel
  DEPENDS:= \
	  +python3-light \
	  +python3-six \
	  +python3-lxml \
	  +python3-w3lib \
	  +python3-cssselect
endef

define Package/python3-parsel/description
 Parsel is a BSD-licensed Python library to extract and remove data from
 HTML and XML using XPath and CSS selectors, optionally combined with
 regular expressions.
endef

$(eval $(call Py3Package,python3-parsel))
$(eval $(call BuildPackage,python3-parsel))
$(eval $(call BuildPackage,python3-parsel-src))
