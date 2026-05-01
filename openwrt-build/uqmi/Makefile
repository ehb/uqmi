include $(TOPDIR)/rules.mk

PKG_NAME:=uqmi
PKG_RELEASE:=99

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ehb/uqmi.git
PKG_SOURCE_DATE:=2026-05-01
PKG_SOURCE_VERSION:=__PKG_SOURCE_VERSION__
PKG_MIRROR_HASH:=skip
PKG_MAINTAINER:=ehb

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=

PKG_FLAGS:=nonshared
PKG_BUILD_FLAGS:=gc-sections

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/uqmi
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=WWAN
  DEPENDS:=+libubox +libblobmsg-json +kmod-usb-net +kmod-usb-net-qmi-wwan +wwan
  TITLE:=Control utility for mobile broadband modems (with --set-lte-band)
endef

define Package/uqmi/description
  uqmi is a command line tool for controlling mobile broadband modems using
  the QMI-protocol. This fork adds --set-lte-band for LTE band preference.
endef

TARGET_CFLAGS += \
	-I$(STAGING_DIR)/usr/include \
	-Wno-error=maybe-uninitialized

CMAKE_OPTIONS += \
	-DDEBUG=1

define Package/uqmi/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/uqmi/uqmi $(1)/sbin/
	$(CP) ./files/* $(1)/
endef

$(eval $(call BuildPackage,uqmi))
