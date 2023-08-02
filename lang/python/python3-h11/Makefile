# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-h11
PKG_VERSION:=0.14.0
PKG_RELEASE:=1

PYPI_NAME:=h11
PKG_MD5SUM:=84c33fc0aa1f868928114c4d02c43dc2

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-h11
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=a little HTTP/1.1 library
  URL:=https://github.com/python-hyper/h11
  DEPENDS:=+python3-light
endef

define Package/python3-h11/description
  It's a "bring-your-own-I/O" library;
  h11 contains no IO code whatsoever.
endef

$(eval $(call Py3Package,python3-h11))
$(eval $(call BuildPackage,python3-h11))
$(eval $(call BuildPackage,python3-h11-src))
