all:	clean validate_xmllint_samu samu-SRS-de.pdf 
epub:	validate_xmllint_samu samu-SRS-de.epub

samu-SRS-de.pdf: samu-SRS-de.xml samu-de.xls
	dblatex samu-SRS-de.xml -p samu-de.xls

samu-SRS-de.epub: samu-SRS-de.xml
	dbtoepub -o samu-SRS-de.epub samu-SRS-de.xml

.PHONY: validate_jing_samu
validate_jing_samu:
	@if [ ! -e jing.jar ]; then \
		wget https://jing-trang.googlecode.com/files/jing-20091111.zip; \
		unzip jing-20091111.zip > /dev/null; \
		mv jing-20091111/bin/jing.jar jing.jar; \
		rm -rf jing-20091111*; \
	fi

	xmllint --xinclude samu-SRS-de.xml --output output.xml
	java -jar jing.jar -c http://docbook.org/xml/5.1CR4/rng/docbookxi.rnc output.xml
	@rm -f output.xml

.PHONY: validate_xmllint_samu
validate_xmllint_samu:
	rm -f output.xml

.PHONY: clean
clean:
	rm -f samu-SRS-de.pdf samu-SRS-de.epub
	rm -f *~

