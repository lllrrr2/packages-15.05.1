#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-docx
PKG_VERSION:=0.8.11
PKG_RELEASE:=1

PYPI_NAME:=python-docx
PKG_MD5SUM:=231baf33ba280d3d751ce50d48872a1e

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-docx
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:= python-docx is a Python library for creating and updating Microsoft Word (.docx) files.
  URL:=https://github.com/python-openxml/python-docx
  DEPENDS:= \
	  +python3-light \
	  +python3-lxml
endef

define Package/python3-docx/description
  python-docx is a Python library for creating and updating Microsoft Word (.docx) files.
endef

$(eval $(call Py3Package,python3-docx))
$(eval $(call BuildPackage,python3-docx))
$(eval $(call BuildPackage,python3-docx-src))
