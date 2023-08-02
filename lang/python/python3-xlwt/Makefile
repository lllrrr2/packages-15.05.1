#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-xlwt
PKG_VERSION:=1.3.0
PKG_RELEASE:=1

PYPI_NAME:=xlwt
PKG_MD5SUM:=4b1ca8a3cef3261f4b4dc3f138e383a8

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-xlwt
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python xlwt
  URL:=https://pypi.org/project/xlwt
  DEPENDS:= \
	  +python3-light
endef

define Package/python3-xlwt/description
 This is a library for developers to use to generate spreadsheet files 
 compatible with Microsoft Excel versions 95 to 2003.
endef


$(eval $(call Py3Package,python3-xlwt))
$(eval $(call BuildPackage,python3-xlwt))
$(eval $(call BuildPackage,python3-xlwt-src))
