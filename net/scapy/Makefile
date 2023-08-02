#
# Copyright (C) 2006-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=scapy
PKG_VERSION:=2.4.4
PKG_RELEASE:=1

PYPI_NAME:=scapy
PKG_MD5SUM:=01e52ff5d1f04364e17fc2d42872282e

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/scapy
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Interactive packet manipulation tool and network scanner
  MAINTAINER:=W. Michael Petullo <mike@flyn.org>
  URL:=https://scapy.net/
  DEPENDS:=+python3
endef

define Package/scapy/description
  Scapy is a powerful interactive packet manipulation program built on top
  of the Python interpreter. It can be used to forge or decode packets of
  a wide number of protocols, send them over the wire, capture them, match
  requests and replies, and much more.
endef

$(eval $(call Py3Package,scapy))
$(eval $(call BuildPackage,scapy))
$(eval $(call BuildPackage,scapy-src))
