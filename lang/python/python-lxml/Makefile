#
# Copyright (C) 2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-lxml
PKG_VERSION:=4.4.2
PKG_RELEASE:=2

PYPI_NAME:=lxml
PKG_HASH:=eff69ddbf3ad86375c344339371168640951c302450c5d3e9936e98d6459db06

PKG_LICENSE:=BSD
PKG_LICENSE_FILES:=LICENSES.txt
PKG_MAINTAINER:=Alexandru Ardelean <ardeleanalex@gmail.com>
PKG_CPE_ID:=cpe:/a:lxml:lxml

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk

define Package/python3-lxml
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=python3-lxml
  URL:=https://lxml.de
  DEPENDS:=+libxml2 +libxslt +libexslt +python3-light
endef

define Package/python3-lxml/description
The lxml XML toolkit is a Pythonic binding
for the C libraries libxml2 and libxslt.
endef

TARGET_LDFLAGS += -lxml2 -lxslt -lexslt

define Py3Build/Compile
	$(call Python3/ModSetup,, \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
		--static \
		--single-version-externally-managed \
		, \
		INCLUDE="$(STAGING_DIR)/usr/include/ $(STAGING_DIR)/usr/include/libxml2" \
		LIBRARY="$(STAGING_DIR)/usr/lib $(STAGING_DIR)/lib" \
		CFLAGS="$(TARGET_CFLAGS)" \
		LDFLAGS="$(TARGET_LDFLAGS)" \
	)
endef

$(eval $(call Py3Package,python3-lxml))
$(eval $(call BuildPackage,python3-lxml))
$(eval $(call BuildPackage,python3-lxml-src))
