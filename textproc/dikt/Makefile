# Created by: Goran Tal <goran.tal@gmail.com>
# $FreeBSD$

PORTNAME=	dikt
PORTVERSION=	2s1
PORTREVISION=	2
PORTEPOCH=	1
CATEGORIES=	textproc net kde
MASTER_SITES=	https://bitbucket.org/dikt/code/downloads/

MAINTAINER=	goran.tal@gmail.com
COMMENT=	Dictionary for KDE

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		cmake compiler:c++11-lang kde:5 qt:5 tar:txz
USE_KDE=	auth bookmarks codecs completion config configwidgets coreaddons dbusaddons guiaddons i18n \
		iconthemes itemviews jobwidgets kio service solid widgetsaddons xmlgui
USE_QT=		concurrent core dbus gui network printsupport svg widgets xml \
		buildtools_build qmake_build

PLIST_FILES=	bin/dikt \
		share/applications/dikt.desktop \
		share/dikt/dikt.css \
		share/dikt/format.conf \
		share/icons/hicolor/128x128/apps/dikt.png \
		share/kservices5/dict.protocol \
		share/kxmlgui5/dikt/diktui.rc

.include <bsd.port.mk>
