# Created by: Radim Kolar
# $FreeBSD$

PORTNAME=	supybot-plugins
PORTVERSION=	20060723
PORTREVISION=	1
CATEGORIES=	irc python
MASTER_SITES=	SF/supybot/OldFiles
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	Supybot-plugins-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Official plugin pack for Supybot

DEPRECATED=	Unmaintained, uses EOLed python27
EXPIRATION_DATE=	2020-01-27

RUN_DEPENDS=	supybot:irc/py-supybot@${PY_FLAVOR}

USES=		python:2.7 tar:bzip2

post-extract:
# Delete, because it now included in irc/py-supybot
.for data in BadWords Dunno Success _darcs
	@${RM} -r ${WRKSRC}/${data}
.endfor

do-build:
	cd ${WRKSRC} && ${PYTHON_CMD} -c 'import compileall;compileall.compile_dir(".");' && ${PYTHON_CMD} -O -c 'import compileall;compileall.compile_dir(".");'

do-install:
	cd ${WRKSRC} && ${FIND} . | ${CPIO} -pdm -R ${BINOWN}:${BINGRP} ${STAGEDIR}${PYTHONPREFIX_SITELIBDIR}/supybot/plugins

.include <bsd.port.mk>
