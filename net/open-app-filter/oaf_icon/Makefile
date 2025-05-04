include $(TOPDIR)/rules.mk

PKG_NAME:=oaf_icon
PKG_VERSION:=6.1.1

include $(INCLUDE_DIR)/package.mk

define Package/oaf_icon
 	SECTION:=luci
	CATEGORY:=LuCI
	SUBMENU:=3. Applications
	TITLE:= FULL ICON for luci-app-oaf
	PKGARCH:=all
endef

define Build/Compile
endef

define Package/oaf_icon/install
	$(INSTALL_DIR) $(1)/www/luci-static/resources/app_icons
	$(INSTALL_BIN) ./app_icons/* $(1)/www/luci-static/resources/app_icons
endef

$(eval $(call BuildPackage,oaf_icon))
