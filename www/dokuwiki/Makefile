# $OpenBSD: Makefile,v 1.4 2012/02/01 09:12:30 pea Exp $

COMMENT =	standards compliant, simple to use Wiki

VERSION =	2012-01-25
DISTNAME = 	dokuwiki-${VERSION}
PKGNAME = 	dokuwiki-${VERSION:S/-/./g}
CATEGORIES =	www
HOMEPAGE =	http://www.dokuwiki.org/dokuwiki
REVISION =	1

MAINTAINER =	Pierre-Emmanuel Andre <pea@openbsd.org>

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MASTER_SITES =	http://www.splitbrain.org/_media/projects/dokuwiki/

EXTRACT_SUFX = 	.tgz
NO_BUILD =	Yes
NO_REGRESS =	Yes
PKG_ARCH =	*

MODULES=	lang/php

PREFIX =	/var/www
INSTDIR =	${PREFIX}/dokuwiki
SUBST_VARS =	INSTDIR
WRKDIST = 	${WRKDIR}/${DISTNAME:S/c//}

RUN_DEPENDS =	lang/php/${MODPHP_VERSION},-gd

do-install:
	cp -Rp ${WRKDIST} ${INSTDIR}
	chown -R ${SHAREOWN}:${SHAREGRP} ${INSTDIR}
	chown www:www ${INSTDIR}/conf
	chown -R www:www ${INSTDIR}/data

.include <bsd.port.mk>
