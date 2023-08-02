#
# Copyright (C) Alexandru Ardelean <ardeleanalex@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-pymysql
PKG_VERSION:=1.0.2
PKG_RELEASE:=1

PYPI_NAME:=PyMySQL
PKG_HASH:=3fe6ff2eefb58af5c54d335c6e0216de

PKG_MAINTAINER:=Alexandru Ardelean <ardeleanalex@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_CONFIG_DEPENDS:=CONFIG_PYTHON3_PYMYSQL_SHA_PASSWORD_SUPPORT

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-pymysql
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Pure Python MySQL Client
  URL:=https://pymysql.readthedocs.io/
  DEPENDS:=+python3 +PYTHON3_PYMYSQL_SHA_PASSWORD_SUPPORT:python3-cryptography
endef

define Package/python3-pymysql/config
  source "$(SOURCE)/Config.in"
endef

define Package/python3-pymysql/description
  This package contains a pure-Python MySQL client library, based on PEP 249.
endef

$(eval $(call Py3Package,python3-pymysql))
$(eval $(call BuildPackage,python3-pymysql))
$(eval $(call BuildPackage,python3-pymysql-src))
