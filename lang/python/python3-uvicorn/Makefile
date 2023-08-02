# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-uvicorn
PKG_VERSION:=0.22.0
PKG_RELEASE:=1

PYPI_NAME:=uvicorn
PKG_MD5SUM:=f83e1cf9f7fbe21ceeee8be3780b7e51

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-uvicorn
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=an ASGI web server
  URL:=https://github.com/MagicStack/uvloop
  DEPENDS:=+python3-light +python3-click +python3-h11
endef

define Package/python3-uvicorn/description
Uvicorn is an ASGI web server implementation for Python.
endef

$(eval $(call Py3Package,python3-uvicorn))
$(eval $(call BuildPackage,python3-uvicorn))
$(eval $(call BuildPackage,python3-uvicorn-src))
