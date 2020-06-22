---
title: 'Ejemplo de Guía Argentina de Citas Legales'
subtitle: Texto ejemplificativo
author: 
  - name: 'Ramiro Álvarez Ugarte'
    affiliation: '*UBA/UP*'
date: 20 de junio de 2020
csl: guia-argentina-de-citas-legales.csl
bibliography: test.bib
toc: false 
suppress-bibliography: true 
notes3: pandoc --number-sections --filter pandoc-citeproc --template=/Users/ramiroalvarezugarte/Dropbox/Templates/draft_article.tex /Users/ramiroalvarezugarte/Dropbox/Templates/draft_article_mac.yaml --bibliography=test.json --pdf-engine=xelatex test.md -o test.pdf
---

La *Guía Argentia de Citas Legales* (GACL) es una guía de estilo volcada a lenguaje CSL que permite la automatización del proceso de citas. Fue desarrollado teniendo en cuenta algunos parámetros usuales de la práctica local, y prestando atención a manuales de estilo y guías existentes. La GACL es un modelo de notas al pie y no está pensado (al menos en esta primera versión) para funcionar con bibliografía final o listado de referencias. Este documento sólo muestra cómo funciona la GACL en la práctica. 

# Cita de libros, artículos y otros materiales académicos  

La escritura jurídica académica suele citar libros [@morgan1988, 55], pero también cita capítulos de libros [@waldron2009, 55; @bergallo2011, 64], artículos académicos [@post2010, 1343; @luchmann2007] y *papers* presentados en conferencias [@siegel2004], entre otros. También---seguramente---se citen de manera creciente blogs [@rau2020; @arballo2020]. 

# Cita de leyes, regulaciones, etcétera  

Tanto la escritura académica como la judicial cita leyes [@ley25673], decretos [@pen2020] y otros tipos de normas de menor jerarquía como resoluciones[@res] y ordenanzas[@ordenanza3a]. También citamos proyectos de leyes [@solanas2015; @carrio2019] y versiones taquigráficas de sesiones legislativas [@reunion7]. 

# Cita de casos judiciales  

Quizás lo más desafiante sea establecer cómo citamos casos judiciales, porque citamos casos diversos, de diversos tribunales, diversas jurisdicciones. Así, por ejemplo, los constitucionalistas solemos citar fallos de la Corte Suprema que están publicados en la colección de *Fallos* ^[@csjn_siri1957; @csjn_peralta1992] pero también casos que aún no están citados en esa colección [@csjn_batalla2018] o casos que se publican en el CIJ [@cfk2020]. También citamos casos de tribunales inferiores, que están citados en revistas [@aborto2007; @aborto1941_b], en suplementos [@inventado1], en sitios como el SAIJ [@saij] o El Dial [@eldial], o que no están publicados en ningún lugar en particular [@giustiniani].

También citamos casos de otros jurisdicciones, tanto provinciales, de otros países, o de sistemas de derecho internacional. Para los órganos internacionales no se indica la jurisdicción porque ella resulta obvia, p.ej., en la Corte IDH [@corteidh1997], en relación a casos individuales de la CIDH [@fondo_uz], o para el Tribunal Europeo de DDHH [@tedh1995]. En el caso de fallos de provincias y de otros países, la jurisdicción va "entre paréntesis [@ussc_sullivan1964; @ccc; @csjsalta2013b]. Los tratados internacionales no requieren citas especiales, pero otros documentos internacionales, como las "Observaciones Generales" de los Comité de ONU, sí [@cdh2011]. 

Una nota sobre las fechas: se optó por seguir el modelo de la fecha para legislaciones de la RATJ porque facilita la lectura a quienes están acostumbrados a la fecha numérica en el mundo anglosajon (mes/día/año) y porque es más versátil, ya que permite poner "entre paréntesis" a una fecha completa o una incompleta (dónde, p.ej., sólo tenemos el año). En los fallos judiciales, muchas veces el año alcanza (p.ej, en casos viejos) pero en muchos casos la fecha exacta de la decisión es útil (p.ej., cuando se trata de casos más recientes o estamos analizando un período histórico corto). En cualquier caso, la opción de fechas entre paréntesis parece adaptarse más fácilmente a esta peculiaridad que ocurre con los fallos y no con otros materiales. 

# Cita de "reportes técnicos"  

Es usual citar reportes técnicos, p.ej. informes temáticos de la CIDH [@cidh2010] o de ONGs [@adc2015] o de la OCDE [@ocde2015], etcétera. Aquí las fechas pueden ser---también---parciales y se optó por el modelo de "fecha completa" porque así lo hacen otros estilos.

# Citas subsiguientes  

Por supuesto, estas citas no ocurren sólo una vez sino que suelen repetirse en el texto. El GACL opta por seguir el modelo de citas "en línea" y sin bibliografía al final, por lo que la cita completa va la primera vez que se cita y las citas subsiguientes son más cortas. Así, por ejemplo, podríamos citar al libro de Morgan citado en la nota número uno [@morgan1988, 135] y lo podríamos citar de nuevo [@morgan1988, 140-156]. Lo mismo ocurre con el caso *Siri* [@csjn_siri1957, cdo. 12] o con el caso *Batalla* [@csjn_batalla2018]. El GACL también permite citar párrafos [@cidh2010, párr. 39], consideranos [@csjn_siri1957, cdo. 14] y---más regularmente---páginas específicas [@post2010, 1343] o conjuntos de páginas [@post2010, 1343-1355]. 

