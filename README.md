Este es un documento con especificaciones sobre la *Guía Argentina de Citas Legales* desarrollado con base en `spanish-legal.csl` de Rafael Palomino. La GACL funciona como guía de estilo (que autores y editores pueden adoptar / modificar como deseen) pero funciona *especialmente* como un mecanismo automatizado de citas que produce resultados que respetan, en general, la práctica jurídica local. A continuación la lista de materiales que el estilo desea procesar y su estado de implementación actual [^fn2]. 

| Tipo madre                  | Precisión                                  | Estado       |
|:----------------------------|:-------------------------------------------|:-------------|
| Decisiones judiciales       | Fallos CSJN                                | Implementado |* 
|                             | Corte IDH                                  | Implementado |*
|                             | Tribunales inferiores                      | Implementado |*
|                             | TEDH                                       | Implementado |*
|                             | Informes individuales (CIDH, HRC)          | Implementado |*
|                             | SCOTUS							           | Implementado |*
| Decisiones cuasi-judiciales | Jurados de enjuiciamiento                  |              |
|                             | Observaciones Generales de Org. de DDHH    | Implementado |*
|                             | Tribunales administrativos                 |              |
|                             | Acordadas                                  |              |
|                             | Dictamenes de MP / PG                      |              |
| Regulaciones                | Leyes (link + BO)                          | Implementado |*
|                             | Decretos                                   | Implementado |*
|                             | Resoluciones                               | Implementado |
|                             | Ordenanzas                                 | Implementado |*
| Proceso legislativo         | Proyectos de ley                           | Implementado |*
|                             | Dictamenes de comisión (mayoría y minoría) | Implementado |
|                             | Versiones taquigráficas                    | Implementado |*
| Actos administrativos       |                                            |              |
| Reportes                    | Reportes técnicos, documentos de org.      | Implementado |*
| Académicos                  | Libros                                     | Implementado |*
|                             | Artículos                                  | Implementado |*
|                             | Papers en conferencias                     | Implementado |*
|                             | Libros                                     | Implementado |*
|                             | Capítulos de libros                        | Implementado |*
|                             | Borradores                                 | Implementado |
| Sitios web                  | sitios en general + blogs                  | Implementado |*
| Documentos en general       |                                            | Implementado |

Table: Lista de materiales de la GACL y estado de implementación.

# Implementación

La GACL funciona bien en [Zotero](https://www.zotero.org/) y debería funcionar bien en otros administradores de bibliografía, como [Mendeley](https://www.mendeley.com/?interaction_required=true), [Papers](https://www.papersapp.com/), [Docear4Word](http://www.docear.org/software/add-ons/docear4word/overview/) o [Paperpile](https://paperpile.com/). También funciona bien como CSL autónomo a ser procesado por `pandoc-citeproc`. 

La GACL es compatible con el estándar CSL 1.0.1 pero **no es compatible** con el estándar de Juris-M. 

La GACL, además de un estilo de citas que editores pueden adoptar / revisar, funciona **especialmente** como lenguaje CSL que automatiza el proceso. Para que el "GACL como CSL" funcione bien, en ocasiones cierto tipo de datos deben "archivarse" en el campo correcto de nuestro administrador de bibliografía. P.ej., para que el tipo de sentencias en casos de la Corte Interamericana sea reflejado correctamente y siguiendo las prácticas usuales, es necesario que el tipo de sentencia se cargue en el campo `abstract`
 (p.ej., "Fondo, Reparaciones y Costas" u "Opinión Consultiva") [^fn4]. 

La Tabla 2 identifica esas particularidades. 

| Uso             | Zot Item Type    | Biblatex            | CSL-JSON          | Notas                                                 |
|:----------------|:-----------------|:--------------------|:------------------|:------------------------------------------------------|
| Casos arg. CSJN | Case             | jurisdiction        | legal_case        | `journal` = {Fallos}                     		       |
| Casos arg. misc | Case             | jurisdiction        | legal_case        | Publicado en revista con tomo, `journal` = {L.L.} etc.|
| Casos arg. misc | Case             | jurisdiction        | legal_case        | Si es un suplemento / diario = día va en `history`    |
| Casos arg. misc | Case             | jurisdiction        | legal_case        | Si SAIJ (`journal`), el ID va en `abstract`		   |
| Casos arg. misc | Case             | jurisdiction        | legal_case        | Si El Dial (`journal`), el ID va en `abstract`		   |
| Casos Corte IDH | Case             | jurisdiction        | legal_case        | Requiere: `abstract` = {Fondos, Rep...} etc.   	   |
| Casos CIDH      | Case             | jurisdiction        | legal_case        | Requiere: `reporter` = {Informe No.} 				   |
| 				  |  				 |   				   |   				   | `abstract` = {Fondo}								   |
| Artículos       | Journal Article  | article             | article-journal   |                                                       |
| Capítulos       | Book Section     | incollecetion       | chapter           |                                                       |
| Conf. papers    | Conference Paper | inproceedings       | conference-papers | CSL --> Requiere: `venue` (address)                   |
| Borradores      | Manuscript       | unpublished         | manuscripts       |                                                       |
| Leyes           | Statute          | legislation         | legislation       | Require: B.O. + No. en `volume`                       |
| Leyes           | Statute          | legislation         | legislation       | Si: SAIJ + ID. en `volume`                            |
| Ley extranjera  | Statute          | legislation         | legislation       | Require: `abstract` = {Jurisdicción / País}           |
| Resolución      | Statute          | legislation         | legislation       | Require: `abstract` = {Organismo que emite}           |
| Ley provincial  | Statute          | legislation         | legislation       | Require: `abstract` = {Provincia}                     |
| Ordenanza       | Statute          | legislation         | legislation       | Require: `abstract` = {Municipalidad}                 |
| Proyecto de ley | Bill             | legislation         | legislation       |                                                       |
| Dict. comisión  | Manuscript       | unpublished         | manuscript        | Requiere: `type` = {Dictamen de Mayoría / Minoría}    |
| Reporte técnico | Report           | report o techreport | report            |                                                       |
| Observ. General | Report 			 | report o techreport | report 		   |   													   |
| Sitio web       | Web Page         | online              | webpage           |                                                       |
| Blog post       | Blog post        | online              | post-weblog       |                                                       |
| Documento misc  | Manuscript       | unpublished         | manuscript        | Requiere: `abstract` = {localización del doc.}          |

Table: Listado de equivalencias y requerimientos para que el CSL funcione óptimamente. 

# Abreviaturas 

La GACL estuvo pensada para usar abreviaciones a la hora de referirse a tribunales. Se siguen las de "Cuadernos del Derecho", entre las más usuales: 

| Nombre completo                                                                 | Abreviación          |
|---------------------------------------------------------------------------------|----------------------| 
| Cámara de Apelaciones del Trabajo                                               | CAT                  |
| Cámara de Apelaciones en lo Civil y Comercial                                   | CACiv. y Com.        |
| Cámara de Apelaciones en lo Contencioso Administrativo y Tributario de CABA     | CACont. Adm. Trib    |
| Cámara de Apelaciones en lo Contravencional y Faltas de la Ciudad               | CAContr. y F.        |
| Cámara de Diputados                                                             | CDi                  |
| Cámara del Trabajo                                                              | CT                   |
| Cámara de Senadores                                                             | CSe                  |
| Cámara Federal                                                                  | CFed                 |
| Cámara Federal de Salta                                                         | CFed (Salta)         |
| Cámara Federal de Casación Penal                                                | CFedCP               |
| Cámara Federal de la Seguridad Social (ex CNA de la Seguridad Social            | CFedSS               |
| Cámara Nacional de Apelaciones de la Seguridad Social                           | CNASS                |
| Cámara Nacional de Apelaciones del Trabajo                                      | CNAT                 |
| Cámara Nacional de Apelaciones del Trabajo-Presidencia                          | CNAT-Pres            |
| Cámara Nacional de Apelaciones en lo Civil                                      | CNACiv.              |
| Cámara Nacional de Apelaciones en lo Civil y Comercial Federal                  | CNACiv. y Com. Fed.  |
| Cámara Nacional de Apelaciones en lo Comercial                                  | CNACom.              |
| Cámara Nacional de Apelaciones en lo Contencioso Administrativo Federal         | CNACont. Adm. Fed.   |
| Cámara Nacional de Apelaciones en lo Criminal y Correccional                    | CNACrim. y Corr.     |
| Cámara Nacional de Apelaciones en lo Criminal y Correccional Federal            | CNACrim. Corr. Fed.  |
| Cámara Nacional de Apelaciones en lo Penal Económico                            | CNAPen. Econ.        |
| Cámara Nacional de Casación en lo Criminal y Correccional de la Capital Federal | CNCCrimCo (CF)       |
| Cámara Nacional de Casación Penal                                               | CNCP                 |
| Cámara Nacional en lo Penal Económico                                           | CNPen. Econ.         |
| Juzgado Laboral                                                                 | JL                   |
| Juzgado Nacional de Primera Instancia en lo Civil                               | JNPICiv.             |
| Juzgado Nacional de Primera Instancia en lo Comercial                           | JNPICom.             |
| Juzgado Nacional de Primera Instancia del Trabajo                               | JNPIT                |
| Juzgado de Primera Instancia en lo Civil y Comercial                            | JPICiv. y Com.       |

Table: Listado de abreviaturas 

# Ejemplos  

## Libros  

<span style="font-variant: small-caps;">E. S. Morgan</span>, *Inventing the People: The Rise of Popular Sovereignty in England and America*, Reprint edition, W. W. Norton & Company, New York, 1988. 

## Capítulos de libros 

<span style="font-variant: small-caps;">P. Bergallo</span>, «Cambio Constitucional, Reproduccion y Derechos», en Roberto Gargarella (ed.) *La Constitución en 2020: 48 propuestas para una sociedad igualitaria*, Siglo XXI, Buenos Aires, 2011. 

<span style="font-variant: small-caps;">J. Waldron</span>, «Constitutionalism: A Skeptical View», en Thomas Christiano, John Philip Christman (eds.) *Contemporary Debates in Political Philosophy*, Wiley-Blackwell, Malden, MA, 2009. 

## Artículos 

L. H. H. Lüchmann, «Representation Within Participative Experiences», Lua Nova: Revista de Cultura e Política, 70, 2007, Disponible en http://www.scielo.br/scielo.php?script=sci_abstract&pid=S0102-6445200700010-0007&lng=en&nrm=iso&tlng=pt.

R. Post, «Theorizing Disagreement: Reconceiving The Relationship Between Law And Politics», California Law Review, vol. 98, 4, 2010, pág. 1343, Disponible en http://www.jstor.org/stable/27896713.

## Ponencias 

R. Siegel, «The Jurisgenerative Role of Social Movements in US Constitutional Law», Seminario en Latinoamérica de Teoria Constitucional y Politica, Oaxaca, Mexico, 7 de Julio de 2004.

## Blogs 

G. Arballo, *Reformas en la Justicia: el Palacio y la Calle*, <span style="font-variant: small-caps;">Saber Leyes no es Saber Derecho</span>, 04/06/2020, disponible en http://www.saberderecho.com/2020/06/reformas-en-la-justicia-el-palacio-y-la.html Fecha de consulta: 12/06/2020. 

## Leyes 

Ley 25.673. Creación del Programa Nacional de Salud Sexual y Procreación Responsable, Nov. 22, 2002, B.O. No. 30.032.

## Decretos 

Decreto 260. Emergencia Sanitaria, Mar. 12, 2020, B.O. No. 34.327. Disponible en: http: //servicios.infoleg.gob.ar/infolegInternet/verNorma.do?id=335423.

## Resoluciones 

Resolución 1054/2020, Jun. 19, 2020 (Ministerio de Salud). Disponible en: http://servicios.infoleg.gob.ar/infolegInternet/verNorma.do;jsessionid-=49E37248395838D0BB7E2DF255C5EC11?id=338960.

## Ordenanzas 

Ordenanza No. 7227. Autoriza al D.E. renovar Comodato de Uso inmueble situado en calle Vélez Sarsfield No 480, Mar. 14, 2019, B.O. Disponible en: https://www.tresarroyos.gov.ar/recursos/boletin_oficial/ordenanzas/2019/2019-O-7227.pdf.

## Proyectos de ley 

CDi, Proyecto 5449-D-2019, Codigo Aduanero, Ley 22415. Derogacion del articulo 755, sobre derechos de exportacion (G. Carrio, Elisa), Dic. 11, 2019

CSe, Proyecto 3878-S-2015, Modificaciones respecto del reglamento interno de funcionamiento y organizacion del consejo de seguridad interior (F. Solanas; R. Giustiniani; G. Morales), Nov. 18, 2015.

## Versiones taquigráficas 

CDi, *Versión taquigráfica de audiencia pública sobre Interrupción Voluntaria del Embarazo*, May. 3, 2018. Disponible en https://www.diputados.gov.ar/comisiones/-permanentes/clgeneral/reuniones/vt/.

## Casos de la CSJN (publicados en Fallos)

CSJN, *Siri, Angel*, Fallos 239:459 (1957)  

CSJN, *Peralta, Luis Arcenio y otro c/ Estado Nacional (Mrio. de Economía BCRA.) s/ amparo*, Fallos 313:1513 (Dic. 27, 1990)  

## Casos de la CSJN (sin publicación)

CSJN, *Recurso de hecho deducido por Batalla, Rufino en la causa Hidalgo Garzón, Carlos del Señor y otros s/ inf. art. 144 bis inc. 1 ---último párrafo---según ley 14.616* (Dic. 4, 2018).

## Casos de la CSJN (CIJ)

CSJN, *Fernández de Kirchner, Cristina en carácter de Presidenta del Honorable Senado de la Nación s/ acción declarativa de certeza* (Abr. 24, 2020). Disponible en: https://www.cij.gov.ar/nota-37179-La-Corte-dict--sentencia-en-la-causa--Fern-ndez-de-Kirchner--Cristina-en-car-cter-de-Presidenta-del-Honorable-Senado-de-la-Naci-n-s--acci-n-declarativa-de-certeza-.html.

## Casos tribunales inferiores 

### Publicados en revistas encuadernadas 

CNCrim. y Correc. (Sala VII), *G., N. s/sobreseimiento, aborto, instr. 33/170*, E.D. 222:435 (Abr. 17, 2007).

SC (Tucumán), *Schull de Giani, Betti*, LL 28:402 (Ago. 25, 1942).

### Publicados en suplementos 

J.CyC No. 2 (San Martín), *Castro de Guerrero, Anibal s/ homicidio*, Suplemento de Derecho Penal de La Ley del 10 oct. 2017. Expediente No. 28123/2016 (Dic. 3, 2016).

### Publicados en sitios web 

CNCP, *Moccia, Gabriela s/ recurso de casacion*, SAIJ SU33000928. Expediente No. 582 (Mar. 11, 1996). Disponible en: http://shorturl.at/eouzJ.

CNCom., *Amaru SACI s/ quiebra s/ incidente de verificación de crédito del Gobierno de la Ciudad de Buenos Aires*, El Dial.com AABBB4 (Feb. 11, 2020). Disponible en: https://www.eldial.com/nuevo/lite-jurisprudencia-detalle.asp?base=14&id=52021&t=j&h=u.

## Casos sin publicación  

CNCAF (Sala I), *Giustiniani, Rubén Héctor c. YPF s/ amparo por mora*. Expediente No. 37747/2013 (Abr. 17, 2020).

## Casos de jurisdicción provincial

CSJ (Salta), *Cari, Irene – Presidenta de Foro De Mujeres por La Igualdad De Oportunidades – Acción De Inconstitucionalidad*. Expediente No. 35475/12 (Jul. 12, 2013)

## Casos de jurisdicción internacional 

Corte IDH, *Caso Loayza Tamayo Vs. Perú*, Serie C 33. Fondo, Reparaciones y Costas (Sep. 17, 1997).

CIDH, *Nestor José y Luis Uzcátegui*, Informe No. 88/10. Admisibilidad (Jul. 14, 2010). 

TEDH, *Tolstoy Miloslavsky v. The United Kingdom*, Series A 316. Merits. Expediente No. 18139/91 (Jul. 13, 1995). Disponible en: https://hudoc.echr.coe.int/eng#-%7B%22fulltext%22:%5B%22tolstoy%22%5D,%22documentcollectionid2%22:%5B%-22GRANDCHAMBER%22,%22CHAMBER%22%5D,%22itemid%22:%5B%22001-57947%22%5D%7D.

## Casos extranjeros 

CCC (Colombia), *Sentencia T-760/2001* (Jul. 18, 2001). Disponible en: http://www.corteconstitucional.gov.co/relatoria/2001/C-760-01.htm;

USSC (EEUU), *New York Times v. Sullivan*, U.S. 376:254 (1964).

## Documentos ONU

CDH, «Observación general No 34. Artículo 19 Libertad de opinión y libertad de expresión». Comité de Derechos Humanos de las Naciones Unidas, Ginebra. CCPR/C/GC/34. 12 de Septiembre de 2011.

## Reportes técnicos

CIDH, «Marco jurídico interamericano del Derecho a la Libertad de Expresión». Relatoría Especial para la Libertad de Expresión de la Comisión Interamericana de Derechos Humanos. OEA/Ser.L/V/II CIDH/RELE/INF. 2/09. 30 de Diciembre de 2009.  

ADC, «El (des)control democrático de los organismos de inteligencia en la Argentina». Asociación por los Derechos Civiles, Buenos Aires. Enero de 2015.  

OCDE, «Recommendation on Public Procurement». Directorate for Public Governance and Territorial Development. OCDE. 2015.  

# Contacto

Por cualquier sugerencia o comentario, vías de contacto en https://ramiroau.github.io/

[^fn2]: La idea es que se vaya expandiendo, pero estos son los materiales que parecen necesarios luego de una mini encuesta en Twitter. 

[^fn4]: Son decisiones arbitrarias pero que se basan en algunas ausencias de opciones en los campos que muestra Zotero por default. Aparentemente, muchas de estas ausencias se van a resolver en la versión 1.0 de Zotero. 
