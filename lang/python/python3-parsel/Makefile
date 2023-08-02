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

PKG_NAME:=parsel
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/scrapy/parsel
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=7ed4b24a9b8ef874c644c6cec01654539bc66cc3
PKG_MD5SUM:=37d4721bb35983e6dfb30eec43a6e36e

PKG_BUILD_DIR:=$(BUILD_DIR)/pypi/parsel-$(PKG_VERSION)

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
