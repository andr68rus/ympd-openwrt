#
# Copyright (C) 2020 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ympd
PKG_VERSION:=2018-03-29
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/notandy/ympd.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=612f8fc0b2c47fc89d403e4a044541c6b2b238c8
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MAINTAINER:=Andrey S. Shidakov <andrey@shidakov.ru>

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/ympd
    TITLE:=ympd
    SECTION:=utils
    CATEGORY:=Utilities
    URL:=http://ympd.org
    DEPENDS:=+libmpdclient +libpthread +libopenssl
endef

define Package/ympd/description
    MPD Web GUI - written in C, utilizing Websockets and Bootstrap/JS
endef

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)


TARGET_CFLAGS += "-std=gnu99"
TARGET_LDFLAGS += -lpthread -lmpdclient

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	cd $(PKG_BUILD_DIR)
	tar xzf $(DL_DIR)/$(PKG_SOURCE) -C $(BUILD_DIR)
	mkdir -p $(PKG_BUILD_DIR)/build
	cd $(PKG_BUILD_DIR)/build
endef

define Package/ympd/install
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ympd $(1)/
endef

$(eval $(call BuildPackage,ympd))
