#
# Copyright (C) 2015-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-ply
PKG_VERSION:=3.11
PKG_RELEASE:=2

PYPI_NAME:=ply
PKG_MD5SUM:=6465f602e656455affcd7c5734c638f8

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=README.md
PKG_MAINTAINER:=Jeffery To <jeffery.to@gmail.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk

define Package/python3-ply
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=lex and yacc for Python
  URL:=http://www.dabeaz.com/ply/
  DEPENDS:=+python3-light
endef

define Package/python3-ply/description
PLY is a 100% Python implementation of the common parsing tools lex
and yacc.
endef

$(eval $(call Py3Package,python3-ply))
$(eval $(call BuildPackage,python3-ply))
$(eval $(call BuildPackage,python3-ply-src))
