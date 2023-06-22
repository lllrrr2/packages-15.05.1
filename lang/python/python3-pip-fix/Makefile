
include $(TOPDIR)/rules.mk

PKG_NAME:=python3-pip-fix
PKG_VERSION:=1

include $(INCLUDE_DIR)/package.mk

define Package/python3-pip-fix
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-pip-fix
  PKGARCH:=all
  DEPENDS:= \
      +python3-pip
endef

define Build/Compile
endef

define Package/python3-pip-fix/install
	$(INSTALL_DIR) $(1)/usr/lib/python3.8/site-packages/pip/_vendor/pep517
	$(INSTALL_BIN) ./files/_in_process.py $(1)/usr/lib/python3.8/site-packages/pip/_vendor/pep517/_in_process.py
	$(INSTALL_DIR) $(1)/usr/include
	$(INSTALL_BIN) ./files/ffi/* $(1)/usr/include
	$(INSTALL_DIR) $(1)/usr/include/python3.8
	$(INSTALL_BIN) ./files/include/* $(1)/usr/include/python3.8
	$(INSTALL_DIR) $(1)/usr/include/python3.8/cpython
	$(INSTALL_BIN) ./files/cpython/* $(1)/usr/include/python3.8/cpython
	$(INSTALL_DIR) $(1)/usr/include/python3.8/internal
	$(INSTALL_BIN) ./files/internal/* $(1)/usr/include/python3.8/internal
endef

$(eval $(call BuildPackage,python3-pip-fix))










