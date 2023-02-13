include $(TOPDIR)/rules.mk

PKG_NAME:=runc
PKG_VERSION:=1.0.0-rc6
PKG_RELEASE:=1
PKG_SOURCE_VERSION:=52b36a2dd837e8462de8e01458bf02cf9eea47dd

include $(INCLUDE_DIR)/package.mk

define Package/runc/config
config RUNC_SECCOMP
	depends on PACKAGE_runc
	bool "Enable support for seccomp in runc"
	default DOCKER_SECCOMP
	select KERNEL_SECCOMP
	select PACKAGE_libseccomp
	help
	  Build runc with support for seccomp filters.
	  Select libseccomp which also pulls-in the needed kernel features.
endef

define Package/runc
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=runc container runtime
  URL:=https://www.opencontainers.org/
  DEPENDS:=+RUNC_SECCOMP:libseccomp +libpthread @TARGET_armvirt
  MENU:=1
endef

define Package/runc/description
runc is a CLI tool for spawning and running containers according to the OCI specification.
endef

ifeq ($(CONFIG_RUNC_SECCOMP),y)
MAKE_FLAGS += BUILDTAGS='seccomp'
else
MAKE_FLAGS += BUILDTAGS=''
endif

define Build/Prepare
endef

define Build/Compile
endef

define Package/runc/install
	$(INSTALL_DIR) $(1)/usr/sbin/
	$(INSTALL_BIN) ./files/arm/runc $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,runc))
