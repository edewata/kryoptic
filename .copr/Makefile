VERSION = 1.5.0

srpm:
	dnf install -y git openssl-devel pandoc cargo-rpm-macros \
		'crate(asn1/default)' 'crate(bimap/default)' 'crate(bindgen/default) >= 0.72.0' \
		'crate(bitflags/default)' 'crate(cfg-if/default)' \
		'crate(clap)' 'crate(clap/cargo)' 'crate(clap/derive)' 'crate(clap/help)' \
		'crate(clap/std)' 'crate(clap/usage)' 'crate(constant_time_eq/default)' \
		'crate(data-encoding/default)' 'crate(hex/default)' \
		'crate(itertools/default)' 'crate(libc/default)' 'crate(num-bigint/default)' \
		'crate(num-integer/default)' 'crate(num-traits/default)' \
		'crate(pkg-config/default)' 'crate(rusqlite/default)' \
		'crate(serde/default)' 'crate(serde/derive)' 'crate(serde_json/default)' \
		'crate(serial_test/default)' \
		'crate(toml)' 'crate(toml/display)' 'crate(toml/parse)' 'crate(toml/serde)' \
		'crate(uuid/default)' 'crate(uuid/v4)' 'crate(uuid/v8)' 'crate(cryptoki/default)' \
		'crate(vsprintf/default)' 'crate(quick-xml/default)' 'crate(quick-xml/serialize)'

	misc/release.sh ${VERSION}
	mkdir -p rpmbuild/SOURCES
	cp kryoptic-${VERSION}.tar.gz kryoptic-vendor-${VERSION}.tar.gz rpmbuild/SOURCES/

	rpmbuild \
		-ba \
		--define "_topdir ${PWD}/rpmbuild" \
		--without=gpgcheck \
		packaging/kryoptic.spec

	if [[ "${outdir}" != "" ]]; then \
	    mv ${HOME}/build/pki/SRPMS/* ${outdir}; \
	fi
