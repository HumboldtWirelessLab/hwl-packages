#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
#
# Originalfile: seeks

include $(TOPDIR)/rules.mk

PKG_NAME:=click-brn
PKG_VERSION:=0.0.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:="https://github.com/HumboldtWirelessLab/click-brn.git"
#PKG_SOURCE_URL:="git@github.com:HumboldtWirelessLab/click-brn.git"
PKG_SOURCE_PROTO:=git
PKG_REV:=e82ee68b278909d181504cb060a9af41141668f1
PKG_SOURCE_VERSION:=$(PKG_REV)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/click-brn
  SUBMENU:=Development
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Click Modular Router (HWL)
  URL:=http://edu.
  DEPENDS:=$(CXX_DEPENDS) +libpcap +libopenssl +libiw +libstdcpp +libexpat
  MAINTAINER:=RobAt <sombrutz@gmail.com>
endef

define Package/click-brn/description
 Click-brn ist the Click Modular Router developed at the MIT with several add-ons.
endef


CONFIGURE_VARS:= \
	 CXXFLAGS="-I$(STAGING_DIR)/usr/include $(ICONV_CFLAGS) $(TARGET_CFLAGS)" \
	 LDFLAGS="-L$(STAGING_DIR)/usr/lib      $(ICONV_LDFLAGS)" \

CONFIGURE_ARGS += \
	--prefix=/usr \
	--enable-wifi \
	--enable-brn \
	--enable-analysis \
	--enable-ialign \
	--disable-linuxmodule \
	--enable-tools=host \
	--enable-userlevel \
	--disable-dynamic-linking \
	--disable-threads

define Build/Configure
	$(call Build/Configure/Default)
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CXXFLAGS="-I$(STAGING_DIR)/usr/include $(ICONV_CFLAGS) $(TARGET_CFLAGS)"
endef

#define Package/click-brn/conffiles
#endef

define Package/click-brn/install
	$(MAKE) -C $(PKG_BUILD_DIR) DESTDIR="$(1)" install-userlevel install-tools
endef

$(eval $(call BuildPackage,click-brn))
