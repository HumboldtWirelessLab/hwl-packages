#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
#
# Originalfile: seeks

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=brn-backports
PKG_VERSION:=release
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=$(PKG_SOURCE)
#PKG_SOURCE_PROTO:=git
#PKG_REV:=8548589055930c390679943b605efef8714209d0
#PKG_SOURCE_VERSION:=$(PKG_REV)

include $(INCLUDE_DIR)/package.mk

define Package/backports-brn
  SUBMENU:=Development
  SECTION:=net
  CATEGORY:=Network
  TITLE:=BackportsBRN
  DEPENDS:=
  URL:=http://wireless.kernel.org
endef

define Package/backports-brn/description
  Backports driver including HWL-Patches.
endef

define Build/Prepare
	$(call Build/Prepare/Default)
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) -j1 KERNELPATH="$(LINUX_DIR)" ARCH="$(LINUX_KARCH)" CROSS_COMPILE="$(TARGET_CROSS)"
endef

define Package/backports-brn/install
#	$(MAKE) -C $(PKG_BUILD_DIR) KERNELPATH="$(LINUX_DIR)" ARCH="$(LINUX_KARCH)" CROSS_COMPILE="$(TARGET_CROSS)" DESTDIR="$(1)" BINDIR="/usr/bin" MANDIR="/usr/share/man" install
endef

$(eval $(call BuildPackage,backports-brn))
