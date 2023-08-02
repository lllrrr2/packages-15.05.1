#
# Copyright (C) 2019 Jakub Piotr Cłapa <jpc@loee.pl>
# Copyright (C) 2020 Alexandru Ardelean <ardeleanalex@gmail.com>
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-numpy
PKG_VERSION:=1.20.2
PKG_RELEASE:=1

PYPI_NAME:=numpy
PKG_MD5SUM:=5e1b381630af4d18db0fedd56b6d8da2

PKG_MAINTAINER:=Alexandru Ardelean <ardeleanalex@gmail.com>

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE.txt
PKG_CPE_ID:=cpe:/a:numpy:numpy

# yes, zip... sigh
PYPI_SOURCE_EXT:=zip
HOST_PYTHON3_PACKAGE_BUILD_DEPENDS:=Cython

HOST_BUILD_DEPENDS:=python3/host

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-numpy
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=The fundamental package for scientific computing with Python
  URL:=https://www.numpy.org/
  DEPENDS:=@!SOFT_FLOAT +INSTALL_GFORTRAN:libgfortran +python3
endef

define Package/python3-numpy/description
NumPy is the fundamental package for array computing with Python.

By default, this package is built without some modules.
For some modules to be available, the INSTALL_GFORTRAN symbol needs
to be enabled in the OpenWrt core/toolchain.
endef


$(eval $(call Py3Package,python3-numpy))
$(eval $(call BuildPackage,python3-numpy))
$(eval $(call BuildPackage,python3-numpy-src))