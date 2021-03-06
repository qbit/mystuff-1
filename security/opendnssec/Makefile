# $OpenBSD$

COMMENT =		open-source turn-key solution for DNSSEC

DISTNAME =		opendnssec-1.3.7

CATEGORIES =		security

HOMEPAGE =		http://www.opendnssec.org/

MAINTAINER =		Fabien Romano <fabien@openbsd.org>

# XXX
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

WANTLIB += c crypto iconv ldns m pthread sqlite3 xml2 z

MASTER_SITES =		http://www.opendnssec.org/files/source/

CONFIGURE_STYLE =	gnu

NO_REGRESS =		Yes

LIB_DEPENDS =		textproc/libxml		\
			net/ldns/libldns	\
			databases/sqlite3
RUN_DEPENDS =		net/ruby-dnsruby	\
			devel/ruby-gems		\
			security/ruby-ezcrypto	\
			security/softhsm

CONFIGURE_ENV +=	CFLAGS="${CFLAGS} -I${LOCALBASE}/include -I${LOCALBASE}/include/libxml2" \
			LDFLAGS="${LDFLAGS} -L${LOCALBASE}/lib -lpthread" \
			GREP_OPTIONS="-E"
CONFIGURE_ARGS =	--localstatedir=/var

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/opendnssec
	@cd ${WRKSRC}/conf && ${INSTALL_DATA} *.xml \
	  ${PREFIX}/share/examples/opendnssec
	@cd ${WRKINST} && rm -rf etc/opendnssec

.include <bsd.port.mk>
