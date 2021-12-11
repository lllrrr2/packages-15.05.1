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

PKG_NAME:=python3-w3lib
PKG_VERSION:=1.22.0
PKG_RELEASE:=1

PYPI_NAME:=w3lib
PKG_HASH:=0ad6d0203157d61149fd45aaed2e24f53902989c32fc1dccc2e2bfba371560df

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-w3lib
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Library of web-related functions
  URL:=https://libraries.io/pypi/w3lib
  DEPENDS:= \
	  +python3-light
endef

define Package/python3-w3lib/description
 Library of web-related functions.
endef

$(eval $(call Py3Package,python3-w3lib))
$(eval $(call BuildPackage,python3-w3lib))
$(eval $(call BuildPackage,python3-w3lib-src))
