
include $(TOPDIR)/rules.mk

PKG_NAME:=python3-w3lib
PKG_VERSION:=2.1.1
PKG_RELEASE:=1

PYPI_NAME:=w3lib
PKG_MD5SUM:=448248f2a9932c4c29add8be3e41e3ad


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
