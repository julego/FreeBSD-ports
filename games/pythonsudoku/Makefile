# Created by: Rusmir Dusko <nemysis@FreeBSD.org>
# $FreeBSD$

PORTNAME=	pythonsudoku
PORTVERSION=	0.13
PORTREVISION=	12
CATEGORIES=	games python
MASTER_SITES=	SF/${PORTNAME}/Python%20Sudoku/${PORTVERSION}/ \
		SF/nemysisfreebsdp/games/:icons
DISTFILES=	${PORTNAME}-${DISTVERSION}${EXTRACT_SUFX} \
		${PORTNAME}.png:icons
DIST_SUBDIR=	python
EXTRACT_ONLY=	${PORTNAME}-${DISTVERSION}${EXTRACT_SUFX}

MAINTAINER=	bofh@FreeBSD.org
COMMENT=	Text and graphical program to create or resolve Sudokus

LICENSE=	GPLv2+
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS+=	libcups.so:print/cups
RUN_DEPENDS=	${PYGAME} \
		${PYTHON_PKGNAMEPREFIX}pillow>=0:graphics/py-pillow@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}reportlab>=0:print/py-reportlab@${PY_FLAVOR}

USES=		gnome python:2.7 tar:bzip2
USE_GNOME=	pygtk2
USE_PYTHON=	distutils

PORTDOCS=	*

DESKTOP_ENTRIES="Python Sudoku" "" "${PORTNAME}" \
		"${PORTNAME}" "Game;LogicGame;" ""
INSTALLS_ICONS=	yes
NO_ARCH=	yes

OPTIONS_DEFINE=	DOCS NLS
OPTIONS_SUB=	yes
NLS_USES=	gettext-runtime:run

post-patch:
	@${REINPLACE_CMD} -e 's|/usr/games|${PREFIX}/bin|; \
		s|/usr/share/games|${PREFIX}/share|' \
		${WRKSRC}/setup.cfg
	@${REINPLACE_CMD} -e  \
		's|#localedir = "DIRECTORY"|localedir = "${PREFIX}/share/locale"|' \
		${WRKSRC}/pythonsudoku/config.py
	@${FIND} ${WRKSRC} -name POTFILES -or -name *.po -or -name *.pot | \
		${XARGS} ${REINPLACE_CMD} -e \
		's|/usr/lib/python2.4|${PYTHON_CMD}|'
	@${FIND} ${WRKSRC} -name "*.bak" -delete

post-patch-NLS-off:
	@${REINPLACE_CMD} -i '' \
		'/for lingua in linguas():/,/\["locale\/%s\/LC_MESSAGES\/pythonsudoku.mo" % lingua\]))/s/^/#/' \
		${WRKSRC}/setup.py

post-install:
	@cd ${STAGEDIR}${PREFIX}/bin && ${LN} -sf pysdk-gui.py ${PORTNAME}
	(cd ${WRKSRC}/doc && ${INSTALL_MAN} *.6 \
		${STAGEDIR}${MAN6PREFIX}/man/man6/)
	${INSTALL_DATA} ${_DISTDIR}/${PORTNAME}.png \
		${STAGEDIR}${PREFIX}/share/pixmaps/
	cd ${WRKSRC} && ${COPYTREE_SHARE} "Changelog README \
		doc/*.png doc/*.html doc/*.txt doc/*.css" ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
