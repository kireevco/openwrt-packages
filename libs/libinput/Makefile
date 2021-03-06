#
# Copyright (C) 2007-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libinput
PKG_VERSION:=0.21.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=http://www.freedesktop.org/software/libinput/
PKG_MD5SUM:=f91d8f4ced986f1ae16d52ea02bc7837

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=Daniel Golle <daniel@makrotopia.org>

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

TARGET_CFLAGS+= -std=gnu99

define Package/libinput
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=a library to handle input devices
  URL:=http://freedesktop.org/wiki/Software/libinput/
  DEPENDS:=+libevdev +mtdev +udev
endef

define Package/libinput/description
  libinput is a library to handle input devices in Wayland compositors
  and to provide a generic X.Org input driver. It provides device
  detection, device handling, input device event processing and
  abstraction so minimize the amount of custom input code compositors
  need to provide the common set of functionality that users expect.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.{la,so*} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* $(1)/usr/lib/pkgconfig/
endef

define Package/libinput/install
	$(INSTALL_DIR) $(1)/usr/lib/udev
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/udev/* $(1)/usr/lib/udev
endef

$(eval $(call BuildPackage,libinput))
