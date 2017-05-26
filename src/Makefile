PTX-html = /Users/joefields/Desktop/mathbook/xsl/mathbook-html.xsl
PTX-latex = /Users/joefields/Desktop/mathbook/xsl/mathbook-latex.xsl
all: pdf html
pdf: pdf/index102.pdf
html: html/index102.html

pdf/index102.pdf: pdf/index102.aux
	cd pdf; pdflatex index102
pdf/index102.aux: pdf/index102.tex
	cd pdf; pdflatex index102
pdf/index102.tex: *.mbx images
	cd pdf; test ! -e images && ln -s ../images; xsltproc --xinclude $(PTX-latex) ../index102.mbx

html/index102.html: *.mbx
	cd html;  test ! -e images && ln -s ../images; xsltproc --stringparam html.css.extra extra.css --stringparam html.knowl.example 'no' --xinclude $(PTX-html) ../index102.mbx
clean::
	rm *.aux *~ *.bak */*.aux */*~ */*.bak pdf/*.pdf html/*.html
check::
	xmllint --xinclude --postvalid --noout --dtdvalid ../../mathbook/schema/dtd/mathbook.dtd ./index102.mbx 2> dtd-errors.txt
images::
	cd images; make
