#
# Copyright (C) 2007-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-simplejson
PKG_VERSION:=3.17.3
PKG_RELEASE:=1
PKG_LICENSE:=MIT
PKG_CPE_ID:=cpe:/a:simplejson_project:simplejson

PYPI_NAME:=simplejson
PKG_MD5SUM:=1dd5baacc5609ecb5a96ade67a6a8027
PKG_MAINTAINER:=Alexandru Ardelean <ardeleanalex@gmail.com>

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-simplejson
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Simple, fast, extensible JSON encoder/decoder
  URL:=https://simplejson.readthedocs.org/
  DEPENDS:=+python3-light +python3-decimal
endef

define Package/python3-simplejson/description
  Simple, fast, extensible JSON encoder/decoder for Python
endef

define Py3Package/python3-simplejson/filespec
+|$(PYTHON3_PKG_DIR)
-|$(PYTHON3_PKG_DIR)/simplejson/tests
endef

$(eval $(call Py3Package,python3-simplejson))
$(eval $(call BuildPackage,python3-simplejson))
$(eval $(call BuildPackage,python3-simplejson-src))
