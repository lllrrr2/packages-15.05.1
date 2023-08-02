
include $(TOPDIR)/rules.mk

PKG_NAME:=python3-tzdata
PKG_VERSION:=2023.3
PKG_RELEASE:=1

PYPI_NAME:=tzdata
PKG_MD5SUM:=3c8f05d031770659a7d80de5159af202

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-tzdata
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=tzdata
  URL:=https://github.com/python/tzdata/
  DEPENDS:=+python3-light
endef

define Package/python3-tzdata/description
This is a Python package containing zic-compiled 
binaries for the IANA time zone database.
endef

$(eval $(call Py3Package,python3-tzdata))
$(eval $(call BuildPackage,python3-tzdata))
$(eval $(call BuildPackage,python3-tzdata-src))
