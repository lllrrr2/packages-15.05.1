
include $(TOPDIR)/rules.mk

PKG_NAME:=pypdf2
PKG_VERSION:=2.1.1
PKG_RELEASE:=1

PYPI_NAME:=PyPDF2
PKG_MD5SUM:=af2a24eb56359b44dd1a4188efb58732

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-pypdf2
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=pure-python PDF library
  URL:=https://github.com/mstamy2/PyPDF2
  DEPENDS:= \
	  +python3
endef

define Package/python3-pypdf2/description
 PyPDF2 is a pure-python PDF library capable of splitting, merging together,
 cropping, and transforming the pages of PDF files. It can also add custom
 data, viewing options, and passwords to PDF files. It can retrieve text 
 and metadata from PDFs as well as merge entire files together.
endef

$(eval $(call Py3Package,python3-pypdf2))
$(eval $(call BuildPackage,python3-pypdf2))
$(eval $(call BuildPackage,python3-pypdf2-src))
