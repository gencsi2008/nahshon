all:	clean validate_xmllint_samu samu-SRS-ro.pdf 
epub:	validate_xmllint_samu samu-SRS-ro.epub

samu-SRS-ro.pdf: samu-SRS-ro.xml samu-ro.xls
	dblatex samu-SRS-ro.xml -p samu-ro.xls

samu-SRS-ro.epub: samu-SRS-ro.xml
	dbtoepub -o samu-SRS-ro.epub samu-SRS-ro.xml

.PHONY: validate_jing_emu
validate_jing_samu:
	@if [ ! -e jing.jar ]; then \
		wget https://jing-trang.googlecode.com/files/jing-20091111.zip; \
		unzip jing-20091111.zip > /dev/null; \
		mv jing-20091111/bin/jing.jar jing.jar; \
		rm -rf jing-20091111*; \
	fi

	xmllint --xinclude samu-SRS-ro.xml --output output.xml
	java -jar jing.jar -c http://docbook.org/xml/5.1CR4/rng/docbookxi.rnc output.xml
	@rm -f output.xml

.PHONY: validate_xmllint_emu
validate_xmllint_samu:
	xmllint --xinclude samu-SRS-ro.xml --output output.xml
	xmllint --relaxng http://docbook.org/xml/5.1CR4/rng/docbookxi.rng output.xml --noout
	rm -f output.xml

.PHONY: clean
clean:
	rm -f samu-SRS-ro.pdf samu-SRS-ro.epub
	rm -f *~

