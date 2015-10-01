all:
	dnu restore
	dnu publish --no-source --runtime active

install:
	# TODO: this is a hack
	sed -i -e 's/DNXHelloWorld/run/' bin/output/DNXHelloWorld
	cp -r bin/output ${DESTDIR}/dnxapp
	chmod -R +r ${DESTDIR}/dnxapp

clean:
	rm -rf bin
