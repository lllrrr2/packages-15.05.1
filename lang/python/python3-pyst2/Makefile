
include $(TOPDIR)/rules.mk

PKG_NAME:=python3-pyst2
PKG_VERSION:=0.5.1
PKG_RELEASE:=1

PYPI_NAME:=pyst2
PKG_MD5SUM:=8ac93b77caf1be99852121c0478d0437

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-pyst2
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=A Python Interface to Asterisk
  URL:=https://github.com/jfernandz/pyst2
  DEPENDS:= \
	+python3 \
	+python3-six
endef

define Package/python3-pyst2/description
  A Python Interface to Asterisk
endef

$(eval $(call Py3Package,python3-pyst2))
$(eval $(call BuildPackage,python3-pyst2))
$(eval $(call BuildPackage,python3-pyst2-src))
