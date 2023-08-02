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

PKG_NAME:=python3-cssselect
PKG_VERSION:=1.2.0
PKG_RELEASE:=1

PYPI_NAME:=cssselect
PKG_MD5SUM:=27fbafacce5447cb867acb240d35002a

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-cssselect
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Cssselect
  URL:=https://libraries.io/pypi/cssselect
  DEPENDS:= \
	  +python3
endef

define Package/python3-cssselect/description
 Cssselect parses CSS3 Selectors and translate them to XPath 1.0 expressions.
endef

$(eval $(call Py3Package,python3-cssselect))
$(eval $(call BuildPackage,python3-cssselect))
$(eval $(call BuildPackage,python3-cssselect-src))
