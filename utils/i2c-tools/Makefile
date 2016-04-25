#
# Copyright (C) 2007-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General ic License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=i2c-tools
PKG_VERSION:=3-1-0
PKG_RELEASE:=1

PKG_SOURCE:=V3-1-0.tar.gz
PKG_SOURCE_URL:=https://github.com/groeck/i2c-tools/archive/

include $(INCLUDE_DIR)/package.mk

define Package/i2c-tools
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=I2C tools for Linux
	URL:=http://www.lm-sensors.org/wiki/I2CTools
endef

define Package/i2c-tools/description
 This package contains an heterogeneous set of I2C tools for x. These tools
 were originally part of the lm-sensors package.
 Includes:
 - i2cdetect
 - i2cdump
 - i2cget
 - i2cset
endef

TARGET_CPPFLAGS += -I$(LINUX_DIR)/include

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		LINUX="$(LINUX_DIR)" \
		CC="$(TARGET_CC)" \
		STAGING_DIR="$(STAGING_DIR)"
	$(Build/Compile/python-smbus)
endef

define Package/i2c-tools/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tools/i2cdetect $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tools/i2cdump $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tools/i2cset $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tools/i2cget $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,i2c-tools))

