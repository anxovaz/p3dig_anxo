<h1>pruebA</h1>
##Practica DIG - Anxo Vázquez Lorenzo

#1. Realiza unha consulta "dig danielcastelao.org" e identific cada parte da resposta (IN, CNAME, A, QUERY SECTION, ANSWER SECTION, AUTHORITY SECTION, etc)

##Para realizar unha consulta con dig usase "dig danielcastelao.org"

##dig danielcastelao.org


#2. Realiza consutas dos seguintes nomes e identifica as diferencias: moodle.danielcastelao.org, www.danielcastelao.org

##Cando executase dig sobre moodle.danielcastelao.com a sección de ANSWER mostra 2 servidores de aws, outra das cousas que cambia é o tamano de mesaxe recibido de 54 de moodle.danielcastelao.com a 63 de danielcastelao.org

##dig danielcastelao.org
##dig moodle.danielcastelao.com


#3. Averigua o nome e IP dos servidores de DNS autoritativos de www.danielcastelao.org, por qué soen ser 2 servidores autoritativos?

##danielcastelao.org->178.211.133.37
##moodle.danielcastelao.com -> 18.119.154.66 e 3.140.13.188


#4. Realiza as consultas de nomes inversas: 130.206.164.68 e de outras dúas IPs que se che ocorran.

##dig -x 130.206.164.68
##dig -x 8.8.8.8
##dig -x 8.8.4.4


#5. A qué servidor DNS estás consultando? Cómo o podes cambiar sen tocar os ficheiros de configuración do sistema?

##Cando executo o comando dig exemplo.com muestrase ao final de todo o servidor dns ao que estase realizando a consulta, no meu caso 127.0.0.53

##dig google.es


#6. Obtén o rexistro SOA (Start of Authority) do dominio moodle.danielcastelao.org preguntándolle ó servidor DNS de google e logo preoguntándollo directamente ó servidor primario do dominio danielcastelao.org.

##Para saber o rexistro SOA añado a palabra SOA ao final do comando, e para preguntarlle ao servidor dns de google ou o de danielcastelao.org o indico co "@"

##dig @8.8.8.8 moodle.danielcastelao.com SOA
##dig @178.211.133.37 moodle.danielcastelao.com SOA


#7. Consulta a IP de www.elpais.com. Cánto tempo queda almaceado o rexistro de recurso no DNS local?, se preguntas ó DNS local por este recurso, qué observas no TTL do rexistro?

##Ao realizar o dig sobre elpais.com na sección de answer mostra o TTL da consulta, neste caso 178

##dig www.elpais.com


#8. Busca o TTL de distintos nomes de dominio de servicios que escollas, a qué se poden deber as diferencias?

##Depende de cantos saltos tenga que dar a mesaxe ata chegar ao emisor (servidor).

##dig google.es
##dig elpais.com


#9. Determina o TTL máximo (original) dun nome de dominio.

##604800 segundos (1 semana)


#10. Averigua cántas máquinas con distintas IPs están detrás do dominio web www.google.es, sempre son as mesmas e na mesma orde? por qué?

##Usando "dig dominio.com +short" podo ver as direccións ip que ten un dominio, non teñen porque ser sempre as mesmas, xa que facendo o dig sobre www.google.es da a saída de 142.250.184.163 mentres que se o fago sobre d dominio .com dame a saída de 142.250.184.164.

##dig www.google.es +short


#11. Pregunta o mesmo a un server raiz (J.ROOTSERVERS.NET por exemplo) e comproba na resposta se o server acepta o modo recursivo

##Ao facer o dig sobre J.ROOTSERVERS.NET da 2 direccións ip (3.33.243.145 e 15.197.204.56), o server acepta modo recursivo porque no header mostra o parámetro "ra": flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

##dig J.ROOTSERVERS.NET


#12. Se queremos ver tóda-las queries que fai o servidor de DNS, qué opción temos que usar? Averigua a IP de www.timesonline.co.uk, especifica os pasos dados

##Para averiguar a ip de www.timesonline.co.uk uso o comando "dig dominio.com", o cal mostra as seguintes ips: 54.76.240.177, 34.240.28.43 e 52.208.17.106.

##dig www.timesonline.co.uk


#13. Usando a información dispoñible a traveso do DNS especifica a máquina (nome e IP) ou máquinas que actúan como servers de correo do dominio danielcastelao.org

##Usando MX ao final do comando dig mostra todos os servidores de correo dun dominio.
##ANSWER SECTION:
##danielcastelao.org.	900	IN	MX	100 alt2.aspmx.l.google.com.
##danielcastelao.org.	900	IN	MX	80 aspmx.l.google.com.
##danielcastelao.org.	900	IN	MX	110 aspmx2.googlemail.com.
##danielcastelao.org.	900	IN	MX	120 aspmx3.googlemail.com.
##danielcastelao.org.	900	IN	MX	130 aspmx4.googlemail.com.
##danielcastelao.org.	900	IN	MX	140 aspmx5.googlemail.com.
##danielcastelao.org.	900	IN	MX	90 alt1.aspmx.l.google.com.

##dig danielcastelao.org MX


#14. Podes obter os rexistros AAAA de www.facebook.com? a qué corresponden?

##Escribindo AAAA ao final do comando mostra os seguntes rexistros:
##www.facebook.com.	210	IN	CNAME	star-mini.c10r.facebook.com.
##star-mini.c10r.facebook.com. 15	IN	AAAA	2a03:2880:f104:83:face:b00c:0:25de

##dig www.facebook.com AAAA

