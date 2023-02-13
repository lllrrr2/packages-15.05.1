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

ifeq ($(ARCH),arm)
ifdef CONFIG_TARGET_armvirt
	runc_ARCH:=arm
	PKG_MD5SUM:=c7768b0ecf332129408e2e228d9925d7
endif
endif

PKG_SOURCE_URL:=https://raw.githubusercontent.com/syb999/cc-upx/master/runc/$(runc_ARCH)
PKG_SOURCE:=runc


define Build/Prepare
	mv $(DL_DIR)/$(PKG_SOURCE) $(PKG_BUILD_DIR)
endef

define Build/Compile
endef

define Package/runc/install
	$(INSTALL_DIR) $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/runc $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,runc))
